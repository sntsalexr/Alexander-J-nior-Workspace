# Alexander Júnior Workspace: publicação com "Orçar com IA"

## Estrutura da pasta (suba tudo para o Vercel)
```
index.html        o aplicativo
api/orcar.js      backend seguro que fala com o Gemini
vercel.json       cabeçalhos de segurança
package.json
```

## Configuração (uma vez)
1. Gere uma chave no Google AI Studio (aistudio.google.com/apikey).
2. No Vercel: projeto > Settings > Environment Variables. Crie:
   - `GEMINI_API_KEY` = sua chave
   - `APP_TOKEN` = um código longo e secreto que você inventa (ex.: 30 caracteres aleatórios)
   - `GEMINI_MODEL` (opcional) = nome do modelo, se quiser fixar um
3. Faça um novo deploy (Deployments > Redeploy) para as variáveis valerem.
4. No app: Orçamentos > Novo orçamento > Orçar com IA. Na primeira vez, digite o `APP_TOKEN`.
   Ele fica salvo só naquele aparelho e não entra nos backups.

## Segurança
- A chave do Gemini nunca vai para o navegador: só existe nas variáveis do Vercel.
- O backend exige o `APP_TOKEN`, aceita só a própria origem, limita 8 pedidos por minuto por IP e limita o tamanho do texto.
- Sem `GEMINI_API_KEY` e `APP_TOKEN` o backend recusa tudo (503).
- A IA só recebe o pedido do cliente e os nomes/ids dos serviços da biblioteca. Ela nunca recebe preços, custos nem horas.
