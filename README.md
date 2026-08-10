# Priyal & Tony — Wedding Website

**Modern Heritage** — A Gujarati & Black American wedding celebration  
**Date:** Saturday, April 17, 2027  
**Location:** Richmond, Virginia

---

## 🚀 Free Hosting Options

### Option 1: GitHub Pages (Recommended — 100% Free)
1. Create a GitHub account (if you don't have one): https://github.com
2. Create a new repository (e.g., `wedding`)
3. Upload all files from this folder to the repository
4. Go to **Settings → Pages → Source** → select `main` branch
5. Your site is live at: `https://yourusername.github.io/wedding/`

### Option 2: Netlify (Free — drag & drop)
1. Go to https://app.netlify.com/drop
2. Drag this entire folder onto the page
3. Done! You'll get a URL like `https://random-name.netlify.app`
4. You can customize the subdomain in settings

### Option 3: Vercel (Free)
1. Go to https://vercel.com
2. Sign up and import your GitHub repo (or drag & drop)
3. Auto-deploys on every change

---

## 📝 How to Edit

This is a single HTML file — open `index.html` in any text editor (VS Code, Notepad++, etc.) to make changes.

### Common Edits:

| What to change | Where to find it |
|---|---|
| Names | Search for "Priyal" and "Tony" |
| Date | Search for "April 17, 2027" |
| Location | Search for "Richmond" |
| Colors | `:root` CSS variables at the top |
| RSVP deadline | Search for "March 1, 2027" |
| Add photo | See comment in the `hero-photo` div |
| Events list | Search for "Mehndi & Sangeet" etc. |
| Meal options | Search for `<select id="meal">` |

### Adding Your Photo:
1. Place your photo file (e.g., `couple.jpg`) in the same folder as `index.html`
2. In `index.html`, find the `hero-photo` section
3. Uncomment the `<img>` tag and update the filename
4. Delete the placeholder `<div>`

---

## 📊 RSVP Data Collection (FREE)

### Option A: Google Sheets (Recommended — Free & Easy)

This stores all RSVPs in a Google Sheet you own.

**Setup Steps:**

1. Create a new Google Sheet
2. Add these column headers in row 1:
   ```
   Timestamp | Full Name | Email | Attending | Guest Count | Plus One | Plus One Name | Plus One Relation | Meal | Dietary | Events | Message
   ```
3. Go to **Extensions → Apps Script**
4. Delete the default code and paste this:

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  
  sheet.appendRow([
    data.timestamp,
    data.fullName,
    data.email,
    data.attending,
    data.guestCount,
    data.hasPlusOne ? 'Yes' : 'No',
    data.plusOneName,
    data.plusOneRelation,
    data.meal,
    data.dietary,
    data.events.join(', '),
    data.message
  ]);
  
  return ContentService.createTextOutput(JSON.stringify({status: 'success'}))
    .setMimeType(ContentService.MimeType.JSON);
}
```

5. Click **Deploy → New Deployment**
6. Choose **Web app**
7. Set "Who has access" to **Anyone**
8. Click **Deploy** and copy the URL
9. In `index.html`, find the Google Sheets integration section and:
   - Uncomment the `fetch()` block
   - Replace `YOUR_GOOGLE_APPS_SCRIPT_URL` with your URL
   - Comment out the localStorage section

### Option B: Formspree (Free up to 50/month)

1. Go to https://formspree.io and create an account
2. Create a new form — you'll get a form ID
3. In `index.html`, replace the fetch URL with:
   ```
   https://formspree.io/f/YOUR_FORM_ID
   ```

---

## 🎨 Design Customization

### Changing Colors
Edit the CSS variables in `:root`:
```css
:root {
    --ivory: #FFFDF7;        /* Background */
    --burgundy: #6B1D3A;     /* Primary accent */
    --terracotta: #C76F3B;   /* Warm accent */
    --saffron: #D4943A;      /* Gold-ish accent */
    --espresso: #2C1810;     /* Text color */
    --gold: #B8923E;         /* Decorative accents */
}
```

### Changing Fonts
The site uses:
- **Cormorant Garamond** — elegant display headings
- **Montserrat** — clean body text

To change, update the Google Fonts `<link>` in `<head>` and the `--font-display` / `--font-body` variables.

---

## 🔮 Future Sections (Coming Soon)

This site is designed to grow. Future additions:
- [ ] Our Story (timeline of your relationship)
- [ ] Travel & Accommodations (hotel blocks, directions)
- [ ] Wedding Weekend Schedule (multi-day events)
- [ ] Registry
- [ ] Gallery
- [ ] FAQ
- [ ] Bridal Party

---

## 📁 File Structure

```
wedding-website/
├── index.html          ← The complete website (edit this!)
├── README.md           ← This file
└── (your photos)       ← Add your images here
```

---

*Built with love for Priyal & Tony* 🇮🇳 × 🖤 × ✨
