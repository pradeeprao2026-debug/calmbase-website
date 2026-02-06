# Calmbase Marketing Website

Static marketing site for [getcalmbase.com](https://getcalmbase.com).

## Project Structure

```
Calmbase/
├── index.html      # Main website
├── netlify.toml    # Netlify configuration
├── favicon.svg     # SVG favicon
└── README.md       # This file
```

## Local Development

Open `index.html` in your browser, or use a local server:

```bash
# Python 3
python -m http.server 8000

# Node.js (npx)
npx serve .

# Then visit http://localhost:8000
```

---

## Deployment Guide

### Step 1: Initialize Git Repository

```bash
cd /path/to/Calmbase

# Initialize git
git init

# Add all files
git add index.html netlify.toml favicon.svg README.md

# Create initial commit
git commit -m "Initial commit: Calmbase marketing website"
```

### Step 2: Push to GitHub

```bash
# Create a new repository on GitHub named "calmbase-website"
# Then connect and push:

git remote add origin https://github.com/YOUR_USERNAME/calmbase-website.git
git branch -M main
git push -u origin main
```

### Step 3: Connect to Netlify

1. Go to [app.netlify.com](https://app.netlify.com)
2. Click **"Add new site"** → **"Import an existing project"**
3. Select **GitHub** and authorize Netlify
4. Choose the `calmbase-website` repository
5. Build settings will auto-detect from `netlify.toml`:
   - Build command: (empty or as configured)
   - Publish directory: `.`
6. Click **"Deploy site"**

Netlify will assign a random URL like `random-name-123.netlify.app`.

### Step 4: Configure Custom Domain

#### In Netlify:

1. Go to **Site settings** → **Domain management**
2. Click **"Add custom domain"**
3. Enter: `getcalmbase.com`
4. Netlify will prompt you to configure DNS

#### In Namecheap:

1. Log into [Namecheap](https://namecheap.com)
2. Go to **Domain List** → click **Manage** next to `getcalmbase.com`
3. Go to **Advanced DNS** tab
4. Delete existing records, then add:

| Type  | Host | Value                        | TTL       |
|-------|------|------------------------------|-----------|
| A     | @    | 75.2.60.5                    | Automatic |
| CNAME | www  | YOUR-SITE.netlify.app        | Automatic |

> **Note:** The A record IP (`75.2.60.5`) is Netlify's load balancer. Replace `YOUR-SITE.netlify.app` with your actual Netlify subdomain.

**Alternative: Use Netlify DNS (Recommended)**

For faster SSL and better reliability:

1. In Netlify, go to **Domain settings** → **Netlify DNS**
2. Click **"Set up Netlify DNS"** for `getcalmbase.com`
3. Netlify will provide nameservers like:
   - `dns1.p01.nsone.net`
   - `dns2.p01.nsone.net`
   - `dns3.p01.nsone.net`
   - `dns4.p01.nsone.net`
4. In Namecheap, go to **Domain** → **Nameservers**
5. Select **"Custom DNS"** and enter the Netlify nameservers
6. Save changes (propagation takes 24-48 hours)

### Step 5: Enable SSL Certificate

1. In Netlify, go to **Site settings** → **Domain management** → **HTTPS**
2. Click **"Verify DNS configuration"**
3. Once verified, click **"Provision certificate"**
4. Enable **"Force HTTPS"** to redirect all HTTP traffic

SSL provisioning is automatic with Let's Encrypt and typically completes within minutes.

### Step 6: Verify Deployment

Test your site:

- [ ] Visit `https://getcalmbase.com` - should load the site
- [ ] Visit `https://www.getcalmbase.com` - should redirect to non-www
- [ ] Visit `http://getcalmbase.com` - should redirect to HTTPS
- [ ] Check mobile responsiveness
- [ ] Verify all navigation links work
- [ ] Test the "Get Early Access" button

### Troubleshooting

**DNS not propagating?**
- Use [dnschecker.org](https://dnschecker.org) to verify DNS records
- Wait up to 48 hours for full propagation

**SSL certificate not provisioning?**
- Ensure DNS is correctly pointed to Netlify
- Try clicking "Renew certificate" in Netlify settings

**www redirect not working?**
- Verify the CNAME record for `www` is set correctly
- Check that `netlify.toml` redirects are deployed

---

## Updating the Site

Make changes to `index.html`, then:

```bash
git add .
git commit -m "Update: description of changes"
git push
```

Netlify will automatically rebuild and deploy.

---

## Assets to Add

Before launch, add these files:

- [ ] `og-image.png` - Social sharing image (1200x630px recommended)
- [ ] `favicon-32x32.png` - 32px favicon
- [ ] `favicon-16x16.png` - 16px favicon
- [ ] `apple-touch-icon.png` - 180px iOS icon

---

## Contact

Questions? Email [hello@getcalmbase.com](mailto:hello@getcalmbase.com)
