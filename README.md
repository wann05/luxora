# Luxora - Fashion Store Management System

Aplikasi web untuk mengelola data operasional toko fashion "Luxora".

## Anggota Kelompok
- Wandy Jesaya Simanjuntak (25051204059)

## Fitur Utama
Manajemen Produk
• CRUD produk lengkap: tambah, lihat, edit, dan hapus produk.
• Upload gambar produk dengan preview sebelum disimpan.
• Produk dapat dihubungkan ke kategori dan supplier melalui antarmuka yang sederhana.

Sistem Stok & Inventori
• Status stok otomatis: Tersedia, Rendah, atau Habis.
• Pengelolaan harga dan stok terpusat untuk menjaga konsistensi data.

Manajemen Kategori & Supplier
• Pengelolaan data kategori dan supplier.
• Produk terhubung langsung dengan kategori dan supplier terkait.

Transaksi & Retur
• Mendukung pencatatan transaksi penjualan.
• Mendukung pengelolaan data retur barang.

---

## 🛠️ Persiapan Awal (Prerequisites)

Sebelum mulai menjalankan aplikasi ini, pastikan komputer Anda telah terinstal:
1. **Python** (versi 3.8 ke atas)
2. **Node.js** (versi 16 ke atas)
3. **MySQL Server** (bisa menggunakan XAMPP, WAMP, atau MySQL Server langsung)

---

## ⚙️ Langkah 1: Pengaturan Database (MySQL)

Aplikasi ini menggunakan MySQL sebagai database utamanya. Konfigurasi bawaan aplikasi menggunakan kredensial standar XAMPP.

1. Buka aplikasi pengelola MySQL Anda (misal: phpMyAdmin, DBeaver, atau MySQL Workbench).
2. Buat database baru bernama **`luxora_db`**.
3. Pastikan *username* MySQL Anda adalah `root` dengan *password* dikosongkan (default XAMPP).
   *(Jika Anda menggunakan password, Anda perlu mengubahnya pada file `dashboard-backend/config/settings.py` di bagian `DATABASES`)*.

---

## 🚀 Langkah 2: Menjalankan Backend (Django)

Backend berada di dalam folder `dashboard-backend`. Ikuti langkah berikut melalui terminal/CMD:

1. Buka terminal dan masuk ke folder backend:
   ```bash
   cd dashboard-backend
   ```
2. *(Opsional namun disarankan)* Buat dan aktifkan **Virtual Environment**:
   ```bash
   # Di Windows
   python -m venv venv
   venv\Scripts\activate

   # Di Mac/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```
3. Install semua *dependencies* (pustaka yang dibutuhkan):
   ```bash
   pip install -r requirements.txt
   ```
4. Buat kerangka tabel di dalam database (Migrasi):
   ```bash
   python manage.py migrate
   ```
5. **Generate Data Dummy (Seeder)** - Sangat penting agar aplikasi tidak kosong:
   ```bash
   python manage.py seed_data
   ```
   *(Perintah ini akan secara otomatis mengisi database dengan data Kategori, Produk, Supplier, Transaksi, dan Retur).*
6. Jalankan server lokal:
   ```bash
   python manage.py runserver
   ```
   *Backend sekarang berjalan di `http://127.0.0.1:8000/`*

---

## 💻 Langkah 3: Menjalankan Frontend (React + Vite)

Frontend berada di dalam folder `dashboard-frontend`. Buka terminal/CMD **BARU** (jangan tutup terminal backend), lalu ikuti langkah ini:

1. Masuk ke folder frontend:
   ```bash
   cd dashboard-frontend
   ```
2. Install semua *dependencies* Node.js:
   ```bash
   npm install
   ```
3. Jalankan server pengembangan (Dev Server):
   ```bash
   npm run dev
   ```
4. Buka *link* yang muncul di terminal (biasanya **`http://localhost:5173`**) melalui *browser* kesayangan Anda.

🎉 **Selamat! Aplikasi Luxora Dashboard kini sudah berjalan dan siap digunakan.**

---

## 💡 Troubleshooting Umum

- **Error: "Access denied for user 'root'@'localhost'"**
  Artinya password MySQL di komputer Anda tidak kosong. Buka `dashboard-backend/config/settings.py`, cari bagian `DATABASES`, dan isi kolom `'PASSWORD'` sesuai dengan password MySQL Anda.
  
- **Error: "Unknown database 'luxora_db'"**
  Artinya Anda belum membuat database di MySQL. Silakan kembali ke Langkah 1.

- **Gambar Produk Tidak Muncul**
  Jika Anda mengunggah gambar secara manual dari UI, gambar tersebut disimpan sementara di _localStorage_ browser dan _folder_ `public/images/products/`. Jika Anda memindahkan _project_ ini, beberapa gambar bawaan mungkin perlu Anda setel ulang atau unggah ulang dari antarmuka web.
