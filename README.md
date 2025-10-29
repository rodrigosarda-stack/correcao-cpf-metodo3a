# Página de Correção de CPF - Método 3a Médico

Página HTML para validação e correção de CPF inválido no fluxo de checkout.

## 🎯 Objetivo

Quando um usuário preenche o Typeform com CPF inválido, ele é redirecionado para esta página onde pode corrigir o CPF antes de continuar o processo.

## 🚀 Como Funciona

1. Usuário preenche Typeform
2. n8n valida o CPF
3. Se inválido, redireciona para esta página
4. Usuário corrige o CPF
5. Página valida em tempo real (JavaScript)
6. Se válido, envia para webhook do n8n
7. Fluxo continua normalmente

## 🌐 URL da Página

```
https://rodrigosarda-stack.github.io/correcao-cpf-metodo3a/
```

## 📋 Parâmetros da URL

A página recebe os seguintes parâmetros via query string:

- `cpf` - CPF inválido que foi informado
- `response_id` - ID da resposta do Typeform
- `tipo` - Tipo de produto (consultorio ou clinica)
- `plano` - Plano escolhido (anual ou mensal)

**Exemplo:**
```
https://rodrigosarda-stack.github.io/correcao-cpf-metodo3a/?cpf=111.111.111-11&response_id=abc123&tipo=consultorio&plano=anual
```

## ✨ Funcionalidades

- ✅ Validação de CPF em tempo real (algoritmo brasileiro)
- ✅ Máscara automática de CPF (formata enquanto digita)
- ✅ Mensagens de erro/sucesso
- ✅ Loading spinner durante validação
- ✅ Design responsivo (mobile e desktop)
- ✅ Link para suporte via WhatsApp

## 🔧 Configuração

### 1. Ativar GitHub Pages

1. Acesse: [Settings → Pages](https://github.com/rodrigosarda-stack/correcao-cpf-metodo3a/settings/pages)
2. Em **Source**, selecione: **Deploy from a branch**
3. Em **Branch**, selecione: **master** e **/ (root)**
4. Clique em **Save**

### 2. Atualizar URL do n8n

Edite o arquivo `index.html` e substitua:

```javascript
const n8nUrl = `https://SEU_DOMINIO_N8N/webhook/corrigir-cpf?...`;
```

Por:

```javascript
const n8nUrl = `https://sua-instancia-n8n.app.n8n.cloud/webhook/corrigir-cpf?...`;
```

## 🧪 Testar

Acesse a URL com parâmetros de teste:

```
https://rodrigosarda-stack.github.io/correcao-cpf-metodo3a/?cpf=111.111.111-11&response_id=teste123&tipo=consultorio&plano=anual
```

## 📊 Integração com n8n

### Webhook de Redirecionamento

No nó "Responder com Página de Correção" do n8n:

```javascript
Location: https://rodrigosarda-stack.github.io/correcao-cpf-metodo3a/?cpf={{$json.cpf_original}}&response_id={{$json.typeform_response_id}}&tipo={{$json.tipo_produto}}&plano={{$json.plano}}
```

### Webhook de Recebimento

Criar webhook no n8n: `/webhook/corrigir-cpf`

Este webhook receberá:
- `cpf` - CPF corrigido (apenas números)
- `response_id` - ID da resposta do Typeform
- `tipo` - Tipo de produto
- `plano` - Plano escolhido

## 🎨 Design

- **Cores:** Gradiente roxo/azul (#667eea → #764ba2)
- **Fonte:** System fonts (rápido e bonito)
- **Layout:** Card centralizado com sombra
- **Responsivo:** 100% mobile-friendly

## 📞 Suporte

Link para WhatsApp: https://wa.me/5548974002997

## 📝 Licença

Uso interno - Método 3a Médico

---

**Desenvolvido para:** Método 3a Médico  
**Data:** Outubro 2024  
**Versão:** 1.0
