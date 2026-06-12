---
title: "Unable to download package information"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by waran4 on 2010-02-23
Hello.
I recently installed Ubuntu, and I've been having problems since the moment I tried using the package system in any way. First, the problem was that I couldn't download anything from the Software Center. I seached the web (on my other, Vista, computer), and 5 minutes later, I was typing "sudo apt-get update" into the terminal. This didn't work, and even the apt-get couldn't download every file it needed too, only some of them. I then read somewhere else about changing repository server in the Synaptics Package Manager. I did so, choosing "Select Best Server". That worked (temporarily), and I could update through Update Manager, so I thought I didn't need to update though apt-get. After the restart, everything went back to start, and the problem returned. The update stayed, no problem with that, but now changing server doesn't have effect, and every apt-get command ends up failing due to interrution or failure to connect.

For those who wants it, the source.list:
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic 
main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic 
main restricted

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic 
main restricted



## Major bug fix updates produced after the final release of the

## distribution.
deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
updates main restricted

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
updates main restricted



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team. Also, please note that software in universe WILL NOT receive any

## review or updates from the Ubuntu security team.

deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic 
universe

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic 
universe

deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
updates universe

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
updates universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic 
multiverse

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic 
multiverse

deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
updates multiverse

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
updates multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.
## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) karmic-backports main 
restricted universe multiverse



## Uncomment the following two lines to add software from Canonical's

## 'partner' repository.

## This software is not part of Ubuntu, but is offered by Canonical and the

## respective vendors as a service to Ubuntu users.

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner



deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
security main restricted

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
security main restricted

deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
security universe

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
security universe

deb [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
security multiverse

deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/](http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/) karmic-
security multiverse

```

Also, I'm unable to load any webpages other than google's. Every other just keeps loading into eternity... Does anyone know why this happends and how to fix it?

---

### Post by Enigmapond on 2010-02-23
from what I'm looking at and what you're saying, your problem is with you internet connection not the Ubuntu programmes. I would start there...

---

### Post by waran4 on 2010-02-23
> **Enigmapond said:**
> from what I'm looking at and what you're saying, your problem is with you internet connection not the Ubuntu programmes. I would start there...
Every other computer on the network is problem free. Until I installed ubuntu, this one was also problem free. And some files, when attempted download, are downloaded, but not all. It may be something interfering with the connection between my computer and the router or something. That's the only network problem that i can think of that can occur.

---

### Post by lidex on 2010-02-23
What kind of connection is this - wifi or lan? Have you tried using a different browser? What do you see in network manager?

---

### Post by waran4 on 2010-02-24
> **lidex said:**
> What kind of connection is this - wifi or lan? Have you tried using a different browser? What do you see in network manager?
It was a LAN connection. I didn't try any other browser...

Okay, news: I (unfortunately) gave up on Ubuntu, since I needed the computer so dearly. I reinstalled XP, so you can say that I chickened out...

---

