# Деплой

## Frontend (GitHub Pages) — ЗАПУЩЕН
- Адрес: https://trapdrug.github.io/yablok-IA-v2/
- `.github/workflows/pages.yml` — сборка и деплой при push в `main`.
- В сборку зашит `VITE_API_URL` (по умолчанию `https://yablok-ia-backend.onrender.com`,
  переопределяется через Settings → Secrets and variables → Actions → Variables → `VITE_API_URL`).
- Пока backend недоступен — сайт сам показывает демо-данные (mock-fallback с плашкой «демо»).
- Jekyll отключён (`.nojekyll` в артефакте), для прямых ссылок есть `404.html`.

## Backend (Render) — НУЖЕН ОДИН РУЧНОЙ ШАГ
1. Render → New → Blueprint → указать репозиторий (подхватит `render.yaml`,
   имя сервиса должно остаться `yablok-ia-backend` — тогда frontend подхватит его сам).
2. В Environment добавить секреты: `DUNGEON_API_KEY` (купленный ключ), при желании
   `AI_FUNPAY_KEY`, `POLLINATIONS_API_KEY`.
3. Render free засыпает: первый запрос после сна идёт до ~1 мин (таймаут ИИ-запросов 90 с),
   остальное в это время работает на демо-данных.

## Секреты
- Секреты НЕ в гите: `backend/.env` в `.gitignore`, в репо только `*.env.example`.
