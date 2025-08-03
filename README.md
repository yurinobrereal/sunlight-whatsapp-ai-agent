# 🌞 Sunlight Power - Agente de IA WhatsApp

Sistema completo de atendimento automatizado via WhatsApp para empresas de energia solar, usando inteligência artificial para responder clientes, qualificar leads e agendar visitas técnicas.

## ✨ Funcionalidades

### 🤖 Agente de IA Inteligente
- **Personalidade customizada** para energia solar
- **Respostas contextuais** baseadas em histórico
- **Processamento de objeções** automático
- **Qualificação de leads** inteligente

### 📱 Integração WhatsApp
- **Conexão direta** com WhatsApp Web
- **QR Code** para autenticação
- **Envio/recebimento** automático de mensagens
- **Suporte a áudio** (síntese de voz)

### 🎯 Especializado em Energia Solar
- **Base de conhecimento** específica
- **Cálculo de economia** energética
- **Informações sobre financiamento**
- **Agendamento de visitas** técnicas

### 📊 Dashboard Administrativo
- **Monitoramento em tempo real**
- **Histórico de conversas**
- **Gestão de clientes**
- **Estatísticas de atendimento**

## 🚀 Instalação Rápida

### 1. Clone o Repositório
```bash
git clone <repository-url>
cd sunlight-power-whatsapp-agent
```

### 2. Instale as Dependências
```bash
npm install
```

### 3. Configure o Sistema
```bash
npm run setup
```

### 4. Inicie o Servidor
```bash
npm run dev
```

### 5. Acesse o Dashboard
Abra http://localhost:8000 no seu navegador

## ⚙️ Configuração Detalhada

### Chaves de API Necessárias

