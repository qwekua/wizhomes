# WizHomes Deployment Guide

## Option 1: Deploy to Vercel (Recommended - Easiest)

Vercel is the easiest way to deploy this React application.

### Steps:

1. **Install Vercel CLI** (if not already installed):
   ```bash
   npm install -g vercel
   ```

2. **Navigate to the project directory**:
   ```bash
   cd wizhomes-core/wiz-homes
   ```

3. **Deploy**:
   ```bash
   vercel
   ```
   
   Follow the prompts:
   - Set up and deploy: Yes
   - Which scope: Select your account
   - Link to existing project: No
   - Project name: wizhomes (or your choice)
   - Directory: `./` (current directory)
   - Override settings: No

4. **Your site will be live!**
   - Vercel will provide a URL like: `https://wizhomes-xxx.vercel.app`
   - You can also set up a custom domain in Vercel dashboard

### For Production Deployment:
```bash
vercel --prod
```

---

## Option 2: Deploy to GitHub Pages

### Prerequisites:
- GitHub repository must be public or you need GitHub Pro for private repos

### Steps:

1. **Enable GitHub Pages in Repository Settings**:
   - Go to: https://github.com/qwekua/wizhomes/settings/pages
   - Under "Source", select "Deploy from a branch"
   - Under "Branch", select "gh-pages" and "/ (root)"
   - Click "Save"

2. **The GitHub Action will automatically deploy** when you push to main branch

3. **Your site will be live at**: https://qwekua.github.io/wizhomes/

---

## Option 3: Deploy to Netlify

1. **Install Netlify CLI**:
   ```bash
   npm install -g netlify-cli
   ```

2. **Navigate to project**:
   ```bash
   cd wizhomes-core/wiz-homes
   ```

3. **Build the project**:
   ```bash
   npm run build
   ```

4. **Deploy**:
   ```bash
   netlify deploy --prod --dir=dist
   ```

---

## Environment Variables

If you need to set environment variables (like API keys), add them in your deployment platform:

### Vercel:
- Go to Project Settings → Environment Variables
- Add your variables

### Netlify:
- Go to Site Settings → Build & Deploy → Environment
- Add your variables

### GitHub Pages:
- Add secrets in Repository Settings → Secrets and variables → Actions

---

## Current Configuration

- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Node Version**: 18.x or higher
- **Package Manager**: npm

---

## Troubleshooting

### Build Fails:
- Make sure all dependencies are installed: `npm install`
- Check Node version: `node --version` (should be 18+)
- Clear cache: `rm -rf node_modules package-lock.json && npm install`

### 404 Errors:
- For GitHub Pages: Make sure gh-pages branch exists and Pages is enabled
- For Vercel/Netlify: Check that routing is configured correctly (already done in vercel.json)

### CORS Errors:
- The app has localStorage fallback for backend API
- Contact form messages will be stored locally if backend is unavailable
