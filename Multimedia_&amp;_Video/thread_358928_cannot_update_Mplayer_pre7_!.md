---
title: "cannot update Mplayer pre7 ?!"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by gian on 2007-02-11
hello,

I would like to update my Mplayer pre7 to pre8 or RC1, but if I apt-get update/install, it says that my version is the latest one.

Here is my /etc/apt/sources.list :
*************************************************************
root@oggy:/home/gian# cat /etc/apt/sources.list
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer                 se multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un                 iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main
***********************************************

Is there anything wrong with it?
How can I update Mplayer without compiling the source ?
I don't want to screw up my server...

thanks for your time,
ciao,
-Gian

---

### Post by tbroderick on 2007-02-11
The lastest mplayer version in Dapper is pre7. You can compile from source or search google and this forum to see if anyone has created a package for Dapper.

---

### Post by deadgobby on 2007-02-11
You'll need to go the manula way on installing F9.
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
 Work very well for me.
Gobby
PS you are my 1000th post 
:guitar:

---

### Post by deadgobby on 2007-02-11
Oh snap I all most forgot. YOu can install Automatix and up date FF and flash player.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Gobby

---

### Post by gian on 2007-02-11
> **deadgobby said:**
> You'll need to go the manula way on installing F9.
...PS you are my 1000th post 

I share your excitement for your 1000th post, but here we're talking about Mplayer, not Firefox or Flash... :-)

---

### Post by deadgobby on 2007-02-11
If you enable the extra repo's like from 
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
 after you do the steps it may be in synaptic. If not try installing Automatix at
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
 Good Luck
Gobby

---

### Post by gian on 2007-02-12
Thanks for your links.

I want to try this in the sources.list :
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

if it does not work, I'll go for Automatix.

---

### Post by gian on 2007-02-14
Deadgobby,

tried Automatix on a clean Dapper box, but installs Mplayer pre7....

<sigh>

-Gian

---

