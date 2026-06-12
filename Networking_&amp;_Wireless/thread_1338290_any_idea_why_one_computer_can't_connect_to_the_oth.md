---
title: "any idea why one computer can't connect to the other?"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by morganpatrick on 2009-11-26
I have two computers, both running ubuntu. one has the other's folder permanently mounted and it can delete and change files.

The other computer can see the first one, but when I go to connect it just keeps prompting me for a password and won't accept the login.

Also: when I try to connect via command line, i.e.

```

sudo mount -t cifs //box/box/ /media/box -o username=user,password=pass, iocharset=utf8,file_mode=0777,dir_mode=0777
```

I just get a list of commands like so:

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.....................
```

and it keeps going on like that. On the other computer this command works just fine. What's going on here?

---

### Post by morganpatrick on 2009-11-26
So is no one responding to this because of the holiday, or because  Karmic is so terminally ****** that the cries for help have inundated the whole system? Hmm...

---

### Post by bobcollard on 2009-11-26
> **morganpatrick said:**
> So is no one responding to this because of the holiday, or because  Karmic is so terminally ****** that the cries for help have inundated the whole system? Hmm...
Yes and no.  I'm not saying which answer goes with which question.  I'm sure when they get around to it they will need more information.  Types of computers, how the one is setup that works compared to the setup of the one that doesn't etc.  Sharing is like networking, everything has to match in settings or it don't jibe.  While you are getting the information for the other guys look closely at both settings.  I networked a classroom with three different systems and 30 computers and it was probably easier than what you are doing if your computers are not compatible.  If they are the same then it has to be in the settings.  Good luck.
P,S, Thought you needed a little support.

---

### Post by Iowan on 2009-11-26
I'm sure you've tried it various ways (various times), but might it be a space in the wrong place?

---

### Post by morganpatrick on 2009-12-09
Solved! go back to stable, functional Jaunty. Now everything works perfect.

---

