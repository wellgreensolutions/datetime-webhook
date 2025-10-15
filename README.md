# Webhook get_date_time para ElevenLabs

## 🧠 Descrição
Este projeto é um webhook simples em Flask que retorna a **data e hora atuais** no formato **ISO 8601**, configurado no **fuso horário America/Sao_Paulo**.  
Ele foi criado para integração com **agentes de voz ElevenLabs**, permitindo que o agente utilize este endpoint para determinar o horário atual e construir corretamente os parâmetros de agendamento.

---

## ⚙️ Tecnologias utilizadas
- Python 3.10+
- Flask → microframework web para criar a API
- pytz → biblioteca para manipulação de fusos horários

---

## 🗂️ Estrutura do projeto
```
.
├── app.py              # Código principal do servidor Flask
├── requirements.txt    # Dependências necessárias
├── Procfile            # Instrução de execução no Railway
└── README.md           # Este arquivo
```

---

## 🚀 Deploy no Railway
1. Faça login em [https://railway.app](https://railway.app)
2. Crie um novo projeto (ou reabra o existente)
3. Faça upload do arquivo `.zip` contendo:
   ```
   app.py
   requirements.txt
   Procfile
   README.md
   ```
4. O Railway detectará o ambiente Python automaticamente e instalará as dependências.
5. Após o deploy, o aplicativo será executado em uma porta pública.

---

## 🌐 Endpoint
Após o deploy, o endpoint ficará acessível em:
```
https://SEU_PROJETO.railway.app/get-datetime
```

### 🔁 Exemplo de resposta:
```json
{
  "datetime": "2025-10-14T23:55:42-0300",
  "formatted": "14/10/2025 23:55:42",
  "timezone": "America/Sao_Paulo",
  "status": "success"
}
```

---

## 🤖 Integração com ElevenLabs
Configure uma **ferramenta de webhook** chamada `get_date_time` na aba *Tools* do seu agente e use:
- **Método:** GET  
- **URL:** `https://SEU_PROJETO.railway.app/get-datetime`  
- **Sem autenticação**  
- **Resposta esperada:** objeto JSON com o campo `"datetime"`

O agente pode usar esse valor como `range_start` na ferramenta `get_available_slots`.

---

## 🧪 Teste local (opcional)
Se quiser testar localmente:
```bash
pip install -r requirements.txt
python app.py
```
Depois acesse:
```
http://127.0.0.1:8080/get-datetime
```

---

## 📅 Autor
Desenvolvido por **Wellington Lemos**  
Para integração com o **agente de voz “Paula” (SDR do programa FAST)**, assistente do **Fábio Soares**.
