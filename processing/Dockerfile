FROM python:3

WORKDIR /mnt/code

RUN adduser --system gazette \
  && apt-get update \
  && apt-get -y install poppler-utils postgresql-client

COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
USER gazette
CMD ["celery", "-A", "tasks", "worker", "-B", "--loglevel=INFO"]
