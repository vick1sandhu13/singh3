# singh3
SuperKart Sales Forecasting model deployment files

## Running the services

Start the backend from the `backend` directory:

```bash
cd backend
gunicorn -w 4 -b 0.0.0.0:7860 app:superkart_api
```

Start the frontend from the `frontend` directory:

```bash
cd frontend
streamlit run app.py --server.port=8501 --server.address=0.0.0.0 --server.enableXsrfProtection=false
```

The backend listens on port `7860`; the frontend listens on port `8501` and sends prediction requests to `http://backend:7860`.

### Running process information

Check whether the services are running and view their process IDs:

```bash
ps -ef | grep -E '[g]unicorn|[s]treamlit'
lsof -nP -iTCP:7860 -sTCP:LISTEN
lsof -nP -iTCP:8501 -sTCP:LISTEN
```

For Docker deployments, list the service containers and published ports with:

```bash
docker ps
```
