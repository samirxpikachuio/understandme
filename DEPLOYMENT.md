# Deployment Guide

This project is a static HTML/CSS/JavaScript website that can be deployed to various hosting platforms. Choose the method that best fits your needs.

## Prerequisites

- Git installed and authenticated (for Git-based deployments)
- Your repository pushed to GitHub, GitLab, or Bitbucket (for Git-based hosting)

## Option 1: GitHub Pages (Recommended for Free Hosting)

GitHub Pages is a free hosting solution that works perfectly for static websites.

### Steps:

1. **Push your code to GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/impressingCrush.git
   git push -u origin main
   ```

2. **Configure GitHub Pages**
   - Go to your repository on GitHub
   - Navigate to **Settings** > **Pages**
   - Under **Source**, select **Deploy from a branch**
   - Choose **main** (or **master**) branch
   - Select **/(root)** as the folder
   - Click **Save**

3. **Access your site**
   - Your site will be available at: `https://YOUR_USERNAME.github.io/impressingCrush/`
   - Note: If your repository is named `impressingCrush`, the URL path will include that name
   - For a custom domain, add a `CNAME` file in the root directory with your domain name

### Important Notes:
- **For mobile devices**: Make sure to update `index.html` line 68 to use `mobile.js` instead of `script.js` before deploying if you want mobile touch support
- GitHub Pages typically takes a few minutes to deploy your changes
- HTTPS is automatically enabled

---

## Option 2: Netlify (Recommended for Easy Deployment)

Netlify offers drag-and-drop deployment and continuous deployment from Git.

### Method A: Drag and Drop

1. **Prepare your files**
   - Ensure all files (HTML, CSS, JS, images) are in the project folder
   - If using `mobile.js` for mobile, update `index.html` accordingly

2. **Deploy**
   - Go to [Netlify Drop](https://app.netlify.com/drop)
   - Drag and drop your entire `impressingCrush` folder
   - Your site will be live immediately at a `netlify.app` URL

### Method B: Git-based Deployment

1. **Connect repository**
   - Sign in to [Netlify](https://app.netlify.com)
   - Click **New site from Git**
   - Connect your GitHub/GitLab/Bitbucket account
   - Select your `impressingCrush` repository

2. **Configure build settings**
   - **Build command**: Leave empty (no build needed)
   - **Publish directory**: `/` (root directory)
   - Click **Deploy site**

3. **Access your site**
   - Netlify will provide a random subdomain (e.g., `random-name-123.netlify.app`)
   - You can customize the site name in **Site settings** > **Change site name**
   - Custom domains can be added in **Domain settings**

### Netlify Benefits:
- Automatic HTTPS
- Custom domain support
- Continuous deployment (auto-deploy on every push)
- Free SSL certificates
- CDN distribution

---

## Option 3: Vercel

Vercel is another excellent option for static site deployment.

### Steps:

1. **Install Vercel CLI** (optional, you can also use the web interface)
   ```bash
   npm i -g vercel
   ```

2. **Deploy via CLI**
   ```bash
   cd impressingCrush
   vercel
   ```
   - Follow the prompts to configure your project
   - For framework preset, choose **Other** or **Static Site**

3. **Deploy via Web Interface**
   - Go to [Vercel](https://vercel.com)
   - Click **Add New** > **Project**
   - Import your Git repository
   - Configure:
     - **Framework Preset**: Other
     - **Root Directory**: `./`
   - Click **Deploy**

4. **Access your site**
   - Your site will be available at a `vercel.app` subdomain
   - Custom domains can be added in project settings

---

## Option 4: Traditional Web Hosting (cPanel/FTP)

If you have traditional web hosting (cPanel, FTP access, etc.):

### Steps:

1. **Prepare your files**
   - Ensure all files are ready in your local `impressingCrush` folder
   - If using mobile version, update `index.html` to use `mobile.js`

2. **Upload files**
   - Connect to your hosting via FTP (FileZilla, WinSCP, etc.) or use cPanel File Manager
   - Upload all files to the `public_html` directory (or your web root)
   - Maintain the folder structure (especially the `images/` folder)

3. **Access your site**
   - Visit your domain to see the live site
   - Ensure your hosting supports HTTPS for secure connections

---

## Mobile vs Desktop Script

**Important**: The project includes two JavaScript files:
- `script.js` - For desktop (mouse events)
- `mobile.js` - For mobile/touch devices (touch events)

### To enable mobile support:

Edit `index.html` line 68 and change:
```html
<script src="./script.js"></script>
```

To:
```html
<script src="./mobile.js"></script>
```

**Recommendation**: You can also detect device type and load the appropriate script automatically, or use a service that detects mobile users and serves the correct version.

---

## Pre-Deployment Checklist

- [ ] All image files are present in the `images/` folder
- [ ] CSS file (`style.css`) is properly linked
- [ ] JavaScript file is correctly referenced in `index.html`
- [ ] External fonts from Google Fonts are loading correctly
- [ ] Test the site locally by opening `index.html` in a browser
- [ ] Decide whether to use `script.js` or `mobile.js` (or implement device detection)
- [ ] Ensure all file paths use relative paths (they do by default)

---

## Post-Deployment

After deploying:

1. **Test the site** on different devices and browsers
2. **Check that images load correctly** (verify image paths work on your hosting platform)
3. **Test drag functionality** on both desktop and mobile
4. **Verify HTTPS** is working (if available)
5. **Test on slow connections** to ensure performance is acceptable

---

## Troubleshooting

### Images not loading
- Verify image file paths are correct (should be `images/filename.jpg`)
- Ensure the `images/` folder is uploaded to the same directory level as `index.html`
- Check file names match exactly (case-sensitive on some servers)

### Scripts not working
- Verify JavaScript files are uploaded
- Check browser console for errors
- Ensure file paths in `index.html` are correct
- Clear browser cache and try again

### Styles not applying
- Verify `style.css` is in the same directory as `index.html`
- Check the link path in `index.html` (should be `./style.css`)
- Ensure external Google Fonts can load (check network tab in browser dev tools)

### GitHub Pages 404 error
- Ensure `index.html` is in the root of the repository (or in the branch/folder you selected)
- Wait a few minutes for GitHub Pages to propagate changes
- Check repository settings > Pages for correct branch/folder selection

---

## Custom Domain Setup (Optional)

### GitHub Pages:
1. Create a `CNAME` file in the root directory
2. Add your domain name (e.g., `yourdomain.com`)
3. Configure DNS records as per GitHub Pages documentation

### Netlify/Vercel:
- Add custom domain in site/project settings
- Follow platform-specific DNS configuration instructions

---

## Need Help?

If you encounter issues:
- Check browser console for JavaScript errors
- Verify all file paths are correct
- Ensure all required files are uploaded
- Test locally first before deploying

Happy deploying! ❤️

