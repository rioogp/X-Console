# Skrip Otomatisasi Twitter/X (Unfollow & Hapus Tweet) via Console

Repository ini berisi skrip JavaScript yang dirancang untuk dijalankan di console browser guna mengotomatisasi beberapa tindakan di Twitter/X:

1.  **Auto Unfollow:** Meng-unfollow akun secara massal dari halaman "Following" Anda.
2.  **Auto Delete Tweets:** Menghapus postingan (tweet) secara massal dari halaman profil Anda.

---

## ⚠️ PERINGATAN SANGAT PENTING ⚠️

*   **PELANGGARAN TOS:** Penggunaan skrip otomatisasi seperti ini **MELANGGAR Persyaratan Layanan (Terms of Service) Twitter/X**.
*   **RISIKO AKUN:** Akun Anda dapat dikenai **pembatasan (rate limiting), pembatasan sementara, atau bahkan PENANGGUHAN PERMANEN** oleh Twitter/X jika terdeteksi menggunakan otomatisasi.
*   **GUNAKAN DENGAN RISIKO ANDA SENDIRI:** Anda bertanggung jawab penuh atas segala konsekuensi yang timbul akibat penggunaan skrip ini.
*   **KHUSUS SKRIP HAPUS TWEET:**
    *   Tindakan penghapusan tweet bersifat **PERMANEN** dan **TIDAK DAPAT DIBATALKAN (UNDO)**.
    *   Risiko terdeteksi dan penangguhan akun **JAUH LEBIH TINGGI** dibandingkan skrip unfollow.
    *   **Sangat disarankan** untuk mengunduh arsip data Twitter Anda terlebih dahulu jika Anda ingin menyimpan salinan tweet Anda sebelum menghapusnya.
*   **PERUBAHAN SITUS:** Twitter/X sering mengubah struktur kode situs web mereka (HTML, CSS, atribut `data-testid`). Skrip ini bergantung pada struktur saat ini dan **dapat berhenti berfungsi kapan saja** tanpa pemberitahuan jika ada perubahan. Anda mungkin perlu memperbarui *selector* di dalam kode skrip secara manual.

---

## Deskripsi Skrip

### 1. Skrip Auto Unfollow

*   **Tujuan:** Mengotomatisasi proses unfollow akun yang Anda ikuti.
*   **Cara Kerja:**
    1.  Mencari tombol "Mengikuti" (`Following`) di halaman `[nama_pengguna]/following`.
    2.  Mengklik tombol "Mengikuti".
    3.  Menunggu dialog konfirmasi muncul.
    4.  Mengklik tombol konfirmasi "Setop Ikuti" (`Unfollow`).
    5.  Memberikan jeda antar proses untuk mengurangi risiko.
*   **Lokasi Penggunaan:** Halaman "Following" Anda (`https://x.com/[nama_pengguna_anda]/following`).
*   **Catatan:** Anda mungkin perlu scroll ke bawah secara manual dan menjalankan ulang skrip jika mengikuti banyak akun, karena skrip hanya memproses tombol yang terlihat/dimuat di layar.

### 2. Skrip Auto Delete Tweets

*   **Tujuan:** Mengotomatisasi proses penghapusan tweet dari profil Anda.
*   **Cara Kerja:**
    1.  Secara otomatis menggulir (scroll) halaman profil ke bawah untuk memuat tweet lama.
    2.  Untuk setiap tweet yang ditemukan:
        *   Mengklik tombol opsi "..." (`More`).
        *   Menunggu menu muncul.
        *   Mengklik opsi "Hapus" (`Delete`) pada menu.
        *   Menunggu dialog konfirmasi muncul.
        *   Mengklik tombol konfirmasi "Hapus" (`Delete`).
    3.  Memberikan jeda antar setiap tindakan dan antar penghapusan tweet untuk mengurangi risiko.
*   **Lokasi Penggunaan:** Halaman profil **ANDA** (`https://x.com/[nama_pengguna_anda]`).
*   **Catatan:** Skrip ini memiliki fitur auto-scroll. Untuk menghentikan proses penghapusan, cukup segarkan (refresh) halaman atau tutup tab browser.

---

## Prasyarat

*   Browser web modern (Google Chrome, Mozilla Firefox, Microsoft Edge, dll.).
*   Sudah login ke akun Twitter/X Anda di browser tersebut.
*   Berada di halaman Twitter/X yang **tepat** sesuai dengan skrip yang ingin dijalankan.

