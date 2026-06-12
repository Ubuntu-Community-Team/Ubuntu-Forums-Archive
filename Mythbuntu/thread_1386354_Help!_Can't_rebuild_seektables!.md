---
title: "Help! Can't rebuild seektables!"
date: 2010-01-20
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-01-20
hi guys, whenever i try to rebuild a seektable (im using mythbuntu x64 karmic with the 0.23 repository), it wont let me do it. this is for all videos in my database (havent tried recordings as i dont need to).
This is the command i run: 
```
ythcommflag --file /var/lib/mythtv/videos/Alien\:\ Directors\ Cut.mkv --rebuild
```

and this is the error i get:
```
2010-01-20 21:37:09.117 Using runtime prefix = /usr
2010-01-20 21:37:09.117 Using configuration directory = /home/john/.mythtv
2010-01-20 21:37:09.117 Empty LocalHostName.
2010-01-20 21:37:09.122 New DB connection, total: 1
2010-01-20 21:37:09.126 Closing DB connection named 'DBManager0'
mythcommflag: ERROR: Unable to find DB info for Alien: Directors Cut.mkv
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.

```

Any help? ive tried this with the videos storage group enabled and disabled. same result both times.

---

### Post by ian dobson on 2010-01-20
Hi,

Is the mkv file you want to commflag a file you downloaded from the internet/not a file that mythtv recorded?

If yes, I think mythcommflag expects to find information about the recording in the recorded database, before it even tries to commflag the file. If you have phpmyadmin installed you could try to manually create a record in the recorded database.

Regards
Ian Dobson

---

### Post by bergqvistjl on 2010-01-21
its ok, it should have been --video instead of --file. seems to have worked.

---

