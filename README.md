# Share de Vagões — INPASA

Dashboard de share de vagões INPASA vs Outros nos terminais Teciap e Ultracargo.

## Estrutura

```
deploy/
├── public/
│   └── index.html        ← App completo (single-file)
├── firebase.json         ← Config Firebase Hosting
├── .firebaserc           ← Projeto Firebase
├── vercel.json           ← Config Vercel
├── .github/
│   └── workflows/
│       └── firebase-deploy.yml  ← CI/CD automático
└── .gitignore
```

---

## 1. GitHub

```bash
# Na pasta deploy/, inicialize o repositório e suba:
git init
git add .
git commit -m "feat: share de vagões dashboard v1"
git remote add origin https://github.com/SEU_USUARIO/SEU_REPO.git
git branch -M main
git push -u origin main
```

---

## 2. Firebase Hosting

### Pré-requisito
```bash
npm install -g firebase-tools
firebase login
```

### Deploy manual (uma vez)
```bash
firebase deploy --only hosting
```

A URL será: **https://sharevagoesroo.web.app**

### Deploy automático (GitHub Actions)
1. No Firebase Console → Configurações do projeto → Contas de serviço
2. Gere uma nova chave privada → baixe o JSON
3. No GitHub → Settings → Secrets and variables → Actions
4. Crie o secret: **FIREBASE_SERVICE_ACCOUNT_SHAREVAGOESROO** → cole o conteúdo do JSON
5. A partir daí, todo `git push` na branch `main` faz deploy automático ✅

---

## 3. Vercel

### Via CLI
```bash
npm install -g vercel
vercel --prod
```

### Via GitHub (recomendado)
1. Acesse **vercel.com** → New Project
2. Importe o repositório GitHub
3. **Root Directory:** deixe em branco (ou `/`)
4. **Build Command:** deixe vazio
5. **Output Directory:** `public`
6. Clique em **Deploy** ✅

A URL será gerada automaticamente (ex: `share-vagoes.vercel.app`).

---

## Firebase Project Info
- **Project ID:** sharevagoesroo
- **Hosting URL:** https://sharevagoesroo.web.app
- **App ID:** 1:725490974670:web:f7931f80907be62359f59f
