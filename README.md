# CFOP · Localizador de Operações

Consulta informativa de **CFOP** (Código Fiscal de Operações e Prestações): busque pelo código ou por palavra-chave do título e da nota explicativa, filtre por fluxo e natureza da operação e veja a ficha completa do CFOP.

- **Base local:** 619 CFOPs da tabela oficial **IT 2023.002 v2.10** (Ajuste SINIEF 07/2005 e alterações) — grupos `1xxx`, `2xxx`, `3xxx`, `5xxx`, `6xxx` e `7xxx`.
- **Arquivo único:** `index.html` (HTML + CSS + JS + dados embutidos). Sem build, sem dependências, funciona abrindo o arquivo ou via GitHub Pages.
- **Uso informativo:** não substitui a legislação nem o texto oficial (SEFAZ / Portal NF-e).

> ⚠ **Aviso:** em caso de divergência, prevalece a legislação vigente. Devolução em regra espelha a operação de origem (ex.: venda `5.102` → devolução `1.202` na mesma UF; venda `6.102` → `2.202` em outra UF).

## Funcionalidades

- Busca por **código** (completo ou prefixo — ex.: `59` lista todos os `59xx`) e por **palavra-chave** (título + descrição, sem acento).
- Filtros por **fluxo** (entradas `1·2·3` / saídas `5·6·7`), **abrangência** (interna `1·5`, interestadual `2·6`, exterior `3·7`) e **natureza** (devolução, retorno, remessa, anulação, combustível) via indicadores oficiais (`indDevol`, `indRetor`, `indRemes`, `indAnula`, `indComb`, `indComunica`, `indTransp`).
- Atalhos rápidos: Devolução, Remessa, Retorno, Anulação, Combustível, Transporte, Comunicação.
- **Ficha do CFOP:** título, descrição/nota explicativa, marcadores, vigência inicial e indicação de NF-e, com botões para copiar código e título.
- **Exportação CSV** do resultado filtrado (separador `;`, com BOM para Excel).
- Layout em 3 painéis (filtros · resultados em cartões · ficha), responsivo.

## Estrutura

```text
consulta-cfop/
├── index.html   # app completo (layout atual em 3 painéis)
├── index - Copia.html  # cópia de segurança do layout anterior
└── README.md
```

## Como usar

1. Abra `index.html` no navegador **ou** sirva a pasta localmente:

   ```bash
   # qualquer servidor estático, ex.:
   npx serve consulta-cfop
   ```

2. Digite o CFOP ou uma palavra-chave (ex.: `5102`, `bonificação`, `venda à ordem`), ajuste os filtros e clique em um cartão para ver a ficha completa.

## Publicar no GitHub Pages

1. Crie o repositório e envie a pasta (ou só o `index.html` na raiz / em `docs/`).
2. Em **Settings → Pages**, selecione a branch e a pasta (`/root` ou `/docs`).
3. Acesse a URL gerada (`https://<usuario>.github.io/<repo>/`).

## Fonte dos dados

- Tabela CFOP — **IT 2023.002 v2.10** (Ajuste SINIEF 07/2005 e alterações), processada a partir do arquivo `IT_2023_002_v2_10_Tabela_CFOP_Descrição.md`.
- Cada registro contém: `CFOP`, `título`, `descrição (nota explicativa)`, `início de vigência` e indicadores (`indNFe`, `indDevol`, `indRetor`, `indAnula`, `indRemes`, `indComb`, `indComunica`, `indTransp`, `indExcIBSCBS`).
- Conferência desta página: **17/09/2026**.

## Limitações conhecidas

- O arquivo-fonte usa `NaN` em `fim de vigência` (sem fim definido); a ficha exibe apenas o início de vigência.
- A base é um retrato da IT 2023.002 v2.10 — valide operações críticas no texto oficial vigente.

## Licença

Defina a licença do repositório (ex.: `MIT`) antes de publicar. Os dados do CFOP são de origem oficial/tributária; este projeto apenas reorganiza a consulta para fins informativos.
