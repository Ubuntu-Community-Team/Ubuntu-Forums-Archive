---
title: "Who has killed lame"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by jsgaarde on 2006-07-23
I can't install liblame, does anyone know why?
I have tried installing lame, and liblame0. Both say the following.
sh-3.1$ sudo apt-get install lame
Reading package lists... Done
Building dependency tree... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate

My sources.list:
```
sh-3.1$ cat /etc/apt/sources.list

deb http://dk.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://dk.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://dk.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ dapper universe

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Best Regards Jakob Simon-Gaarde

---

### Post by clouno on 2006-07-26
Hello,
Similar problem here, I'm trying to locate libmp3lame.so for audacity but I can't locate the "lame" package for dapper. Here is my sources.list:

[INDENT]deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

[/INDENT]

The package seems available ([http://packages.ubuntulinux.org/dapper/sound/](http://packages.ubuntulinux.org/dapper/sound/)) but doesn't show up on my system.

Any hints here?
Cheers,

Daniel

---

### Post by NMUrugbysteve on 2006-07-26
The problem is that you both need to enable the "multiverse" repos. You're going to want to add to your sources something like this.


deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) dapper universe *multiverse*
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) dapper universe *multiverse*

---

### Post by clouno on 2006-07-27
NMUrugbysteve,
Thanks for pointing out the "multiverse" repos, this all works fine now.
Cheers,

Dan

---

### Post by RJARRRPCGP on 2006-07-27
> **jsgaarde said:**
> I can't install liblame, does anyone know why?
I have tried installing lame, and liblame0. Both say the following.
sh-3.1$ sudo apt-get install lame
Reading package lists... Done
Building dependency tree... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate


Please update the lists by typing the following: ```
sudo apt-get update
```

---

