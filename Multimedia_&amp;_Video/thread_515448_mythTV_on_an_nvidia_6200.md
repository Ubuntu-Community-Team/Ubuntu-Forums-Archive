---
title: "mythTV on an nvidia 6200?"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by darksidedude on 2007-08-02
well  i just got ubuntu installed ( its great) however i noticed it has a S-video port in the back, soi i install  mythTv  from the ubuntu websight  [https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

and it ends up not working correctly, i dont know if this card dosen't work with this or i did something wrong but i run it from the terminal i get a bunch of errors ( endless loops no less)

```
        QSqlQuery::exec: database not open
2007-08-01 21:57:16.519 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-01 21:57:16.571 Database not open while trying to load setting: MenuTheme
2007-08-01 21:57:16.572 Unable to connect to database!
2007-08-01 21:57:16.572 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-01 21:57:16.631 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-01 21:57:16.687 Database not open while trying to load setting: QtFontBig
2007-08-01 21:57:16.687 Unable to connect to database!
2007-08-01 21:57:16.688 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-01 21:57:16.751 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-01 21:57:16.803 Database not open while trying to load setting: QtFontMedium
2007-08-01 21:57:16.803 Unable to connect to database!
2007-08-01 21:57:16.803 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-01 21:57:16.859 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-01 21:57:16.915 Database not open while trying to load setting: QtFontSmall
2007-08-01 21:57:17.003 Unable to connect to database!
2007-08-01 21:57:17.004 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-01 21:57:17.059 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-01 21:57:17.115 Database not open while trying to load setting: ThemePainter
2007-08-01 21:57:17.115 Using the Qt painter
2007-08-01 21:57:17.116 Unable to connect to database!
2007-08-01 21:57:17.116 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-01 21:57:17.175 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-01 21:57:17.231 Database not open while trying to load setting: HideMouseCursor
2007-08-01 21:57:17.232 Unable to connect to database!
2007-08-01 21:57:17.232 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
   
```


I have direct tv if this makes a difference thanks for the help

---

### Post by Scorpuk on 2007-08-02
Can you list the hardware you have in your computer?


Video card: Nvidia 6200 (something)
 
TV Tuner Card:  ?


I ask this as you only mention the S-Video connector on your video card and no other capture device.

Just incase you didnt know the S-Video connector on a graphics card is usually just for video out so you can connect your computer to a TV with S-Video connectors and does not mean it has a TV Tuner onboard.


Oh and wots direct TV?


---------------------------------------------------


If you do have a TV Tuner card then:


Could be a mysql database problem


Have you let the text whiz by and end or do you stop it before it naturaly stops?


If not then try and let it stop and it should start the mythfrontend, but prompt you for some configuration screens


First will be the language you want to use


Second will be the IP address of the backend machine and the frontend machine, data base name and database password.

Ensure they are correct. :)

---

### Post by darksidedude on 2007-08-02
hmm i never thought it might not have a tunner card, i thought since there was an svideo port there was a tunner card built in :(

---

### Post by Scorpuk on 2007-08-02
Well TV Tuner cards are relatively cheap and MythTV is awesome once set up. Especially if you work away like me and use mythweb to schedule programs.


For me the Hauppauge Nova T-500 (dual tuner card) worked a treat after installing the firmware for it, but there are others that will work straight out of the box. 


If ya need any help just post on these forums and you will get the help you need, no doubt. ;-)

---

### Post by darksidedude on 2007-08-02
that would be good if i had any open PCi slots, i had the white box bug ( i just had to build my own ubuntu PC, this was before dell) 

I cant figure out how to use nvTV this has to work right? because i do indeed have the svideo port

it gives me this? maybe there is no suport for this card do to it was made by BFG

```
      joe@joe-desktop:~$ nvtv
Fatal: No supported video card found. 
```

---

### Post by afljafa on 2007-08-02
That error has nothing to do with capture cards or graphics adapters. You have a problem connecting to the database.

It could be due to incompatible mysql client (unlikely)

---

### Post by darksidedude on 2007-08-02
yea I doubt there is a tuner card in here, but didnt wana make a new thread on how to use the Svideo out to connect to a TV

---

