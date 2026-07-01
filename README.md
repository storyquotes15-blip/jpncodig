# GramCode Gallery

Isi zip ini:
- `index.html` = frontend IG-style, CSS dan JS sudah digabung.
- `worker.js` = API Cloudflare Worker untuk feed, search CODE, dan embed video.

Cara pakai cepat:
1. Upload `index.html` ke Cloudflare Pages.
2. Buat Cloudflare Worker dari `worker.js`.
3. Route Worker ke domain yang sama, misalnya `/api/*`.
4. Nanti Telegram bot tinggal menyimpan feed ke KV key `feed` dengan format JSON array:

```json
[
  {"code":"MIDV-123","caption":"Caption bebas","cover":"https://url-cover.jpg"}
]
```

Catatan:
- Search CODE manual membuka `/p/CODE`.
- Worker hanya mencari gambar dari area `<div class="p-slider -work">` bila tersedia.
- Fungsi `makeUpload18Embed()` perlu kamu sesuaikan dengan format embed Upload18 yang kamu pakai.

CARA PAKAI feed.js

1. Upload feed.js satu folder dengan index.html.

2. Di index.html, tambahkan ini sebelum script utama atau sebelum </body>:

<script src="feed.js"></script>

3. Di bagian renderHome(), pastikan feed memakai:

let posts = window.DEMO_FEED || [];

4. Kalau mau tambah postingan baru, buka feed.js lalu tambah baris:

['CODE-BARU', 'https://link-gambar.jpg'],
