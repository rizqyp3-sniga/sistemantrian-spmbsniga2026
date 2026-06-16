# 🎟️ Sistem Antrian Online SPMB - SMP Negeri 3 Pemalang

Sistem Antrian Online berbasis web yang dirancang khusus untuk memfasilitasi proses verifikasi berkas pendaftaran siswa baru di SMP Negeri 3 Pemalang. Sistem ini memungkinkan calon pendaftar mengambil nomor antrian secara real-time dari rumah untuk jadwal verifikasi esok hari.

## ✨ Fitur Utama

- **Real-time Queue Status**: Menampilkan sisa kuota dan antrian yang terpakai secara langsung di halaman utama.
- **Dual Track Registration**: Mendukung pendaftaran jalur **Mandiri** (Individu) dan **Kolektif** (Sekolah Asal).
- **Anti-Bentrok (Concurrency Lock)**: Dilengkapi dengan `LockService` pada backend untuk mencegah duplikasi nomor antrian meskipun banyak pendaftar mengakses secara bersamaan.
- **Pemisahan Jalur Antrian**: Nomor antrian dibedakan secara otomatis menggunakan prefix (**M-** untuk Mandiri dan **K-** untuk Kolektif).
- **Admin Dashboard**: Panel khusus administrator untuk memantau data pendaftar secara real-time.
- **Search by NISN**: Memungkinkan pendaftar mengecek kembali nomor antrian mereka hanya dengan memasukkan NISN.
- **Data Export**: Fitur ekspor data pendaftar ke format CSV untuk pengolahan di Excel.
- **Modern UI/UX**: Antarmuka responsif menggunakan Tailwind CSS dengan dukungan Mode Gelap (Dark Mode).

## 🚀 Teknologi yang Digunakan

- **Frontend**: Tailwind CSS, JavaScript (ES6+), Lucide Icons.
- **Backend**: Google Apps Script (Web App).
- **Database**: Google Sheets.
- **Fonts**: Plus Jakarta Sans.

## 🛠️ Panduan Instalasi & Konfigurasi

### 1. Persiapan Google Sheets & Apps Script
1. Buat Google Sheets baru dan beri nama, misalnya `Data Antrian SPMB`.
2. Ubah nama sheet pertama menjadi `Data_Antrian`.
3. Pastikan kolom **C** (Tanggal Antrian) diatur ke format **Plain Text** (Format > Number > Plain Text).
4. Buka **Extensions** > **Apps Script**.
5. Masukkan kode backend (Google Apps Script) yang mengelola fungsi `doPost` dan `doGet`.
6. Klik **Deploy** > **New Deployment**.
    - **Type**: Web App
    - **Execute as**: Me
    - **Who has access**: Anyone
7. Salin **Web App URL** yang muncul.

### 2. Konfigurasi Frontend
1. Buka file `index.html`.
2. Cari bagian `const CONFIG` di dalam tag `<script>`.
3. Tempel URL Web App yang sudah disalin ke variabel `webhook_url`:
   ```javascript
   const CONFIG = {
     main_title: 'Sistem Antrian SPMB',
     school_name: 'SMP Negeri 3 Pemalang',
     webhook_url: 'URL_WEB_APP_ANDA_DISINI'
   };
   ```
4. Simpan file.

### 3. Pengaturan Kuota & Waktu
- Untuk mengubah kuota harian, cari variabel berikut di `index.html`:
  ```javascript
  const DAILY_LIMIT_MANDIRI = 50;
  const DAILY_LIMIT_KOLEKTIF = 10;
  ```
- Logika pengambilan antrian saat ini disetel untuk **"Ambil hari ini untuk verifikasi besok"**. Pendaftaran otomatis terbuka sesuai logika waktu di fungsi `isQueueOpen()` dan `getTargetDay()`.

## 🔑 Akses Administrator

- Klik teks **ADMIN** di pojok kiri atas halaman utama.
- Masukkan password default: `@Vieqy126892`.
- Di dalam dashboard, Anda dapat melihat tabel pendaftar yang update setiap 10 detik dan mengunduh laporan CSV.

## 📝 Struktur Data Spreadsheet

Sistem akan otomatis membuat header berikut jika sheet masih kosong:
| ID Unik | Waktu Daftar | Tanggal Antrian | Nomor Antrian | Status | NISN | Nama Siswa | Asal Sekolah | Nama Ortu | No WA |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |

## 🛡️ Lisensi

Proyek ini dibuat untuk kepentingan internal SMP Negeri 3 Pemalang. Penggunaan dan modifikasi kode diperbolehkan dengan tetap mencantumkan atribusi desain.

---
Designed by rizqy p3
```

### Penjelasan Bagian README:
1.  **Fitur Utama**: Menjelaskan nilai jual aplikasi seperti *Anti-Bentrok* dan *Dashboard Real-time*.
2.  **Panduan Instalasi**: Ini bagian paling penting di GitHub agar orang lain tahu cara menghubungkan file HTML dengan Google Sheets.
3.  **Akses Administrator**: Memberikan instruksi cara masuk ke panel admin (termasuk password yang Anda gunakan).
4.  **Struktur Data**: Memberikan gambaran bagaimana data akan tertata di Google Sheets.

README ini akan tampil sangat rapi di halaman utama repositori GitHub Anda. Apakah ada bagian lain (seperti fitur tambahan atau aturan pendaftaran) yang ingin Anda masukkan ke dalam deskripsi tersebut?

<!--
[PROMPT_SUGGESTION]Bagaimana cara membuat file .gitignore agar file sampah tidak ikut terupload ke GitHub?[/PROMPT_SUGGESTION]
[PROMPT_SUGGESTION]Tambahkan instruksi cara melakukan update (deploy ulang) Apps Script di README tersebut.[/PROMPT_SUGGESTION]
