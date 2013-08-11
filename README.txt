
development



from https://github.com/kennethlove/Getting-Started-With-Django

pip-3.2 freeze > requirements.txt

web: python manage.py runserver 0.0.0.0:$PORT --noreload


python-3.3.2 in runtime.txt


git push heroku master



heroku logs is your friend


my database is template1


sql -U development -d template1




heroku run python manage.py syncdb

#use south

python3.2 manage.py schemamigration --initial blog 
python3.2 manage.py migrate blog


Well you have screwed up your migrations.

When I screw them up I find that it is easiest to start over. I delete all migrations/* files. I remove the changes in models.py which I want to migrate at the moment (by the help of version control tools, or just comment out your new fields). Then initialize migration from scratch:

manage.py migrate my_app --delete-ghost-migrations
manage.py schemamigration my_app --init
manage.py migrate my_app --fake
Then restore my changes to models.py and begin new clean migration:

manage.py schemamigration my_app --auto
manage.py migrate my_app
Now when everything is clean it works.




