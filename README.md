[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=zxcteen3seed2М&show_icons=true&theme=radical)](https://github.com/anuraghazra/github-readme-stats)

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=zxcteen3seed2М&layout=compact&theme=radical)](https://github.com/anuraghazra/github-readme-stats)
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *" # Обновлять каждый день в полночь
  workflow_dispatch: # Позволяет запустить вручную

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate Snake
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/snake.svg
            dist/snake-dark.svg?palette=github-dark

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.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 }}
![Snake animation](https://raw.githubusercontent.com/zxcteen3seed2/zxcteen3seed2/output/snake.svg)
