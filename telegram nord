{
  "meta": {
    "instanceId": "408f9fb9940c3cb18ffdef0e0150fe342d6e655c3a9fac21f0f644e8bedabcd9",
    "templateCredsSetupCompleted": true
  },
  "nodes": [
    {
      "id": "telegramTrigger",
      "name": "Telegram Trigger",
      "type": "n8n-nodes-base.telegramTrigger",
      "position": [-220, 380],
      "parameters": {
        "updates": ["message"],
        "additionalFields": {}
      },
      "credentials": {
        "telegramApi": {
          "id": "XVBXGXSsaCjU2DOS",
          "name": "jimleuk_handoff_bot"
        }
      },
      "typeVersion": 1.1
    },
    {
      "id": "openAiChat",
      "name": "OpenAI Chat Model",
      "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
      "position": [20, 380],
      "parameters": {
        "model": {
          "__rl": true,
          "mode": "list",
          "value": "gpt-4o-mini"
        },
        "text": "=Respond as a helpful assistant with emojis: {{ $json.message.text }}",
        "options": {}
      },
      "credentials": {
        "openAiApi": {
          "id": "8gccIjcuf3gvaoEr",
          "name": "OpenAi account"
        }
      },
      "typeVersion": 1.2
    },
    {
      "id": "telegramSend",
      "name": "Telegram",
      "type": "n8n-nodes-base.telegram",
      "position": [380, 380],
      "parameters": {
        "chatId": "={{ $json.message.chat.id }}",
        "text": "={{ $json.text }}",
        "additionalFields": {}
      },
      "credentials": {
        "telegramApi": {
          "id": "XVBXGXSsaCjU2DOS",
          "name": "jimleuk_handoff_bot"
        }
      },
      "typeVersion": 1.2
    }
  ],
  "connections": {
    "telegramTrigger": {
      "main": [
        [
          {
            "node": "openAiChat",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "openAiChat": {
      "main": [
        [
          {
            "node": "telegramSend",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "pinData": {}
}