---

## Cara Penggunaan Umum

1.  **Buka Twitter/X:** Login ke akun Anda.
2.  **Navigasi ke Halaman yang Benar:**
    *   Untuk **Unfollow:** Pergi ke `https://x.com/[nama_pengguna_anda]/following`.
    *   Untuk **Delete Tweets:** Pergi ke halaman profil Anda `https://x.com/[nama_pengguna_anda]`.
3.  **Buka Developer Console:**
    *   Tekan tombol `F12` pada keyboard Anda.
    *   Atau, klik kanan di mana saja pada halaman, pilih "Inspect" atau "Inspect Element", lalu klik tab "Console".
4.  **Salin Kode Skrip:** Salin **seluruh** kode JavaScript untuk skrip yang ingin Anda gunakan (baik skrip unfollow atau skrip delete).
5.  **Tempel ke Console:** Tempelkan kode yang telah disalin ke dalam area input di Console.
6.  **Jalankan Skrip:**
    *   Tekan `Enter`. Setelah Tempel Kode ke Console. Skrip akan langsung berjalan.
7.  **Amati Proses:** Perhatikan output yang muncul di Console untuk melihat progres, jumlah item yang diproses, atau pesan error jika ada.
8.  **Scroll & Ulangi (Jika Perlu):**
    *   **Unfollow:** Jika Anda mengikuti banyak akun, scroll ke bawah halaman secara manual untuk memuat lebih banyak akun, lalu jalankan ulang skrip (ulangi langkah 5 & 6a).
    *   **Delete Tweets:** Skrip ini sudah memiliki auto-scroll. Biarkan berjalan hingga selesai atau hentikan secara manual (lihat langkah berikutnya).
9.  **Menghentikan Skrip (Khusus Delete):** Cara termudah dan teraman untuk menghentikan skrip penghapusan tweet adalah dengan **menyegarkan (refresh) halaman (F5)** atau **menutup tab browser**.

---

## Konfigurasi (Opsional)

Di bagian awal setiap skrip, terdapat beberapa variabel konfigurasi yang bisa Anda ubah:

*   `delay...`: Variabel seperti `delayBetweenUnfollows`, `delayBetweenTweets`, `delayAfterScroll`, dll., mengatur waktu jeda (dalam milidetik) antar tindakan.
    *   **Penting:** Jangan mengatur nilai delay terlalu rendah (misalnya di bawah 1500ms atau 1.5 detik untuk jeda antar item utama) karena dapat meningkatkan risiko akun Anda ditandai. Nilai yang lebih tinggi lebih aman tetapi memperlambat proses.
*   `deleteMenuText`, `confirmButtonText` (Hanya di skrip Delete): Jika antarmuka Twitter/X Anda menggunakan bahasa selain Inggris, Anda mungkin perlu menyesuaikan nilai teks ini ("Delete") agar sesuai dengan teks tombol/menu di bahasa Anda.

---

## Troubleshooting

*   **Skrip Tidak Bekerja / Tidak Menemukan Tombol:** Kemungkinan besar Twitter/X telah mengubah kode HTML/CSS atau `data-testid` mereka. Anda perlu menggunakan fitur "Inspect Element" di browser untuk menemukan selector (misalnya `data-testid`, class, atau struktur HTML) yang baru untuk tombol/menu yang relevan, lalu perbarui variabel selector di bagian awal skrip.
*   **Error Rate Limit / Tindakan Gagal Sporadis:** Coba tingkatkan nilai variabel `delay...` (terutama `delayBetweenUnfollows` atau `delayBetweenTweets`) menjadi lebih tinggi (misalnya, 5000ms atau lebih).
*   **Skrip Berhenti Tiba-tiba:** Periksa Console untuk pesan error. Mungkin ada perubahan tak terduga di halaman atau masalah jaringan.

---

## Disclaimer

Skrip ini disediakan "sebagaimana adanya" untuk tujuan edukasi dan penggunaan pribadi. Pengguna bertanggung jawab penuh atas penggunaan skrip ini dan segala risiko yang menyertainya, termasuk namun tidak terbatas pada, pembatasan atau penangguhan akun oleh Twitter/X. Tidak ada jaminan bahwa skrip ini akan selalu berfungsi atau aman digunakan.
