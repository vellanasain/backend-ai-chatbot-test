# TECHNICAL TEST
## Backend & AI Chatbot Developer

### 1. Tujuan Technical Test

Technical test ini bertujuan untuk mengetahui kemampuan kandidat dalam membangun backend API menggunakan Python serta mengembangkan alur kerja chatbot yang dapat mengambil informasi dari knowledge base dan menyimpan riwayat percakapan.

Penilaian akan berfokus pada:
- Kemampuan dasar Python.
- Pembuatan dan pengelolaan REST API.
- Pengelolaan database.
- Logika chatbot dan pengambilan informasi dari knowledge base.
- Kemampuan menangani error dan melakukan debugging.
- Kerapian struktur dan dokumentasi kode.

### 2. Teknologi yang Digunakan

Teknologi utama yang wajib digunakan:

| Teknologi | Keterangan |
|---|---|
| Python 3.11+ | Bahasa pemrograman |
| FastAPI | Framework backend API |
| SQLite | Database lokal |
| REST API | Komunikasi antar layanan |
| Git & GitHub | Pengelolaan dan pengumpulan kode |

**Ketentuan AI Chatbot:**
- Kandidat tidak diwajibkan menggunakan API OpenAI, Gemini, atau layanan AI berbayar.
- Kandidat dapat menggunakan Mock LLM Provider, yaitu simulasi layanan AI untuk menguji alur chatbot tanpa API key.
- Kandidat tetap harus membuat alur retrieval, penyusunan context, dan pembentukan jawaban.
- Penggunaan LLM sungguhan diperbolehkan secara opsional menggunakan API key milik kandidat sendiri. API key tidak boleh dicantumkan di repository.

### 3. Ketentuan Pengerjaan

1. Pengerjaan dilakukan secara individu.
2. Waktu pengerjaan maksimal 3 hari sejak soal diberikan.
3. Kandidat diperbolehkan menggunakan dokumentasi, Google, dan AI tools seperti ChatGPT atau GitHub Copilot.
4. Kandidat harus memahami kode yang dibuat dan tidak sekadar menyalin hasil dari AI.
5. Kode harus dapat dijalankan secara lokal tanpa membutuhkan akses ke server perusahaan.
6. Tidak diperbolehkan mencantumkan API key, password, atau informasi rahasia di dalam repository.
7. Kandidat wajib menyertakan dokumentasi cara instalasi dan menjalankan aplikasi.

---

### 4. Tugas Utama

#### A. Python Programming

Buat program Python sederhana untuk menyelesaikan beberapa kasus berikut:

**1. Pengolahan Transaksi**

Diberikan data transaksi:

```python
transactions = [
    {"customer": "Andi", "amount": 500000, "status": "paid"},
    {"customer": "Budi", "amount": 300000, "status": "unpaid"},
    {"customer": "Andi", "amount": 200000, "status": "paid"},
    {"customer": "Citra", "amount": 700000, "status": "paid"}
]
```

Buat fungsi untuk:
- Menghitung total transaksi yang berstatus paid.
- Menghitung jumlah transaksi paid dan unpaid.
- Mengelompokkan total transaksi berdasarkan customer.

**2. Pencarian Informasi**

Buat fungsi untuk mencari informasi berdasarkan kata kunci dari sekumpulan data teks.

**3. Validasi Data**

Buat fungsi untuk memvalidasi input JSON. Jika data tidak sesuai format atau terdapat field wajib yang kosong, program harus memberikan pesan error yang jelas.

#### B. Backend API

Buat aplikasi backend menggunakan FastAPI dengan endpoint berikut:

| Method | Endpoint | Fungsi |
|---|---|---|
| GET | `/health` | Mengecek status aplikasi |
| POST | `/chat` | Mengirim pesan ke chatbot |
| GET | `/conversations/{id}` | Melihat riwayat percakapan |
| DELETE | `/conversations/{id}` | Menghapus percakapan |
| POST | `/knowledge-bases` | Menambahkan knowledge base |
| GET | `/knowledge-bases` | Melihat daftar knowledge base |
| DELETE | `/knowledge-bases/{id}` | Menghapus knowledge base |

Ketentuan:
- API menerima dan mengembalikan data dalam format JSON.
- Setiap percakapan memiliki ID yang berbeda.
- Chatbot dapat membuat percakapan baru jika belum ada ID percakapan.
- Setiap pesan pengguna dan jawaban chatbot tersimpan di database.
- API harus memiliki penanganan error yang sesuai.

#### C. AI Chatbot dan Knowledge Base

Buat chatbot sederhana yang dapat menjawab pertanyaan berdasarkan informasi di dalam knowledge base.

Alur chatbot yang diharapkan:

1. Pengguna mengirimkan pertanyaan melalui endpoint `/chat`.
2. Sistem mencari informasi yang relevan dari knowledge base.
3. Informasi yang ditemukan digunakan sebagai context untuk membentuk jawaban.
4. Chatbot memberikan jawaban berdasarkan informasi yang tersedia.
5. Pesan pengguna dan jawaban chatbot disimpan ke database.

Ketentuan:
- Chatbot harus dapat mengambil informasi yang relevan dari knowledge base.
- Chatbot tidak boleh mengarang informasi yang tidak tersedia.
- Jika informasi tidak ditemukan, chatbot harus memberikan respons bahwa informasi belum tersedia.
- Chatbot harus dapat mempertahankan konteks percakapan.
- Riwayat percakapan yang berbeda tidak boleh tercampur.

Penggunaan metode pencarian kata kunci diperbolehkan. Penggunaan TF-IDF, embeddings, atau vector database menjadi nilai tambahan, bukan kewajiban.

#### D. Database

Gunakan SQLite untuk menyimpan data aplikasi.

