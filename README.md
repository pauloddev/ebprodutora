# Produtora EB: landing page

Site estático (HTML + CSS + JS puro, sem build). Pronto para GitHub + Vercel.

> Se alguma foto ou vídeo não aparecer no site publicado, confira se os 82 arquivos estão no GitHub. Veja "Enviar para o GitHub" abaixo.

## Estrutura

**Todos os arquivos ficam soltos, sem nenhuma pasta** (82 arquivos). Isso foi feito de propósito para o envio ao GitHub funcionar em um único upload pelo botão "choose your files", que não aceita pastas e aceita até 100 arquivos por vez.

- `index.html`: página principal, com o CSS (tag `<style>`) e o JS (tag `<script>`) embutidos
- `404.html`: página de erro personalizada (noindex)
- `robots.txt`, `sitemap.xml`, `site.webmanifest`, `vercel.json`
- `favicon.ico`, `favicon.svg`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, `og-image.jpg`
- `*.webp` (fotos) e `logo-produtora-eb.png`
- `eb-video-01.mp4` a `eb-video-11.mp4` e as capas `eb-video-XX.webp`
- `bebas-neue-latin-400.woff2` e `manrope-latin-var.woff2` (fontes)

## Enviar para o GitHub (1 envio só)

1. Descompacte o zip. Abra a pasta descompactada: lá dentro só tem arquivos, nenhuma pasta.
2. No repositório do GitHub, clique em **Add file → Upload files → choose your files**.
3. Na janela, clique em qualquer arquivo e aperte **Ctrl + A** para selecionar os 82 arquivos. Clique em **Abrir**.
4. Espere a barra de envio terminar (os vídeos somam cerca de 72 MB) e clique em **Commit changes**.
5. O Vercel publica sozinho em cerca de 1 minuto. Abra o site e aperte **Ctrl + F5**.

## URL do site (SITE_URL)

Já configurada com o link de produção: `https://ebprodutora.vercel.app`. Ela aparece em:

| Arquivo | Linha(s) | O que é |
|---|---|---|
| index.html | 10 | `<link rel="canonical">` |
| index.html | 25, 26 | `og:url`, `og:image` |
| index.html | 33 | `twitter:image` |
| index.html | 46, 49, 50, 51 | JSON-LD (`@id`, `url`, `image`, `logo`) |
| robots.txt | 4 | linha `Sitemap:` |
| sitemap.xml | 4 | `<loc>` da home |

Se um dia conectar um domínio próprio, faça "Localizar e substituir" de `https://ebprodutora.vercel.app` pelo domínio novo nesses arquivos.

Outros itens:
- **og-image.jpg**: já existe uma versão (logo + foto de evento, 1200x630). Se quiser outra arte, substitua o arquivo mantendo nome e tamanho.
- **Favicons**: já gerados a partir da logo oficial. Para trocar, mantenha os nomes e tamanhos da tabela acima.
- **sitemap.xml `<lastmod>`**: atualize a data quando mudar o conteúdo.
- **JSON-LD**: preenchido só com dados do site (nome, telefone, e-mail, endereço, Instagram, região atendida, CEO). Não há horário de funcionamento nem coordenadas porque essas informações não foram fornecidas; se quiser, adicione `openingHours` e `geo`.

## Publicar no Vercel via GitHub

1. Crie um repositório no GitHub e envie os 82 arquivos (veja "Enviar para o GitHub"). O `index.html` deve ficar na raiz do repositório.
2. No Vercel: **Add New → Project → Import** o repositório.
3. Framework Preset: **Other**. Build Command: vazio. Output Directory: vazio (raiz). Clique em **Deploy**.

## Conferir depois de publicar

1. Abra `https://ebprodutora.vercel.app/robots.txt` e `https://ebprodutora.vercel.app/sitemap.xml`: os dois devem mostrar o link `https://ebprodutora.vercel.app`.
2. Abra um endereço inexistente (ex.: `https://ebprodutora.vercel.app/teste`) para ver a página 404.
3. Use sempre o link de produção. Links de *preview* (com um código no nome) recebem `noindex` automaticamente; isso é normal.

## Google Search Console

1. Acesse search.google.com/search-console → **Adicionar propriedade** → **Prefixo do URL** → cole `https://ebprodutora.vercel.app/`.
2. Verificação: escolha **Tag HTML**, copie a meta tag e cole no `<head>` do `index.html` (logo abaixo de `<meta name="robots" ...>`). Faça commit, aguarde o deploy e clique em **Verificar**.
3. Menu **Sitemaps** → envie `sitemap.xml`.
4. Menu **Inspeção de URL** → cole a URL da home → **Solicitar indexação**.

A indexação depende da avaliação do próprio Google e pode levar de dias a semanas. Este projeto prepara o site para ser encontrado; ele não garante a indexação.

## Se no futuro conectar um domínio próprio

1. Vercel → Project → **Settings → Domains** → adicione o domínio e configure o DNS como o Vercel indicar.
2. Defina o domínio próprio como principal e configure o `.vercel.app` para **redirecionar (308)** para ele (opção "Redirect to" na lista de domínios).
3. Substitua o link `.vercel.app` pelo domínio novo em todos os arquivos da tabela e publique.
4. No Search Console, adicione a nova propriedade (de preferência **Domínio**, verificada por DNS), envie de novo o `sitemap.xml` e, na propriedade antiga, use **Alteração de endereço** apontando para a nova.
