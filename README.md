# djangogirls012


https://tutorial.djangogirls.org/en/installation/


    sudo apt install python3.5
    sudo apt install python3.5-venv
    
    mkdir djangogirls
    cd djangogirls
    
    python3.5 -mvenv myvenv
    source myvenv/bin/activate
    pip install django
    pip install --upgrade pip


https://tutorial.djangogirls.org/en/django_start_project/

    django-admin startproject mysite .
    ./manage.py migrate
    
mysite/settings.py
    TIME_ZONE = 'Asia/Taipei'
    STATIC_ROOT = os.path.join(BASE_DIR, 'static')


    ./manage.py runserver $IP:$PORT
    https://djangogirls012-twoutlook.c9users.io/
    https://djangogirls012-twoutlook.c9users.io/admin
    
    
# create blog application
## new terminal
    cd djangogirls
    source myvenv/bin/activate 
    ./manage.py startapp blog
    
    
# mysite/settings.py

    INSTALLED_APPS = [
      ...
      'blog',
    

# models.py
    from django.db import models
    from django.utils import timezone
    
    
    class Post(models.Model):
        author = models.ForeignKey('auth.User')
        title = models.CharField(max_length=200)
        text = models.TextField()
        created_date = models.DateTimeField(
                default=timezone.now)
        published_date = models.DateTimeField(
                blank=True, null=True)
    
        def publish(self):
            self.published_date = timezone.now()
            self.save()
    
        def __str__(self):
            return self.title



# DB
    ./manage.py makemigrations
    ./manage.py migrate


# Template

# View




# URL
## mysite/urls.py

    from django.conf.urls import include, url
    from django.contrib import admin
    
    urlpatterns = [
        url(r'^admin/', admin.site.urls),
        url(r'', include('blog.urls')),
    ]
    
## blog/urls.py   

from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^$', views.post_list, name='post_list'),
]


# Github
    echo "# djangogirls012" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin https://github.com/twoutlook/djangogirls012.git
    git push -u origin master

# Django Forms
https://tutorial.djangogirls.org/en/django_forms/