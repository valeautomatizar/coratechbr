# Site Coratech — Guia rápido de edição

Site estático (HTML + CSS + JS puro). Não precisa de instalação nem de build:
basta abrir o `index.html` no navegador ou subir a pasta inteira para qualquer hospedagem
(Hostinger, Locaweb, HostGator, Netlify, Vercel, GitHub Pages…).

## Estrutura

```
index.html            → página principal
privacidade.html      → Política de Privacidade (LGPD)
termos.html           → Termos de Uso
assets/css/style.css  → visual (cores, fontes, espaçamentos)
assets/js/main.js     → dados de contato + animações
assets/img/           → logos, símbolo e favicon (extraídos do Manual da Marca)
assets/img/projetos/  → coloque aqui as fotos dos projetos
```

## 1. Dados de contato (WhatsApp, e-mail, Instagram, cidade)

Abra `assets/js/main.js` e edite o bloco `CONFIG` no topo do arquivo.
Se um campo ficar vazio (`''`), o item correspondente some do site.
Depois de editar CSS ou JS, aumente o número em `?v=2` nos `<link>`/`<script>` das 3 páginas,
para que os visitantes não vejam a versão antiga em cache.
Esses dados são aplicados automaticamente em todos os botões e páginas.

```js
const CONFIG = {
  whatsapp: '5562999998888',   // 55 + DDD + número, só dígitos
  telefone: '(62) 99999-8888',
  email: 'contato@coratech.com.br',
  instagram: 'https://instagram.com/coratech',
  cidade: 'Goiânia — GO',
  ...
};
```

O formulário de contato **abre o WhatsApp** com a mensagem já preenchida (nome, telefone,
tipo de imóvel e interesses). Não precisa de servidor.

## 2. Fotos dos projetos

As fotos ficam em `assets/img/projetos/` (JPG de até 1600px, ~300 KB cada).
Para trocar ou adicionar uma foto, na seção **PROJETOS** do `index.html`, altere o caminho nos dois lugares de cada projeto:

```html
<article class="project ..." data-full="assets/img/projetos/home-theater.jpg">
  <div class="project__img" style="background-image: url('assets/img/projetos/home-theater.jpg'); background-position: center"></div>
```

- `data-full` → foto que abre ampliada ao clicar (galeria com setas, Esc fecha, deslizar no celular).
- `background-position` → ajusta o enquadramento (ex.: `center 30%` mostra mais da parte de cima).
- `project--lg` → card largo. A grade usa linhas de 12 colunas: card largo (8) + normal (4), ou três normais (4+4+4).

Fotos do iPhone (.heic) precisam ser convertidas para JPG antes. No Mac, pode usar:

```bash
sips -s format jpeg -s formatOptions 72 -Z 1600 FOTO.heic --out assets/img/projetos/nome.jpg
```

## 3. Textos

Todos os textos estão no `index.html`, separados por comentários grandes
(`HERO`, `SOLUÇÕES`, `MANIFESTO`, `EXPERIÊNCIAS`, `PROJETOS`, `PROCESSO`, `DÚVIDAS`, `CONTATO`, `RODAPÉ`).

- Palavras em *itálico azul* nos títulos: envolva com `<em class="accent">…</em>`.
- Manifesto: palavras entre `*asteriscos*` acendem em azul.
- Cenas do painel do topo (Receber, Cinema, Jantar, Boa noite): bloco `SCENES` no `main.js`.

## 4. Cores e fontes

No topo do `assets/css/style.css`, em `:root`:

| Variável     | Cor       | Origem no Manual                    |
|--------------|-----------|-------------------------------------|
| `--blue`     | `#0096D6` | Azul Coratech Automação (degradê)   |
| `--blue-2`   | `#007BA8` | Azul Coratech Automação (uma cor)   |
| `--teal`     | `#035457` | Coratech Grupo                      |
| `--orange`   | `#E8833A` | Coratech Construções (só acento)    |
| `--graphite` | `#272E2F` | Grafite da marca                    |
| `--paper`    | `#F1F2F2` | Off-white da capa                   |

Fonte: **Libre Franklin** (Google Fonts), da família Franklin indicada no manual.
O logotipo usa a fonte Slant original, convertida em vetor — por isso não depende de fonte instalada.

## 5. Antes de publicar — checklist

- [x] WhatsApp, telefone e e-mail no `CONFIG` do `main.js`
- [x] Endereço no `CONFIG`
- [ ] Instagram no `CONFIG` (vazio = ícone fica oculto)
- [x] Dados da empresa nas páginas legais (Coratech Ltda, CNPJ, endereço, foro Ijuí/RS)
- [x] Colocar fotos reais dos projetos
- [ ] Revisar as respostas da seção **Dúvidas** e os textos dos projetos
- [ ] Se adicionar Google Analytics / Meta Pixel, atualizar a seção 6 (Cookies) da Política de Privacidade

## Visualizar localmente

Basta dar dois cliques no `index.html`. Ou, no terminal, dentro da pasta:

```bash
python3 -m http.server 8000
```

e abra http://localhost:8000