#### 🔑 OpenRouter (Obrigatório)
Para o funcionamento da IA:
1. Acesse [OpenRouter](https://openrouter.ai/)
2. Crie uma conta e obtenha sua API key
3. Configure no `.env.local`:
```env
OPENROUTER_API_KEY=your_openrouter_api_key_here
```

#### 🎤 Google Cloud Text-to-Speech (Opcional)
Para síntese de voz:
1. Crie um projeto no [Google Cloud Console](https://console.cloud.google.com/)
2. Ative a API Text-to-Speech
3. Crie uma conta de serviço e baixe o JSON
4. Configure no `.env.local`:
```env
GOOGLE_APPLICATION_CREDENTIALS=path/to/your/credentials.json
ENABLE_VOICE=true
```

### Arquivo .env.local Completo
```env
# OpenRouter API Key (obrigatório)
OPENROUTER_API_KEY=your_openrouter_api_key_here

# Google Cloud Text-to-Speech (opcional)
GOOGLE_APPLICATION_CREDENTIALS=path_to_your_service_account.json
ENABLE_VOICE=true

# Configurações do WhatsApp
WHATSAPP_SESSION_PATH=./whatsapp-session

# Configurações da empresa
COMPANY_NAME=Sunlight Power
COMPANY_WEBSITE=sunlightpower.com.br
COMPANY_PHONE=+55_11_99999_9999

# Configurações do banco de dados
DATABASE_URL="file:./dev.db"
```

## 📱 Como Conectar o WhatsApp

1. **Acesse o Dashboard**: http://localhost:8000
2. **Clique em "Conectar WhatsApp"**
3. **Escaneie o QR Code** com seu WhatsApp
4. **Aguarde a confirmação** de conexão
5. **Teste o agente** na aba "Testar IA"

## 🎯 Personalização para Sua Empresa

### 1. Informações da Empresa
Edite `src/data/personality.json`:
```json
{
  "name": "Seu Assistente",
  "knowledge_base": {
    "company_info": {
      "name": "Sua Empresa",
      "website": "seusite.com.br",
      "specialties": ["Seus serviços"]
    }
  }
}
```

### 2. Produtos e Serviços
Edite `src/data/products.json`:
```json
{
  "solar_panels": {
    "residential": {
      "name": "Seu Kit Residencial",
      "price_range": "R$ 15.000 - R$ 45.000"
    }
  }
}
```

### 3. Respostas Padrão
Edite `src/data/responses.json`:
```json
{
  "greetings": [
    "Olá! Sou da Sua Empresa. Como posso ajudar?"
  ]
}
```

## 🧪 Testes

### Testar IA
```bash
npm run test:ai
```

### Testar Síntese de Voz
```bash
npm run test:voice
```

### Resetar Banco de Dados
```bash
npm run db:reset
```

## 📊 Estrutura do Projeto

```
├── src/
│   ├── app/                 # Next.js App Router
│   │   ├── api/            # API Routes
│   │   │   ├── whatsapp/   # WhatsApp integration
│   │   │   ├── ai/         # AI processing
│   │   │   ├── voice/      # Voice synthesis
│   │   │   └── database/   # Database operations
│   │   ├── layout.tsx      # Layout principal
│   │   └── page.tsx        # Dashboard
│   ├── components/         # Componentes React
│   ├── lib/               # Bibliotecas principais
│   │   ├── whatsapp.ts    # Cliente WhatsApp
│   │   ├── ai.ts          # Processamento IA
│   │   ├── voice.ts       # Síntese de voz
│   │   └── database.ts    # Banco de dados
│   └── data/              # Configurações
│       ├── personality.json
│       ├── products.json
│       └── responses.json
├── scripts/
│   └── setup.js           # Script de configuração
└── README.md
```

## 🔧 APIs Disponíveis

### WhatsApp API
- `GET /api/whatsapp` - Status e QR Code
- `POST /api/whatsapp` - Inicializar/Enviar mensagem
- `DELETE /api/whatsapp` - Desconectar

### IA API
- `POST /api/ai` - Processar mensagem
- `GET /api/ai` - Testar IA

### Voice API
- `POST /api/voice` - Sintetizar voz
- `GET /api/voice` - Testar síntese

### Database API
- `GET /api/database` - Consultar dados
- `POST /api/database` - Inserir dados
- `PUT /api/database` - Atualizar dados

## 🎨 Interface do Dashboard

### Tela Principal
- **Status do WhatsApp** (conectado/desconectado)
- **Estatísticas em tempo real**
- **QR Code para conexão**

### Abas Disponíveis
1. **Conversas** - Histórico de mensagens
2. **Clientes** - Lista de leads/clientes
3. **Testar IA** - Interface de teste
4. **Envio Manual** - Enviar mensagens manuais

## 🔍 Monitoramento

### Logs do Sistema
```bash
# Logs em tempo real
tail -f logs/app.log

# Logs do WhatsApp
tail -f logs/whatsapp.log
```

### Banco de Dados
O sistema usa SQLite com as seguintes tabelas:
- `conversations` - Histórico de mensagens
- `customers` - Dados dos clientes
- `appointments` - Agendamentos
- `settings` - Configurações do sistema

## 🚨 Solução de Problemas

### WhatsApp não conecta
1. Verifique se o QR Code está sendo exibido
2. Certifique-se de que o WhatsApp Web está funcionando
3. Tente resetar a sessão: `rm -rf whatsapp-session`

### IA não responde
1. Verifique se a `OPENROUTER_API_KEY` está configurada
2. Teste a API: `npm run test:ai`
3. Verifique os logs de erro

### Síntese de voz não funciona
1. Verifique as credenciais do Google Cloud
2. Teste a API: `npm run test:voice`
3. Configure `ENABLE_VOICE=false` para desabilitar

### Banco de dados corrompido
```bash
npm run db:reset
```

## 🔒 Segurança

- **Variáveis de ambiente** para chaves sensíveis
- **Validação de entrada** em todas as APIs
- **Rate limiting** para evitar spam
- **Logs de auditoria** para monitoramento

## 📈 Escalabilidade

### Para Produção
1. **Use PostgreSQL** ao invés de SQLite
2. **Configure Redis** para cache
3. **Use PM2** para gerenciamento de processos
4. **Configure NGINX** como proxy reverso

### Múltiplas Empresas
O sistema pode ser facilmente adaptado para:
- **Multi-tenant** (várias empresas)
- **Diferentes personalidades** por empresa
- **Bases de conhecimento** específicas

## 🤝 Contribuição

1. Fork o projeto
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Push para a branch
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 🆘 Suporte

Para suporte técnico:
- **Email**: suporte@sunlightpower.com.br
- **WhatsApp**: +55 11 99999-9999
- **Site**: https://sunlightpower.com.br

---

**Desenvolvido com ❤️ para revolucionar o atendimento em energia solar**

## 🎯 Próximas Funcionalidades

- [ ] Integração com CRM
- [ ] Relatórios avançados
- [ ] Chatbot por voz
- [ ] Integração com calendário
- [ ] API para terceiros
- [ ] App mobile
- [ ] Integração com redes sociais
- [ ] IA preditiva para leads
