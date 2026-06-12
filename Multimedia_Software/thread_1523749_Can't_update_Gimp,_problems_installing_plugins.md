---
title: "Can't update Gimp, problems installing plugins"
date: 2010-07-04
forum: Multimedia Software
---

### Post by furoido on 2010-07-04
Hi guys,

Complete noob here, so please bear with me!
When I try to update my Gimp from 2.6.8, I get this:

andrew@andrew-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

How do I get round it?

Also, I downloaded a couple of Gimp plug-ins onto my desktop but don't know how to install them!
1-focusblur-3.2.6.tar.xz
2-vignette.scm

Anyone kind enough to give me the EXACT instructions to do so?!

Thanks!

---

### Post by indytim on 2010-07-04
The OP has "double-posted".  Thread addressed in the General Topics area.

[-X

Indytim

---

### Post by 23dornot23d on 2010-07-04
> **furoido said:**
> Hi guys,

Complete noob here, so please bear with me!
When I try to update my Gimp from 2.6.8, I get this:

andrew@andrew-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

How do I get round it?

Also, I downloaded a couple of Gimp plug-ins onto my desktop but don't know how to install them!
1-[focusblur-3.2.6.tar.xz]("http://registry.gimp.org/node/1444")
2-[vignette.scm]("http://registry.gimp.org/files/vignette_0.scm")

Anyone kind enough to give me the EXACT instructions to do so?!

Thanks!

[**Ok its on this Thread Now Just found it**]("http://ubuntuforums.org/showthread.php?p=9545787")


[Installing scripts Gimp]("http://www.youtube.com/watch?v=UJWkx3pcw0A")

---

### Post by claus on 2010-07-08
Hi,

> **furoido said:**
> andrew@andrew-desktop:~$ apt-get install gimp

you will have to install Gimp as root: '[COLOR="Red"]sudo[/COLOR] apt-get install gimp'. And regarding the plug-ins: Untar the archive and put the .scm files into $HOME/.gimp-2.2/plug-ins.

HTH,

Claus

---

