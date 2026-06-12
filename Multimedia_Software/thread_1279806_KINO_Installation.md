---
title: "KINO Installation"
date: 2009-10-01
forum: Multimedia Software
---

### Post by kmuzheri on 2009-10-01
Hello Guys

I am relatively new to the LINUX (UBUNTU) platform. I love the power and stability I have seen in the short period I have used LINUX. I however, have a problem with installation. I would like to install KINO for video editing. If I go to the ADD/REMOVE applications submenu, I can see it. When I try to download through the automatic install option (synaptic, I think), it fails. When I check the progress of single files, I realize each one of the files fails to download. A snippet of the message is below:

```
http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found
http://ftp.debian.org/dists/sarge/main/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 404 Not Found
http://ftp.leg.uct.ac.za/pub/linux/ubuntu/dists/feisty/universe/source/Sources.bz2
```How could I go about this problem. Your advice is greatly appreciated.
Thank You

---

### Post by bruno9779 on 2009-10-01
Download the .deb from here

[http://packages.ubuntu.com/jaunty/graphics/kino](http://packages.ubuntu.com/jaunty/graphics/kino)

---

### Post by bruno9779 on 2009-10-01
Hey!!!

Do you run feisty? and what about that sarge entry?

If you don't run jaunty you will have to look in getdeb (the link i gave) for the package relative to your release.

If you post your release and the content of /etc/apt/sources.lst I can help you out putting some order to it

---

### Post by kmuzheri on 2009-10-01
My Ubuntu Release is 7.04

and my /etc/apt/sources.lst is a below:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty main restricted
deb-src [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty-updates main restricted
deb-src [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://zw.archive.ubuntu.com/ubuntu/](http://zw.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://zw.archive.ubuntu.com/ubuntu/](http://zw.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty-security main restricted
deb-src [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty-security universe
deb [http://ftp.leg.uct.ac.za/pub/linux/ubuntu/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu/) feisty-security multiverse
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main

---

