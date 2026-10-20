# Advanced Engineering Mathematics & Computational Methods Lab

Laboratorium belajar interaktif untuk mahasiswa teknik (terutama aerospace). Ubah parameter, jalankan metode numerik, lihat grafiknya, lalu pahami artinya secara teknik. Semua angka dihitung oleh fungsi JavaScript sungguhan, tanpa hasil acak atau palsu.

**Demo online:** `https://USERNAME.github.io/NAMA-REPO/`
(ganti `USERNAME` dan `NAMA-REPO` setelah kamu publish, lihat bagian [Cara Publish](#cara-publish-ke-github-pages))

---

## Fitur

| Bagian | Isi |
|---|---|
| **Dashboard** | Statistik, roadmap belajar 9 tahap, catatan, bookmark, ekspor/impor progres (JSON) |
| **Lab Interaktif** | 14 simulasi: ODE orde-1 (Euler, Heun, RK4), getaran teredam, integrasi & diferensiasi numerik, eliminasi Gauss, gradient descent, Fourier/DFT, regresi least-squares, transformasi Laplace, BVP beda hingga, medan vektor 2D, FEM batang 1D, integral garis, integral permukaan 3D, rangka batang 2D |
| **Playground** | Perbandingan 4 metode pencarian akar (Bisection, False Position, Newton-Raphson, Secant), tabel iterasi, waktu eksekusi, grafik konvergensi, ekspor CSV |
| **Studi Kasus** | Simulasi roket sounding 1D (RK4 + drag + massa berkurang) dibandingkan dengan persamaan Tsiolkovsky |
| **Kuis, Glosarium, Resume** | Latihan 8 soal, glosarium istilah dengan bookmark, ringkasan hasil percobaan terakhir |

Semua rumus ditampilkan dengan **MathJax** (gaya buku teks), misalnya metode Runge-Kutta:

```
y(n+1) = y(n) + (1/6)(k1 + 2k2 + 2k3 + k4)
```

tampil sebagai rumus rapi di dashboard, lengkap dengan `k1` sampai `k4`.

## Teknologi

- HTML, CSS, dan JavaScript murni (satu file, tanpa build step, tanpa Node.js)
- [Plotly.js](https://plotly.com/javascript/) untuk grafik
- [MathJax 3](https://www.mathjax.org/) untuk rumus
- Pustaka dimuat lewat CDN (cdnjs), jadi **perlu koneksi internet** saat membuka halaman

## Struktur repo

```
.
├── index.html   # seluruh aplikasi (wajib bernama index.html)
└── README.md    # file ini
```

---

## Cara Publish ke GitHub Pages

### Opsi A: lewat browser (paling mudah, tanpa Git)

1. Login ke [github.com](https://github.com), klik **New repository**.
2. Isi nama repo, misalnya `aem-lab`. Pilih **Public**. Klik **Create repository**.
3. Klik **uploading an existing file**, lalu drag & drop `index.html` dan `README.md`.
4. Klik **Commit changes**.
5. Buka **Settings → Pages**.
6. Pada **Build and deployment**, pilih:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main`, folder `/ (root)`
   - Klik **Save**.
7. Tunggu sekitar 1 sampai 2 menit, lalu buka:
   ```
   https://USERNAME.github.io/aem-lab/
   ```

### Opsi B: lewat Git (command line)

```bash
git init
git add index.html README.md
git commit -m "Rilis awal AEM Lab"
git branch -M main
git remote add origin https://github.com/USERNAME/aem-lab.git
git push -u origin main
```

Setelah itu aktifkan Pages seperti langkah 5 sampai 7 di Opsi A.

### Update setelah online

Edit `index.html` (di GitHub klik ikon pensil, atau `git push` lagi). Pages akan otomatis deploy ulang dalam beberapa menit. Kalau tampilan belum berubah, tekan **Ctrl + F5** untuk refresh tanpa cache.

---

## Menjalankan di komputer sendiri

Klik dua kali `index.html`, atau pakai server lokal:

```bash
python -m http.server 8000
# buka http://localhost:8000
```

Tetap perlu internet saat pertama dibuka untuk memuat Plotly dan MathJax.

## Cara menulis fungsi di kolom input

Gunakan `x^2`, `sin(x)`, `cos(x)`, `exp(x)`, `log(x)` (logaritma natural), `sqrt(x)`, `abs(x)`, `pi`.
Contoh: `x^3 - 2*x - 5`. Perkalian harus ditulis dengan `*`.

## Catatan penting

- **Progres tersimpan di `localStorage` browser** masing-masing pengunjung. Mode private atau menghapus data situs akan menghapusnya. Gunakan tombol **Ekspor JSON** sebagai cadangan.
- Evaluator fungsi memakai JavaScript, jadi hanya masukkan ekspresi yang kamu tulis sendiri.
- Jika grafik tidak muncul, Plotly gagal dimuat (internet mati atau diblokir). Tabel angka tetap berfungsi.
- Jika rumus tampil sebagai teks mentah seperti `\frac{...}`, MathJax belum termuat. Muat ulang halaman setelah online.

## Riwayat versi

| Versi | Perubahan |
|---|---|
| v1.5 | Semua rumus dirender dengan MathJax; rumus Euler, Heun, RK4, trapesium/Simpson, DFT, Laplace, Newton, FEM, dan lain-lain ditambahkan di tiap lab |
| v1.4 | Integral permukaan 3D, rangka batang 2D, studi kasus roket |
| v1.3 | Perbaikan warna, bilangan kondisi matriks, integral garis |
| v1.2 | Laplace, BVP, medan vektor 2D, FEM batang 1D |
| v1.1 | Warna lebih kontras, regresi least-squares |
| v1.0 | Rilis awal |

**Rencana v1.6:** FEM kontinum 2D, studi kasus tambahan (sayap, orbit), Three.js, unduhan file langsung.

## Lisensi

Tambahkan file `LICENSE` sesuai kebutuhan (misalnya MIT) bila ingin repo ini dipakai orang lain.
