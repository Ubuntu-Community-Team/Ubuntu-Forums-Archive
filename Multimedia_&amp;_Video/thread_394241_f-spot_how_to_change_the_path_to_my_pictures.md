---
title: "f-spot: how to change the path to my pictures?"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by oxenfrogga on 2007-03-26
Hello everyone,

from time to time I'm taking photos and I like managing them with f-spot. Up to now, everything worked like a charm, so no reason to worry at all.

But things have changed; a few days ago I bought a new USB drive and moved my pictures (which where NOT imported with the "copy to folder blabla") to that device. Now, of course, f-spot can't find them any more, but I would like to make it do so, because I don't want to reimport all of them a second time (already spent a lot of time on sorting them, adding labels and the like). Sadly, the database file

~/.gnome2/f-spot/photos.db

is a binary file and thus it's rather difficult to change it with sed in an appropriate way. The first line looks like it was a  SQLite format 3 database file. The really bad thing about that is that I don't have the idea of a clou how to go around with that kind of stuff.

Due to that, I would like to ask if anyone already mastered such a problem. Or have I overlooked an option in the program? Hm, don't know ...

Any help would be greatly appreciated,
Oxenfrogga

---

### Post by catchmeifyoutry on 2008-06-15
hai, i just had the same problem for some folders that I moved to a backup disk. Here is my procedure on Ubuntu 8.04 (of course, use at own risk):

0) close f-spot
1) !IMPORTANT! backup the "~/.gnome2/f-spot" dir, just to be sure
2) dump the contents of "~/.gnome2/f-spot/photos.db" to a .sql file.
I used the graphical interface which has an export option to do this.
Probably you'll have to install sqlitebrowser first.
From the commandline:

```
sudo aptitude install sqlitebrowser
```

then open the database file
```
cd
~/.gnome2/f-spot
sqlitebrowser photos.db

```

Go to File-> Export -> Database to SQL file, and save the dump as "fspot.sql", for example.
The SQL file format will allow to put the complete content of the database in a single file, including meta data. This is useful to restore the database in a moment.
You can close sqlbrowser now (or even uninstall it)

3) change the paths in "fspot.sql" that you want to change using a text editor with 'replace all' or something similar.
So replace "/home/catchmeifyoutry/Documents/Pictures/Cat" by "/media/My Book/Pictures/Cat" for example.

3.5) The dump seems to contain two lines that will result in an error in the next step if they are not removed. These lines are somewhere at the end of "fspot.sql" and look like this:

```

CREATE TABLE sqlite_sequence(name,seq);
INSERT INTO sqlite_sequence VALUES('photos',3391);

```

Remove them from fspot.sql.


4) Now recreate the complete database by dumping "fspot.sql" into a new .db file. Lets say the file "bla.db" does not exist yet, then use the sqlite3 command

```
sqlite3 -init fspot.sql bla.db
```

Now there should not be -any- SQL error message.
What you will see is the sql prompt:
```

SQLite version 3.4.2
Enter ".help" for instructions
sqlite> 

```
Just press "Ctrl"+"d" to exit the prompt. The database file "bla.db" should now be created.
If there was an error message, check step 3.5 again. Be sure to remove the (incorrect) "bla.db" before attempting to step 4 again.

By the way, importing could probably be done using sqlbrowser as well but this worked for me already.


5) replace "photos.db" now by "bla.db".
You might first want to check that both files have approximately the same file save first. The new file should at least not be empty.
To rename bla.db:
```
mv bla.db photos.db
```

6) test if everything went well. Start f-spot and see if it found the files again and recreates the thumbnails.
If something went wrong, check first if you correctly changed the paths in "fspot.sql".
In the worst case use your backup of "~/.gnome2/f-spot" to restore the original settings.

Everything seems to work for me now again, so I hope this helps for other people too,
chao!

---

