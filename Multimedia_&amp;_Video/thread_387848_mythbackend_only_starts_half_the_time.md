---
title: "mythbackend only starts half the time"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by electronikjunkie on 2007-03-18
for some reason i have problems connecting to mythtvdatabase from the frontend, but it only happens sometimes.  half the time i log in and start mythbackend by hand and then start mythfrontend with no problems. the other times i have troubles. here's the output from mythbackend when i have problems:
```
me@mycomputer:~$ mythbackend
2007-03-18 20:14:53.899 Using runtime prefix = /usr
2007-03-18 20:14:54.002 New DB connection, total: 1
2007-03-18 20:14:54.006 Connected to database 'mythconverg' at host: localhost
2007-03-18 20:14:54.038 Current Schema Version: 1160
Starting up as the master server.
2007-03-18 20:14:54.065 New DB connection, total: 2
2007-03-18 20:14:54.066 Connected to database 'mythconverg' at host: localhost
2007-03-18 20:14:54.109 EITHelper: localtime offset -4:00:00 
2007-03-18 20:14:54.175 New DB connection, total: 3
2007-03-18 20:14:54.176 Connected to database 'mythconverg' at host: localhost
2007-03-18 20:14:54.204 DVBChan(0) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
2007-03-18 20:14:54.223 EITHelper: localtime offset -4:00:00 

```

i have:

asus av8-deluxe
geforce 6200
pchdtv hd-5500
pvr-350

anyone know what's going on?

---

### Post by pixelseventy2 on 2007-09-24
i've been having the same problem and think i've sussed it. I have a UK dvb card and a pvr250.  It seems that my 2 cards start in a random order. Normally the pvr250 is /dev/video0 but sometimes the dvb starts first and the pvr250 becomes /dev/video1.  This is when it fails to start.  Now I just need to figure out how to force the order :)

BTW, this is on a Fedora box

---

