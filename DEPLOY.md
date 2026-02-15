# 🚀 QuickDeploy — Panduan Deployment ke Vercel

## Prasyarat

1. **Akun Vercel** — [vercel.com/signup](https://vercel.com/signup)
2. **Akun Netlify** — [app.netlify.com/signup](https://app.netlify.com/signup)
3. **Node.js** v18+ — [nodejs.org](https://nodejs.org)
4. **Vercel CLI** (opsional, untuk lokal) — `npm i -g vercel`

---

## Langkah 1: Dapatkan Netlify Personal Access Token

1. Buka [app.netlify.com/user/applications#personal-access-tokens](https://app.netlify.com/user/applications#personal-access-tokens)
2. Klik **"New access token"**
3. Beri nama (contoh: "QuickDeploy") lalu klik **"Generate token"**
4. **Salin token** dan simpan di tempat aman. Token ini hanya muncul sekali!

---

## Langkah 2: Deploy ke Vercel

### Opsi A: Via Vercel Dashboard (Disarankan)

1. Push kode ini ke repository GitHub/GitLab
2. Buka [vercel.com/new](https://vercel.com/new)
3. Import repository Anda
4. Di bagian **Environment Variables**, tambahkan:
   - **Name**: `NETLIFY_TOKEN`
   - **Value**: *(paste token dari Langkah 1)*
5. Klik **Deploy**

### Opsi B: Via Vercel CLI

```bash
# Install Vercel CLI
npm i -g vercel

# Login
vercel login

# Deploy (dari folder project ini)
vercel

# Set environment variable
vercel env add NETLIFY_TOKEN
# Paste token saat diminta

# Deploy ulang agar env var aktif
vercel --prod
```

---

## Langkah 3: Testing Lokal (Opsional)

```bash
# Install dependencies
npm install

# Buat file .env di root project
echo NETLIFY_TOKEN=your_token_here > .env

# Jalankan dev server
npx vercel dev
```

Buka `http://localhost:3000` di browser.

---

## Struktur Folder

```
WEB QUICK DEPLOY/
├── index.html        ← Frontend (UI & Logic)
├── api/
│   └── deploy.js     ← Backend (Serverless Function)
├── vercel.json       ← Konfigurasi routing Vercel
├── package.json      ← Dependencies
└── DEPLOY.md         ← File ini
```

---

## Catatan Penting

> ⚠️ **Jangan pernah** commit token Netlify ke repository.
> Selalu gunakan Environment Variables di Vercel Dashboard.

> 💡 Setiap upload (folder atau file) akan membuat **site baru** di akun Netlify Anda.
> Pantau penggunaan di [app.netlify.com/teams](https://app.netlify.com/teams).

