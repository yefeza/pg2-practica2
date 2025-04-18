# Uso de Django

Repositorio de ejemplo para el uso de Django en un proyecto de desarrollo web.

## Crear entorno virtual

```bash
python -m venv venv
```

## Activar entorno virtual

```bash
# Windows
.\env\Scripts\activate

# Linux
source env/bin/activate
```

## Instalar dependencias

```bash
pip install -r requirements.txt
```

## Crear proyecto Django

```bash
django-admin startproject practica2
```

## Aplicar migraciones

```bash
python manage.py migrate
```

## Iniciar servidor

```bash
python manage.py runserver
```

## Crear superusuario

```bash
python manage.py createsuperuser
```

## Crear aplicación

```bash
python manage.py startapp libros
```

## Agregar aplicación a settings.py

```python
INSTALLED_APPS = [
    ...
    'libros',
]
```

## Crear modelo

Escribe el modelo en `libros/models.py`:

```python
from django.db import models

class Autor(models.Model):
    nombre = models.CharField(max_length=100)
    fecha_nacimiento = models.DateField()

    def __str__(self):
        return self.nombre

class Libro(models.Model):
    titulo = models.CharField(max_length=100)
    autor = models.ForeignKey(Autor, on_delete=models.CASCADE, related_name="libros")
    fecha_publicacion = models.DateField()

    def __str__(self):
        return self.titulo
```

## Crear migraciones

```bash
python manage.py makemigrations
```

## Aplicar migraciones

```bash
python manage.py migrate
```

## Configurar admin.py

Escribe el siguiente código en `libros/admin.py`:

```python
from django.contrib import admin
from .models import Autor, Libro

admin.site.register(Autor)
admin.site.register(Libro)
```

## Iniciar servidor

```bash
python manage.py runserver
```

## Acceder al panel de administración

Abre tu navegador y ve a `http://localhost:8000/admin/`. Inicia sesión con el
superusuario que creaste anteriormente. Deberías ver las opciones para agregar
autores y libros.
