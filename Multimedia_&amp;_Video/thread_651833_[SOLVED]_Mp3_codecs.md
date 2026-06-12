---
title: "[SOLVED] Mp3 codecs"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by tad1073 on 2007-12-28
I can't play mp3's with any player i have and have followed all the threads to no avail. [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1) thats what I get when I try to update synaptics. I can't download gstreamer or any mp3 codecs. What gives...

---

### Post by pay on 2007-12-28
What does your sources.list contain?```
cat /etc/apt/sources.list
```

---

### Post by ray bot on 2007-12-28
Try running this command: ```
sudo rm /var/lib/apt/lists/partial/* && sudo apt-get update
``` and then try installing the codec again.

---

### Post by tad1073 on 2007-12-28
> **pay said:**
> What does your sources.list contain?```
cat /etc/apt/sources.list
```

```
# 
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb http://ubuntu.beryl-project.org feisty main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
```

---

### Post by tad1073 on 2007-12-28
> **ray bot said:**
> Try running this command: ```
sudo rm /var/lib/apt/lists/partial/* && sudo apt-get update
``` and then try installing the codec again.
got some error mesages, but I reran the gstreamer package and it installed fine. Thanks a million.

---

### Post by pay on 2007-12-30
You have multiple instances of the same repository... I don't think that it would cause a problem but just incase it does you could change your sources.list with```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main feisty-updates feisty-backports restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty feisty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb http://ubuntu.beryl-project.org feisty main
deb http://www.getautomatix.com/apt feisty main
deb http://archive.canonical.com/ubuntu feisty-commercial main
```and it should do the exact same thing

---

