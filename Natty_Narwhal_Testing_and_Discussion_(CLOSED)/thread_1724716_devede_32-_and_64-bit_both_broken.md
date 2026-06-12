---
title: "devede 32- and 64-bit both broken"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wizard10000 on 2011-04-08
I've had problems with both 32- and 64-bit devede failing when building the DVD itself - devede suggests I'm out of disk space, which I ain't  ;)

Found the solution here - apparently the new dvdauthor requires a VIDEO_FORMAT variable that wasn't required before.

[http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1](http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948?pli=1)

Running in a terminal window and exporting the variable before starting devede within the same window worked.  Testing another video file to confirm, but this got things running.

```
wizard@wizard-desktop:~$ export VIDEO_FORMAT=NTSC
wizard@wizard-desktop:~$ devede

```

---

### Post by cariboo on 2011-04-08
How recent is this problem? I used devede to create 17 dvds about two weeks ago, and didn't have any problems.

---

### Post by wizard10000 on 2011-04-08
> **cariboo907 said:**
> How recent is this problem? I used devede to create 17 dvds about two weeks ago, and didn't have any problems.

You might wanna try it again now.  I installed beta 1 about five days ago.

Version of dvdauthor I have installed is 0.7.0-1

cheers -

---

### Post by wizard10000 on 2011-04-08
More info, cariboo - it appears it happened with beta 1, which I installed on Monday.  I exported my list of installed packages, blew away everything but /home, installed beta 1 and then reloaded the list of installed packages and let apt do it's thing.

```
Start-Date: 2011-04-04  08:45:37
Commandline: apt-get dselect-upgrade
Install: ...dvdauthor:amd64 (0.7.0-1)
```

So - this came out of the box with beta 1 it appears.

edit:  Also, that group is devede's official support forum, so the developer's got it - he had it in January and hasn't released a fix yet.  I may have to cobble something together to get the variable loaded in the meantime  :(

---

### Post by wizard10000 on 2011-04-08
Two for two good DVDs now where I was 0 for 6 before.  I'll put together a bug report in the morning.

cheers -

---

### Post by rbrick49 on 2011-04-08
I just tried devede on my computer it is working ok

---

### Post by wizard10000 on 2011-04-09
> **rbrick49 said:**
> I just tried devede on my computer it is working ok

Interesting.  Did you go through the whole process?  This happens after the video is rendered and when devede calls dvdauthor to build the DVD tree.

Maverick had dvdauthor 0.6.18-1build1, while Natty has 0.7.0-1.  Version of devede is the same for both releases (3.16.9-0ubuntu3).

Only other thing I can think of is it's a KDE-only problem, but that doesn't make a whole lot of sense - but I can reproduce it consistently on both 32-and 64-bit machines.

But report is here if anyone else has issues.

[https://bugs.launchpad.net/ubuntu/+source/devede/+bug/755340](https://bugs.launchpad.net/ubuntu/+source/devede/+bug/755340)

---

