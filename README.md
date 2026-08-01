# MAXIMUM · AI-Бюджет

Живой дашборд контроля AI-расходов: токены LLM, инструменты и подписки, инфраструктура.

## Как это работает

1. **Финансовый агент (Financier)** сканирует почту (чеки OpenRouter, Anthropic, Firecrawl, ElevenLabs…) и мониторит API-балансы (DeepSeek, OpenRouter) через `api_cost_monitor.py`.
2. После каждой оплаты агент запускает `update_dashboard.py`:
   - читает чеки (`expenses_full.json`) и историю балансов (`api_costs_history.json`)
   - тянет живые балансы с API
   - генерирует `data.json`
   - пушит в этот репозиторий → GitHub Pages пересобирается автоматически
3. Сайт показывает актуальную картину: балансы, расход за месяц, разбивка по назначению, последние платежи. Страница сама обновляется каждую минуту.

## Обновление вручную

```bash
python3 /root/.hermes/scripts/update_dashboard.py
```

## Структура

| Файл | Назначение |
|------|------------|
| `index.html` | Лендинг-дашборд (Chart.js, тёмная тема) |
| `data.json` | Данные: балансы, категории, платежи (генерируется) |
| `.github/workflows/pages.yml` | Деплой на GitHub Pages |

## Категории расходов

- **Токены LLM** — DeepSeek, OpenRouter, Anthropic (Claude)
- **Инструменты и подписки** — Firecrawl, ElevenLabs, Aqua Voice, fal.ai, Google Play
- **Инфраструктура** — Cloudflare, Hetzner

---

MAXIMUM Group · Novi Sad · https://github.com/tarasenko-maximum
