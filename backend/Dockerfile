FROM python:3.10-slim
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
WORKDIR /app
COPY dependencies.txt .
RUN pip install --no-cache-dir -r dependencies.txt
RUN pip install gunicorn
COPY . .
EXPOSE 8000
RUN python manage.py migrate
RUN gunicorn --version
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi:application"]