Minimal terdapat tiga jenis data:

1. **Knowledge Base:** menyimpan informasi yang digunakan chatbot.
2. **Conversations:** menyimpan identitas dan informasi percakapan.
3. **Messages:** menyimpan pesan pengguna dan jawaban chatbot.

Kandidat bebas menentukan struktur tabel dan relasi selama data dapat dikelola dengan baik.

#### E. Debugging dan Problem Solving

Jelaskan bagaimana kandidat akan menangani tiga kasus berikut:

**Kasus 1 — API Error**

Ketika pengguna mengirim pesan, API mengembalikan status `500 Internal Server Error`.

Jelaskan kemungkinan penyebab dan langkah yang akan dilakukan untuk menemukan sumber masalah.

**Kasus 2 — Jawaban Chatbot Tidak Sesuai**

Knowledge base menyimpan informasi harga paket Silver sebesar Rp700.000, tetapi chatbot menjawab Rp900.000.

Jelaskan kemungkinan penyebab dan bagaimana cara memperbaikinya.

**Kasus 3 — Riwayat Percakapan Tercampur**

Ketika dua pengguna mengirimkan pesan secara bersamaan, chatbot justru menggunakan riwayat percakapan pengguna lain.

Jelaskan kemungkinan penyebab dan solusi untuk mencegah masalah tersebut.

---

### 5. Dataset Knowledge Base

Gunakan informasi berikut sebagai sumber pengetahuan chatbot. Kandidat tidak perlu menambahkan informasi lain di luar data yang diberikan.

| Paket | Harga | Keterangan |
|---|---:|---|
| Silver | Rp700.000 | Domain web.id, 4 menu, 500 MB, maksimal 30 foto |
| Gold | Rp1.600.000 | Harga promo Rp1.500.000, DP minimal Rp600.000 |
| Diamond | Rp2.000.000 | Paket Diamond |
| Platinum | Rp3.000.000 | Harga promo Rp2.800.000 |

Informasi tambahan:
- Perpanjangan paket Silver sebesar Rp500.000 per tahun.
- Setiap website mendapatkan maksimal 3 kali revisi gratis.
- Revisi gratis berlaku selama 1 bulan setelah pelunasan.
- Revisi di luar ketentuan tersebut dikenakan biaya tambahan.

### 6. Skenario Pengujian Chatbot

Pastikan chatbot dapat menangani beberapa pertanyaan berikut:

| No. | Pertanyaan | Informasi yang Diharapkan |
|---|---|---|
| 1 | Berapa harga paket Silver? | Rp700.000 |
| 2 | Apa saja fasilitas paket Silver? | Domain web.id, 4 menu, 500 MB, maksimal 30 foto |
| 3 | Berapa DP minimal paket Gold? | Rp600.000 |
| 4 | Berapa biaya perpanjangan Silver? | Rp500.000 per tahun |
| 5 | Berapa kali revisi gratis yang didapatkan? | Maksimal 3 kali |
| 6 | Apakah tersedia layanan pembuatan aplikasi mobile? | Chatbot menyatakan informasi belum tersedia |
| 7 | Apakah revisi setelah 1 bulan masih gratis? | Tidak, revisi di luar ketentuan dikenakan biaya tambahan |

Selain itu, lakukan pengujian:
- Mengirim beberapa pesan dalam satu percakapan.
- Membuat dua percakapan berbeda.
- Memastikan riwayat percakapan tidak tercampur.
- Menghapus salah satu percakapan.
- Memastikan data knowledge base tersimpan dan dapat digunakan kembali.

---

### 7. Optional Features (Nilai Tambahan)

Fitur berikut tidak wajib, tetapi dapat menjadi nilai tambah:

- Menggunakan LLM sungguhan melalui API atau model lokal.
- Menggunakan embeddings atau vector database.
- Menampilkan sumber informasi yang digunakan chatbot.
- Menggunakan Redis untuk pengelolaan cache atau percakapan.
- Menggunakan asynchronous processing.
- Menambahkan unit testing.
- Menggunakan Docker.

Fitur tambahan tidak otomatis mendapatkan nilai tinggi. Kualitas implementasi dan kesesuaian fungsi tetap menjadi prioritas.

---

### 8. Hasil yang Harus Dikumpulkan

Kandidat wajib mengumpulkan:

1. **GitHub Repository**
   - Source code lengkap.
   - Struktur folder yang rapi.
   - File `requirements.txt`.
   - File `.env.example` jika diperlukan.

2. **README.md**
   - Penjelasan proyek.
   - Teknologi yang digunakan.
   - Cara instalasi.
   - Cara menjalankan aplikasi.
   - Daftar endpoint API.
   - Contoh penggunaan API.

3. **Database**
   - Struktur database atau file SQL untuk membuat tabel.
   - Database SQLite hasil pengerjaan jika diperlukan untuk pengujian.

4. **Dokumentasi Pengujian**
   - Bukti pengujian endpoint.
   - Hasil pengujian skenario chatbot.
   - Bukti bahwa riwayat percakapan tersimpan dengan benar.

5. **Jawaban Debugging**
   - Jawaban tertulis untuk ketiga kasus pada bagian D.

6. **Video Demo**
   - Durasi sekitar 3–5 menit.
   - Menunjukkan aplikasi berhasil dijalankan.
   - Menunjukkan pengujian chatbot dan database.
   - Menjelaskan secara singkat alur kerja aplikasi.

### 9. Penutup

Kandidat diharapkan dapat menyelesaikan tugas sesuai ketentuan yang telah diberikan. Fokus utama technical test ini adalah kemampuan membangun backend yang berfungsi dengan baik, mengelola data, serta memahami alur kerja chatbot berbasis knowledge base.

Selamat mengerjakan.
