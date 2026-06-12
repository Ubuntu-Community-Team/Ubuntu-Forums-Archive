---
title: "Sound not working: Ubuntu 10.04, HP G42"
date: 2012-03-19
forum: Multimedia Software
---

### Post by johnnydoe on 2012-03-19
Sound has never worked with Ubuntu on this laptop.  However, the sound works with other linux distros.

I ran 

```
ls -latrh /home/johndoe/.pulse
```

and received this

```
total 224K
lrwxrwxrwx  1 johndoe johndoe   23 2012-03-19 17:57 37bc9dadb1f660d0680bcac44f5cc2d6-runtime -> /tmp/pulse-U1PasHqE5Gvv
drwx------  2 johndoe johndoe 4.0K 2012-03-19 17:57 .
drwx------ 37 johndoe johndoe  12K 2012-03-19 18:23 ..
-rw-r--r--  1 johndoe johndoe  24K 2012-03-19 18:38 37bc9dadb1f660d0680bcac44f5cc2d6-card-database.tdb
-rw-r--r--  1 johndoe johndoe  60K 2012-03-19 18:38 37bc9dadb1f660d0680bcac44f5cc2d6-device-volumes.tdb
-rw-r--r--  1 johndoe johndoe   42 2012-03-19 18:38 37bc9dadb1f660d0680bcac44f5cc2d6-default-source
-rw-r--r--  1 johndoe johndoe   43 2012-03-19 18:38 37bc9dadb1f660d0680bcac44f5cc2d6-default-sink
-rw-r--r--  1 johndoe johndoe  72K 2012-03-19 18:38 37bc9dadb1f660d0680bcac44f5cc2d6-stream-volumes.tdb

```

Not sure if running that code was helpful to anyone.  This is a fairly  new installation and I haven't really modified other than updating and  upgrading.

---

### Post by Yellow Pasque on 2012-03-19
More info, please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by johnnydoe on 2012-03-19
ALSA info is located here:

```
http://www.alsa-project.org/db/?f=f950a789004a1b394114b512cfea0cd97a085330
```

---

### Post by Yellow Pasque on 2012-03-19
Use the ALSA 1.0.24 Upgrade Script here: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by johnnydoe on 2012-03-19
Thanks! I must say that this worked flawlessly!

---

