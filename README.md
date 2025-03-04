# Buku Masjid

Buku Masjid adalah sistem pengelolaan keuangan dan jadwal pengajian masjid berbasis web yang dibuat dengan framework Laravel.

## Tujuan

- Meningkatkan transparansi laporan keuangan masjid/mushalla.
- Memungkinkan akses online bagi jamaah dan masyarakat umum untuk melihat laporan kas.
- Mempermudah bendahara masjid/mushalla dalam mencatat transaksi keuangan.
- Otomatisasi pembuatan laporan kas setiap kali ada transaksi.
- Mempermudah pengurus masjid/mushalla dalam mengelola jadwal khatib dan pengajian.

## Manfaat

- Meningkatkan kepercayaan jamaah/masyarakat terhadap pengelolaan dana infaq masjid/mushalla.
- Memudahkan masyarakat dalam memutuskan untuk berinfaq ke masjid tertentu.
- Mengurangi beban tugas bendahara dalam pembuatan laporan kas masjid/mushalla.
- Memungkinkan masyarakat/jamaah untuk memantau jadwal pengajian secara online.

## Fitur

1. Pengelolaan buku catatan: Setiap kegiatan dapat dicatat di buku catatan kas yang terpisah.
2. Pengelolaan kategori/kelompok pemasukan dan pengeluaran untuk setiap buku catatan.
3. Input pemasukan dan pengeluaran.
4. Laporan:
   - Laporan kas Bulanan
   - Laporan kas per Kategori
   - Laporan kas Mingguan
5. Pengelolaan jadwal khatib Jumat.
6. Pengelolaan jadwal pengajian rutin.

## Cara Install

Aplikasi ini dapat diinstal pada server lokal maupun online dengan spesifikasi berikut:

### Kebutuhan Server

1. PHP 8.1 (dan sesuai dengan [persyaratan server Laravel 10.x](https://laravel.com/docs/10.x/deployment#server-requirements)).
2. Database MySQL atau MariaDB.
3. SQLite (digunakan untuk pengujian otomatis).

### Langkah Instalasi

1. Clone repositori ini
2. Masuk ke direktori buku-masjid: `$ cd buku-masjid`
3. Instal dependensi menggunakan: `$ composer install`
4. Salin berkas `.env.example` ke `.env`: `$ cp .env.example .env`
5. Generate kunci aplikasi: `$ php artisan key:generate`
6. Buat database MySQL untuk aplikasi ini.
7. Konfigurasi database dan pengaturan lainnya di berkas `.env`.
    ```
    APP_URL=http://localhost
    APP_TIMEZONE="Asia/Jakarta"

    DB_DATABASE=homestead
    DB_USERNAME=homestead
    DB_PASSWORD=secret

    MASJID_NAME="Masjid Al-Huda"
    MASJID_DEFAULT_BOOK_ID=1
    AUTH_DEFAULT_PASSWORD=password

    MONEY_CURRENCY_CODE="Rp"
    MONEY_PRECISION=2
    MONEY_DECIMAL_SEPARATOR=","
    MONEY_THOUSANDS_SEPARATOR="."
    ```
8. Jalankan migrasi database: `$ php artisan migrate --seed`
9. Buat kunci passport: `$ php artisan passport:keys`
10. Buat tautan penyimpanan: `$ php artisan storage:link`
11. Mulai server: `$ php artisan serve`
12. Buka web browser dengan alamat web: http://localhost:8000, kemudian masuk dengan akun bawaan:
    ```
    email: admin@example.net
    password: password
    ```

### Data Demo

Ketika sudah ter-install di localhost, kita bisa generate data dummy untuk simulasi sistem buku masjid. Datad demo dapat di-generate dengan perintah berikut:

Generate demo data (3 bulan terakhir):

```bash
$ php artisan buku-masjid:generate-demo-data
```

Hapus semua demo data (yang `created_at` nya `NULL`)

```bash
$ php artisan buku-masjid:remove-demo-data
```


## Screenshot

#### Laporan Bulanan

![Laporan Bulanan](public/screenshots/Screenshot_63.jpg)


#### Jadwal Pengajian

![Jadwal Pengajian](public/screenshots/Screenshot_63.jpg)


## Lisensi

Proyek Buku Masjid merupakan perangkat lunak open-source yang dilisensikan di bawah [Lisensi MIT](LICENSE).
