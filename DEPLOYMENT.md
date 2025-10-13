# PALMS Chatbot Deployment Guide

## Quick Deploy to Render

### Option 1: Connect GitHub Repository (Recommended)
1. Go to [Render.com](https://render.com)
2. Click "New +" → "Web Service"
3. Connect your GitHub account
4. Select the repository: `parth17sharma2005-ops/onpalms-5`
5. Configure:
   - **Name**: `palms-chatbot` (or your preferred name)
   - **Environment**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python app.py`
6. Add Environment Variables:
   - `OPENAI_API_KEY`: Your OpenAI API key
   - `ALLOW_RESET`: `TRUE`
   - `FLASK_DEBUG`: `False`
7. Click "Create Web Service"

### Option 2: Using render.yaml (Auto-deployment)
1. Push the `render.yaml` file to your repository
2. On Render, go to Dashboard → "New +" → "Blueprint"
3. Connect to your GitHub repository
4. Render will automatically detect the `render.yaml` configuration
5. Add your `OPENAI_API_KEY` in the environment variables

## Environment Variables Required
- `OPENAI_API_KEY`: Your OpenAI API key (get from https://platform.openai.com)
- `ALLOW_RESET`: Set to `TRUE` (allows ChromaDB to reset if needed)
- `FLASK_DEBUG`: Set to `False` for production

## After Deployment
1. Your app will be available at: `https://your-app-name.onrender.com`
2. Update `footer.php` with the new URL:
   ```javascript
   const API_URL = 'https://your-app-name.onrender.com';
   ```

## Testing the Deployment
1. Visit `https://your-app-name.onrender.com` (should show the chat interface)
2. Test the chat functionality
3. Test the demo form submission

## Troubleshooting
- If ChromaDB fails to initialize, check that `ALLOW_RESET=TRUE` is set
- If OpenAI fails, verify your `OPENAI_API_KEY` is correct and has credits
- Check Render logs for any deployment errors

## Files Modified for Deployment
- `app.py`: Updated to use environment PORT variable
- `Procfile`: Added for deployment process
- `render.yaml`: Added for easy Render deployment
- This deployment guide created
