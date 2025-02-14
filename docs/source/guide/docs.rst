Документация
============

Docstring
---------

Docstring помогают в чтении вашего кода другими людьми, а также хорошо улетают в документацию. У них есть разные стили, но я рекомендую использовать ``numpydoc`` стиль. По крайней мере, под этого точно настроена документация в бойлерплейте.

Основные моменты
----------------

Документация генерируется автоматически благодаря следующему:

- Зависимости ``docs`` в ``pyproject.toml`` описывают необходимые для сборки документации пакеты.
- Команда ``install-docs`` в ``Makefile`` - устанавливает необходимые зависимости из ``pyproject.toml``.
- Директория ``./docs`` содержит необходимую базовую конфигурацию для сборки документации, а также ``source`` с ``.rst`` файлами. 
- ``documentation.yml`` файл в директории ``.github/workflows`` - автоматически подтягивается гитхабом и заставляет выполнять описанные внутри него команды:
    
   - Автоматически проверяет при ``push`` в любую ветку, всё ли хорошо с документацией.
   - При ``push`` в ``main`` собирает документацию на ветке ``documentation``.

- ``nbsphinx`` позволяет встраивать примеры-ноутбуки в документацию (например, как `здесь <https://github.com/vasilstar97/test-boilerplate/tree/main/docs/source/examples>`__).
- ``myst_parser`` позволяет встраивать части README в документацию (`пример <https://raw.githubusercontent.com/vasilstar97/test-boilerplate/refs/heads/main/docs/source/index.rst>`__):

   - Используем ``include`` и говорим, откуда читать и где закончить.
   - В README файле вставляем соответствующие комментарии.

Публикация на Github Pages
--------------------------

Github Pages позволяет создавать веб-страницы из элементов вашего репозитория. Так как наша документация автоматически собирается в ``documentation``, необходимо просто указать Pages, куда смотреть:

- Заходим в настройки **Settings** в верхней части главной страницы репозитория.
- Переходим в раздел **Pages** либо сразу по следующему адресу: ``https://github.com/{ВАШ НИКНЕЙМ}/{НАЗВАНИЕ ВАШЕГО РЕПОЗИТОРИЯ}/settings/pages``
- В **Build and deployment** выставляем:
  
  - Source - deploy from branch
  - Branch - documentation - /root

- После успешного деплоя гитхабом, ваша документация будет доступна по адресу ``https://{ВАШ НИКНЕЙМ}.github.io/{НАЗВАНИЕ ВАШЕГО РЕПОЗИТОРИЯ}``. Желательно эту же ссылку продублировать везде, где необходимо, а также вставить в описание репозитория.   