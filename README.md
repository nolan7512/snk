# snk

Este projeto é uma versão do projeto [Platane/snk](https://github.com/Platane/snk)!

### O que esse projeto faz?

Você pode gerar um svg ou gif que é uma cobrinha comendo suas contribuições no Github.

![Snake animation](https://raw.githubusercontent.com/Sutil/Sutil/2b2fad3bf54522bb30c8c170591fc68ff51b69e6/github-contribution-grid-snake2.svg)

### O que tem de diferente do projeto original?

- O README está escrito em português! o/
- I background da imagem é semi-transparente.
- Você pode escolher a cor da cobrinha!

## Como eu posso usar?

* Crie um repositório com o mesmo nome do seu perfil no github.
  No meu caso, eu criei um repo com o nome Sutil (https://github.com/Sutil).
  Neste exemplo o repo ficará com o endereço https://github.com/Sutil/Sutil.

* Dentro deste projeto crie um arquivo README.md
  O Conteúdo deste arquivo será mostrado no seu Perfil do github.
  Veja o exemplo do [meu perfil](https://github.com/Sutil).

* Coloque a cobrinha neste arquivo de README.
  
  a) Para fazer isso, coloque a url da imagem que será gerada.

  ```md
  ![snake animation](https://github.com/<seu user name>/<seu user name>/blob/output/github-contribution-grid-snake2.svg)
  ```

  b) crie um github actions dentro do seu repo.
     Para isso crie um arquivo `.github/workflows/snake.yml`.
     
     coloque o conteúdo abaixo dentro do arquivo.


```yml

name: Generate snake game

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"
  workflow_dispatch:

jobs:
  build:
    name: Jobs to update datas
    runs-on: ubuntu-latest
    steps:
      # Snake Animation
      - uses: Sutil/snk@master
        id: snake-gif
        with:
          github_user_name: ${{ github.repository_owner }}
          svg_out_path: dist/github-contribution-grid-snake2.svg

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  
```

A cada 12 horas seu perfil será atualizado!