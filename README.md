![lisensi](https://img.shields.io/badge/lisensi-MIT-blue)
![kontributor](https://img.shields.io/badge/kontributor-terbuka-informational)
![isu](https://img.shields.io/badge/isu-diterima-brightgreen)


[![buka di editor daring](https://img.shields.io/badge/buka-di%20editor-007acc)](#)

# cascade-plat 🚗:
![contoh masukan](https://cdn.example.dev/shots/cascade-input.jpg)


Mencari pelat nomor kendaraan memakai pengklasifikasi bertingkat berbasis fitur sederhana adalah pendekatan lama yang masih berguna untuk perangkat terbatas. Cara kerjanya: sebuah berkas model yang sudah dilatih menyimpan pola-pola khas pelat, lalu dipakai sebagai cetakan untuk mencocokkan wilayah gambar.

Alurnya dimulai dengan mengubah gambar ke skala abu-abu, karena warna tidak membantu di tahap ini. Pengklasifikasi kemudian menyapu seluruh gambar mencari susunan pola yang mirip pelat. Setiap wilayah yang cocok ditandai kotak, menandakan kemungkinan lokasi pelat.

Pendekatan ini disukai karena ringan dan bisa berjalan waktu nyata di perangkat biasa, serta jauh lebih sederhana dibanding metode modern. Kekurangannya jelas: akurasinya goyah saat pencahayaan berubah, sudut pengambilan miring, atau format pelat antarnegara berbeda. Kotak palsu juga sering muncul pada bentuk yang sekilas mirip pelat.

Untuk kebutuhan sederhana, metode ini titik awal yang wajar. Tapi kalau butuh ketahanan lebih tinggi, model pembelajaran mendalam seperti keluarga YOLO memberi hasil yang jauh lebih baik.


## Alur kerja ⚔️:

### Persiapan:

* `Siapkan pustaka:` pasang OpenCV dan NumPy. Keduanya menyediakan fungsi pengolahan gambar yang dibutuhkan.
* `Ambil berkas model:` unduh berkas model pelat yang sudah dilatih (umumnya berformat xml) dari sumber terpercaya.

### Pengolahan gambar:

* `Muat gambar:` baca berkas foto memakai fungsi baca bawaan OpenCV.
* `Ubah ke abu-abu:` warna tidak penting untuk pencarian pelat, jadi konversi ke satu kanal mempercepat proses sekaligus menyederhanakan analisis.

### Pencarian dengan pengklasifikasi:

* `Buat objek pengklasifikasi:` arahkan ke berkas model yang sudah diunduh.
* `Jalankan pencarian:` panggil fungsi pencarian multi-skala pada gambar abu-abu. Fungsi ini mengembalikan daftar kotak yang dianggap pelat.

### Pengolahan hasil (opsional):

* `Telusuri hasil:` iterasi setiap kotak yang dikembalikan.

Jika sebuah kotak lolos penyaringan ukuran, gambar dipotong pada area itu dan disimpan terpisah untuk dibaca lebih lanjut oleh mesin pengenal karakter.