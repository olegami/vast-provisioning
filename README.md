# vast-provisioning

Манифесты провижининга для GPU-инстансов Vast.ai, которые заказывает Telegram-бот.

Шаблон `vastai/comfy` содержит встроенный декларативный провижинер: бот передаёт
ссылку на манифест в переменной `PROVISIONING_MANIFEST`, провижинер скачивает
файлы (Hugging Face — через `hf download`, параллельно, с повторами) и снимает
флаг `/.provisioning`, после чего стартует ComfyUI.
Формат манифеста: https://github.com/vast-ai/base-image — `ROOT/opt/instance-tools/lib/provisioner/README.md`.

Секретов в манифестах нет: только публичные ссылки.

| Манифест | Профиль бота | Что внутри | Объём |
|---|---|---|---|
| `h3/fl2va_3090.yaml` | `minimax_3h_3090` | MiniMax H3 FL2VA pruned INT8, энкодер NVFP4, VAE, turbo-LoRA 4/8 шагов, шаблоны T2V/I2V | ~46 GB |
| `h3/fl2va_h100.yaml` | `minimax_3h_h100` | MiniMax H3 FL2VA pruned BF16, энкодер BF16, VAE, turbo-LoRA 8 шагов, шаблоны T2V/I2V (переключены на BF16) | ~100 GB |

Ссылка для бота: `https://raw.githubusercontent.com/olegami/vast-provisioning/main/h3/<файл>.yaml`
(после отладки — закрепить на хэше коммита вместо `main`).

Лицензия модели MiniMax H3: MiniMax H3 Community License — см. https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/LICENSE
