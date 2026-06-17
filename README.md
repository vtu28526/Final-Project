# Disease Outbreak Risk Predictor

A Flask web app that uses the provided county-level health dataset to estimate disease outbreak risk, with prediction, history, dataset browsing, and project information pages.

## Run

```powershell
pip install -r requirements.txt
python app.py
```

## Render Deployment

Keep `app.py`, `requirements.txt`, `runtime.txt`, `.python-version`, `Procfile`, and `render.yaml` in the repository root.

Render settings:

```bash
Root Directory: leave blank
Build Command: python -m pip install --upgrade pip && python -m pip install -r requirements.txt
Start Command: gunicorn app:app --bind 0.0.0.0:$PORT
```

Open the Disease Outbreak Risk Predictor web link:

https://brokers-aged-succeed-jeff.trycloudflare.com/

## Google Sign-In

1. Create OAuth credentials in Google Cloud Console:
   - Application type: Web application
   - Authorized redirect URI for local development: `http://127.0.0.1:5001/auth/google/callback`
   - If using the Cloudflare URL, also add: `https://brokers-aged-succeed-jeff.trycloudflare.com/auth/google/callback`
2. Copy `.env.example` to `.env`.
3. Fill in `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, and `SECRET_KEY`.
4. If you are using the Cloudflare URL, set `GOOGLE_REDIRECT_URI=https://brokers-aged-succeed-jeff.trycloudflare.com/auth/google/callback`.
5. Restart the Flask server. The Sign In and Sign Up pages will show the Google button when credentials are configured.

## Pages

- Home: project summary and dataset coverage.
- Predict: choose disease category and county, then generate an explainable risk score.
- History: view saved predictions.
- Dataset: browse counties from the CSV.
- About: scoring method and dataset notes.
