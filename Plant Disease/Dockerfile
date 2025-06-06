# Use an official Python runtime as a parent image.
FROM python:3.9-slim

# Prevent Python from writing .pyc files to disc
ENV PYTHONDONTWRITEBYTECODE=1
# Ensure stdout and stderr are flushed immediately
ENV PYTHONUNBUFFERED=1

# Install system dependencies required for OpenCV and related libraries
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory in the container.
WORKDIR /app

# Copy requirements file and install Python dependencies.
COPY requirements.txt /app/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy the rest of the application code.
COPY . /app

# Expose the port the app runs on.
EXPOSE 7860

# Define the command to run your app.
CMD ["python", "app.py"]
