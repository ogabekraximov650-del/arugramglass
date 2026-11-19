# ARUGRAMGLASS

Telegram (Android) ilovasining **shisha (Liquid Glass) ko'rinishi** bilan o'zgartirilgan nusxasi — qiziqish va sinov uchun.
ARUMEDIATV loyihasining bir qismi: <https://github.com/ogabekraximov650-del/arugram>.

## Tuzilishi
| Joy | Nima |
|---|---|
| `upstream/` | `DrKLO/Telegram` (rasmiy Android ilovasi) — **git submodul**, aniq commit'ga qotirilgan (13.2.2). Kod nusxalanmaydi: repo kichik qoladi, yangilash oson |
| `patches/*.patch` | bizning o'zgarishlarimiz (tartib raqami bilan); yig'ishdan oldin `upstream/` ga qo'llanadi |
| `.github/workflows/build.yml` | GitHub Actions: submodullarni olish -> patchlarni qo'llash -> APK yig'ish (arm64-v8a) |

## Qoidalar
- Yig'ish FAQAT GitHub Actions'da (mahalliy muhitga hech narsa o'rnatilmaydi).
- `upstream/` ichidagi fayllarni to'g'ridan-to'g'ri o'zgartirmang — o'zgarish `patches/` ga yoziladi.
- Telegram yangilanganda: `upstream` commit'ini yangilab, patchlar qo'llanishini tekshiring.

## Litsenziya va Telegram qoidalari
- Telegram Android kodi **GPLv2**; bu repo uning o'zgartirilgan nusxasini tarqatadi, shuning uchun u ham GPLv2 (`LICENSE`). APK tarqatilsa, shu repo (manba) ham ochiq berilishi shart.
- Telegram'ning talabi: o'z `api_id` olish, ilova nomida "Telegram" va oq qog'oz samolyot logotipidan foydalanmaslik, foydalanuvchi ma'lumoti xavfsizligiga e'tibor.
- `api_id` / `api_hash`: repo OCHIQ bo'lgani uchun kodga yozilmaydi. Repo Settings -> Secrets and variables -> Actions ga `TG_API_ID` va `TG_API_HASH` qo'shiladi; yig'ish paytida `BuildVars.java` ga qo'yiladi (secret yo'q bo'lsa Telegram'ning standart sinov qiymati qoladi). Secret qo'shilgach Actions -> "Telegram (shisha) — APK yig'ish" -> Run workflow.
- Ilova hozircha rasmiy Telegram serverlariga ulanadi. Server almashtirish (ARUMEDIATV worker) — keyingi bosqich.

## Patchlar
1. `0001-faqat-arm64.patch` — faqat arm64-v8a (yig'ish tez va kichik).
2. `0002-shisha-standart-yoqiq.patch` — Liquid Glass + xiralashtirish hamma qurilma sinfida standart yoqiq (`LiteMode` presetlari, `SharedConfig.canBlurChat`). Sinish effekti Android 13+ da; Android 12 da faqat xiralashtirish.
