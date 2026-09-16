# Колесо подарков для Bizon365

Виджет добавляет на страницу эфира плавающую кнопку. По нажатию открывается модальное окно с колесом. Результат каждой прокрутки сохраняется в `localStorage` браузера, после выигрыша появляется прямая кнопка скачивания PDF с Google Drive.

## Общий управляемый код

Этот вариант получает номер активной прокрутки и видимость кнопки из `config.json`:

```html
<script src="https://xbaranova-neiro.github.io/prize-wheel-bizon-widget/widget.js" defer></script>
```

Для Bizon рекомендуется встроенный режим: кнопка появится в том месте HTML-блока, куда вставлен код, с отступом 18 пикселей сверху:

```html
<script src="https://xbaranova-neiro.github.io/prize-wheel-bizon-widget/widget.js" data-placement="inline" defer></script>
```

## Фиксированные коды

Первая прокрутка:

```html
<script src="https://xbaranova-neiro.github.io/prize-wheel-bizon-widget/widget.js?round=1" defer></script>
```

Вторая прокрутка:

```html
<script src="https://xbaranova-neiro.github.io/prize-wheel-bizon-widget/widget.js?round=2" defer></script>
```

Третья прокрутка:

```html
<script src="https://xbaranova-neiro.github.io/prize-wheel-bizon-widget/widget.js?round=3" defer></script>
```

Фиксированный код показывает кнопку только тогда, когда соответствующая прокрутка включена в удалённой конфигурации.

## Удалённое управление

Основная панель: <https://xbaranova-neiro.github.io/prize-wheel-bizon-widget/admin.html>

При первом открытии панели нужен fine-grained GitHub token с доступом только к репозиторию `prize-wheel-bizon-widget` и разрешением **Contents: Read and write**. Токен вводится непосредственно в браузере и не отправляется на сторонние серверы.

GitHub Actions остаётся запасным способом управления:

Откройте в GitHub вкладку **Actions**, выберите **Управление виджетом Bizon**, нажмите **Run workflow** и выберите:

- `round-1` — включить первую прокрутку;
- `round-2` — включить вторую;
- `round-3` — включить третью;
- `off` — скрыть кнопку у всех зрителей.

Виджеты проверяют состояние раз в 15 секунд. Вращение выполняется локально в браузере, поэтому одновременные нажатия зрителей не создают очередь на сервере.
