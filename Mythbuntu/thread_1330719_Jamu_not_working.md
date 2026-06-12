---
title: "Jamu not working"
date: 2009-11-18
forum: Mythbuntu
---

### Post by DiGiTGOD on 2009-11-18
I've just upgrading my Myth network to 0.22 (love the new UI!)

I've also decided to start using Storage Groups and MythVideo...  so I've started using the Metadata features for Fanart, etc.

this all works fine, the problem is that I need to populate my library.... so I came across jamu... I've never use it before so I may be using it wrong.  I've tried doing this after creating my user configuration file.

```
./jamu.py -Mf
```

it gives me the following error

```
! Warning - Creating an instance caused and error for one of: MythTV, MythVideo or MythDB


! Error: The MythTV python interface is not installed or Cannot connect to MythTV Backend. MythTV meta data cannot be updated

Exception AttributeError: "'MythDB' object has no attribute 'db'" in <bound method MythDB.__del__ of <MythTV.MythDB.MythDB object at 0xa1cfdec>> ignored

```

I found a way of testing whether the bindings are working... not knowing much about python, I don't know whether this actually tests it.

```
from MythTV.MythTV import *

```

this seems to work.

has anyone got any ideas??

I've used the 9.10  MythBuntu ISO to download, and the machine is a backend only.

Hope someone can help!!!

thanks
Martin

---

### Post by RDV on 2009-11-19
Martin,
    This is most likely caused by a missing or misconfiguration "~/.mythtv/comfig.xml" file.
See #1 of [http://www.mythtv.org/wiki/Jamu#This_stupid_thing_does_not_work.21](http://www.mythtv.org/wiki/Jamu#This_stupid_thing_does_not_work.21)

---

### Post by sledhead45 on 2009-12-21
Hey, I'm having the same issue. I've been over and over the [wiki page]("http://www.mythtv.org/wiki/Jamu#This_stupid_thing_does_not_work.21"). 

Im not using mythbuntu, but rather standard 32-bit karmic with a frontend/backend mythtv setup. 

relevant directories look as follows:

```
mythbox@travis-desktop:/home/mythtv/.mythtv$ ls -ll
total 68
lrwxrwxrwx 1 root   root      22 2009-12-14 22:29 config.xml -> /etc/mythtv/config.xml
-rw-r----- 1 root   root     330 2009-12-20 23:58 config.xml~
-rw-r----- 1 root   root     334 2009-12-21 18:31 config.xml.backup
-rw-r--r-- 1 mythtv mythtv 28384 2009-12-21 19:45 jamu.conf
-rw-r--r-- 1 mythtv mythtv 28387 2009-12-20 22:53 jamu.conf~
-rw-r----- 1 root   root    1123 2009-12-20 23:51 mysql.txt
```

I've triple checked the config.xml and its setting are correct. mythfrontend connects fine with /etc/mythtv/config.xml.

```
mythbox@travis-desktop:/usr/share/mythtv/mythvideo/scripts$ ls -ll
total 484
-rwxr-xr-x 1 root root  11483 2009-08-12 00:16 allocine.pl
-rwxr-xr-x 1 root root  10578 2009-08-12 02:14 alpacine.pl
-rwxr-xr-x 1 root root   8326 2009-08-13 00:53 fetch_poster.py
-rwxr-xr-x 1 root root  29078 2009-08-21 13:19 find_meta.py
-rwxr-xr-x 1 root root   9053 2009-04-10 20:04 ilovecinema.pl
-rwxr-xr-x 1 root root  12100 2009-08-13 00:53 imdbpy.py
-rw-r--r-- 1 root root  28388 2009-10-10 18:08 jamu-example.conf
-rwxrwxrwx 1 root root 254761 2009-10-22 12:41 jamu.py
-rw-r--r-- 1 root root   4108 2009-08-24 18:54 jamu.README
-rwxr-xr-x 1 root root   9989 2009-04-10 20:04 kinox.pl
drwxr-xr-x 2 root root   4096 2009-12-18 19:54 MythTV
-rwxr-xr-x 1 root root  10229 2009-07-14 16:34 ofdb.py
-rw-r--r-- 1 root root   2582 2009-04-10 20:04 README
-rwxr-xr-x 1 root root  12296 2009-08-09 20:29 tmdb.pl
drwxr-xr-x 2 root root   4096 2009-12-20 23:10 ttvdb
-rwxr-xr-x 1 root root  51052 2009-10-15 10:27 ttvdb.py
```

mythbuntu-repos.dev has been installed and within the jamu.py i see:
> __version__=u"v0.5.5" 

The command I am trying to run is:
```
/usr/share/mythtv/mythvideo/scripts/jamu.py -l en -C "/home/mythtv/.mythtv/jamu.conf" -sMV > "/home/mythbox/Desktop/log.txt"
```

I've tried with and without sudo.

All I can ever get from this command is:
```
! Error: The MythTV python interface is not installed or Cannot connect to MythTV Backend. MythTV meta data cannot be updated

Exception AttributeError: "'MythDB' object has no attribute 'db'" in <bound method MythDB.__del__ of <MythTV.MythDB.MythDB object at 0x9636e4c>> ignored
```

```
python --version
``` returns ```
Python 2.6.4
```

I'm guessing its something stupid I'm missing, but i can't find it. Any input would be great. Thanks

---

### Post by sledhead45 on 2010-01-03
Ok well I had another look at this today and immediately saw the problem. For this issue the wiki says: "you are likely missing a properly configured ~/.mythtv/config.xml file." Take that file location quite literally.

---

