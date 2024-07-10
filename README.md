# 215610063-Oktarisa-Vinarsih-Responsi

# Membuat Website Sederhana

## 1. Persiapan

#### a. Membuat dua direktori: website-utama dan website-profil:

```bash
mkdir website-utama
cd website-utama
mkdir website-profil
cd website-profil
```

#### b. Didalam website-utama:

Buat file index.html (sesuai deskripsi halaman utama).

```bash
  nano index.html
```
lalu masukkan script pada file index-utama.html untuk website-utama

Pastikan link "profil" mengarah ke /profil

```bash
  <a href="https://8f61cc0b-b562-474a-9d64-4ca775a6c7aa-10-244-7-242-8081.papa.r.killercoda.com/">Profil</a>
```

#### c.	Di dalam website-profil, letakkan file gambar profil Anda (foto.jpg)

```bash
  cd website-profil
  nano index.html
```
lalu masukkan script pada file index-profile.html untuk website-profil

lanjut mengupload foto.jpg

```bash
  wget -O ~/website-profil/foto.jpg  "https://drive.google.com/uc?export=download&id=146d3v2nlXNVrV2xj17KTrE4xy7i0eiKx" 
```

## 2. Docker Network (Modul 13)

Buat jaringan Docker dengan nama my-nama-mahasiswa-network

```bash
  docker network ceate my-oktarisa-network
```

## 3. Dockerfile dan Image (Modul 11 & 12)

Dockerfile untuk Website Utama (direktori website-utama)

```bash
FROM nginx:latest
COPY . /usr/share/nginx/html
EXPOSE 80
```
Dockerfile untuk Website Profile (direktori website-profile)

```bash
FROM nginx:latest
COPY . /usr/share/nginx/html
EXPOSE 80
```

## 4. Build Image

### Bangun dua image Docker dari Dockerfile yang sudah dibuat. Berikan nama yang jelas untuk setiap image (misalnya, website-utama, website-profil).

website-utama

```bash
docker build -t website-utama .
```

website-profil

```bash
docker build -t website-profil .
```

## 5. Docker Volume (Modul 14) (Opsional)

Buat volume bernama profile-images

```bash
docker volume create profile-images
```

## 6. Menjalankan container website-utama dan website-profil

website-utama

```bash
docker run -d –name website-utama –network my-oktarisa-network -p 8080:80 website-utama
```

website-profil

```bash
docker run -d –name website-profil –network my-oktarisa-network -p 8081:80 website-utama
```

## 7. Mengakses website

1. Membuka traffic port accessor pada killercoda ubuntu.
2. Akses halaman utama di: http://localhost:8080. maka akan menampilkan website data diri.
3. Klik halaman profil untuk bernavigasi “ke Halaman Profil”.
4. Akan tampak halaman profil.
