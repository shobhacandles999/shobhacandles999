# Shobha Candles & Gifting — owner-only product manager

## What this adds
- Public visitors can browse active products; they cannot add/edit/delete products.
- Owner signs into `admin.html` and can add/edit/hide/publish/delete products, photos, descriptions, prices, and optional product video links.
- Photos are stored in Supabase Storage. Product metadata is stored in Supabase Postgres.
- Responsive dashboard for phone, tablet and laptop.

## Setup (required before it works)
1. Create a Supabase project at https://supabase.com/.
2. In Authentication > Users, create an owner user with your email and a strong password. Email must match the SQL policy exactly.
3. Open `supabase-setup.sql`; replace BOTH instances of `owner@example.com` with your owner email, then run the whole file in Supabase SQL Editor.
4. Copy Project URL and anon/public key from Supabase Project Settings > API.
5. Open `index.html`, find `YOUR_SUPABASE_PROJECT_URL` and `YOUR_SUPABASE_ANON_KEY`, and replace both values. Only use the anon/publishable key; NEVER put a service_role/secret key in browser code.
6. Upload `index.html` to your site root (replace the current `index.html` after taking a backup). Upload `admin.html` and `supabase-setup.sql` to the same repository/root (SQL can stay private/not published; best keep it off the public website after setup). If you place `admin.html` in `/admin/`, adjust the public-site link inside it.
7. Open `admin.html` (for GitHub Pages, e.g. `https://YOUR-USERNAME.github.io/YOUR-REPO/admin.html`), enter the same Project URL and anon key, and sign in.
8. Add a test product, verify it appears in the public catalogue, then test hide/edit/delete.

## Important
- This is not deployed or connected to your Supabase project yet because project credentials and owner email were not supplied.
- The owner restriction is enforced by Supabase Row Level Security and Storage policies, not by a hidden admin button. Keep the anon/public key public as designed; never share the owner password or a service_role key.
- Existing hard-coded products remain as fallback until at least one active product exists in the database. Once active database products exist, they replace the public product grid. Other home-page showcase tiles remain part of the original design.
- Product photo maximum is 8 MB. Price is optional. Visitors see active products only; signed-in owner can see and manage all products.
- If your Supabase project has stricter password/confirmation settings, confirm the owner email and use the password you set.
