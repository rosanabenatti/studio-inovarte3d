# Loja Studio Inovarte 3D

Site de catálogo com carrinho. O cliente escolhe os produtos, monta o pedido e envia pelo WhatsApp com o resumo e o valor do sinal de 50%. Você responde com a chave Pix. Custo: zero.

## O que tem na pasta

- `index.html`: o site inteiro (um arquivo só).
- `produtos.csv`: a lista de produtos, pronta para abrir no Google Planilhas.
- `img/`: as fotos dos produtos.

## 1. Editar produtos pela planilha (adicionar, mudar preço, excluir)

1. No Google Planilhas, crie uma planilha nova e use Arquivo > Importar > Enviar, escolhendo `produtos.csv`.
2. Cada linha é um produto. Para **adicionar**, crie uma linha nova. Para **excluir**, apague a linha (ou escreva `nao` na coluna `ativo` para só esconder).
3. Vá em Arquivo > Compartilhar > Publicar na web. Escolha a aba dos produtos, o formato **CSV**, clique em Publicar e copie o link.
4. Abra o `index.html` em qualquer editor de texto e cole o link em `planilhaCsv`, no começo do script:

```
planilhaCsv: "https://docs.google.com/spreadsheets/d/e/.../pub?output=csv",
```

Depois disso, qualquer mudança na planilha aparece no site sozinha (o Google pode levar alguns minutos para atualizar).

### Colunas da planilha

| Coluna | Para que serve |
|---|---|
| `id` | Nome curto sem espaços (ex.: `chaveiro-fe`). |
| `categoria` | Cria as abas do site (Chaveiros, Decoração, Brindes ou outra). |
| `nome`, `descricao` | Texto do produto. |
| `imagem` | `img/nome-da-foto.jpg` (foto na pasta `img`) ou um link direto de imagem. |
| `variantes` | Opções de preço no formato `rótulo=preço`, separadas por `\|`. Ex.: `1 unidade=3,00\|5 unidades=19,80`. Produto com preço único: `cada=17,90`. |
| `escolha_rotulo`, `escolhas` | Escolha obrigatória do cliente, como cor ou modelo. Ex.: rótulo `Cor`, escolhas `Preto\|Vermelho\|Bege`. |
| `personalizar` | Pergunta do campo de texto (ex.: `Nome que vai na bola`). Deixe vazio se não precisa. |
| `prazo` | Ex.: `7 dias`. |
| `novo` | `sim` mostra a etiqueta NOVO. |
| `ativo` | `sim` mostra, `nao` esconde. |

## 2. Colocar no ar de graça

O jeito mais simples: acesse app.netlify.com/drop e arraste a **pasta inteira** (com `index.html` e `img`). Você recebe um link na hora. Dá para trocar o nome do link nas configurações do site e, depois, ligar um domínio próprio se quiser. Vercel e GitHub Pages também servem.

Para foto de produto novo, ponha o arquivo na pasta `img` e envie a pasta de novo, ou use um link direto de imagem na coluna `imagem`.

## 3. Pix

Por enquanto o Pix é manual: o cliente envia o pedido pelo WhatsApp, você confirma prazo e frete e manda a chave Pix com o valor do sinal (50%). Se quiser que a chave apareça no carrinho, preencha `chavePix` no começo do script do `index.html`.

## Conferir antes de publicar

- Os kits de brindes (`Kit 10 un`, `Kit 20 un`, `Kit 50 un` do Chaveiro Nossa Senhora Aparecida) foram lidos como preço do kit inteiro, como está no catálogo. Confirme se é isso mesmo.
- O número de WhatsApp está em `whatsapp`, no começo do script.
