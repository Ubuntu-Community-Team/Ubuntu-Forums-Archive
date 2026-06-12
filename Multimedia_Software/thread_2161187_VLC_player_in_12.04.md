---
title: "VLC player in 12.04"
date: 2013-07-09
forum: Multimedia Software
---

### Post by Bobisha on 2013-07-09
I am running Ubuntu 12.04 64 Bit and I am having trouble installing VLC Player. I have tried through he terminal and the software center and get the same results. This is the message I get:

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.5+git20130703+r591-0~r42~precise1) but 2.0.5+git20130703+r591-0~r42~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.6ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.6ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.4 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.4 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.4 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed
vlc-plugin-notify: Depends: vlc-nox (= 2.0.5+git20130703+r591-0~r42~precise1) but 2.0.5+git20130703+r591-0~r42~precise1 is to be installed
                   Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.4 is to be installed
                   Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is to be installed
                   Depends: libglib2.0-0 (>= 2.12.0) but 2.32.3-0ubuntu1 is to be installed
                   Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6 is to be installed
vlc-plugin-pulse: Depends: vlc-nox (= 2.0.5+git20130703+r591-0~r42~precise1) but 2.0.5+git20130703+r591-0~r42~precise1 is to be installed
                  Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.4 is to be installed
                  Depends: libpulse0 (>= 1:1.0) but 1:1.1-0ubuntu15.3 is to be installed


I have been trying for about an hour and have checked the forums and I am still unable to install it. I have even tried purging and re installing it like that to no avail. I have also tried installing each of the packets above individually, but that doesn't seem to work either. Any suggestions?

---

### Post by mc4man on 2013-07-09
When using a ppa you may occasionally try to upgrade in the middle of a package upgrade, that's what happened to you.
So if seeing as you saw instead of trying to force or re-install [go to the ppa page]("https://launchpad.net/~videolan/+archive/stable-daily") & ck. out - 
screen 1 - the yellow circles mean build in progress
screen 2 - current status of the amd64 build for precise

I'd say another 1/2 - to 1 hr. till done & published, then you'll be ok to upgrade.

Edit:  today has been a very busy day for launchpad builds, ppa packages are taking 7 -9 hrs. to clear the queue & start building. During that time & until published not too good for upgrading your install from that ppa..

---

### Post by Bobisha on 2013-07-10
Thanks. I tried again this morning, but it still didn't work. I'll just do a reinstall of the OS and try again... Thanks anyway. I'll let you know if that works.

---

### Post by Bobisha on 2013-07-11
Rebooting didn't work... I'll keep fooling around with it and see if I can fix it...

---

### Post by pixiq on 2013-07-20
I install vlc into 12.04.2 in a straight-forward way without involving any PPAs.

```
sudo apt-get install vlc
```

I think mc4man is right. Maybe it works better after a few more hours. By the way, do you really need the PPA?

---

### Post by trash on 2013-08-02
I just installed xubuntu 12.04, not using PPA's, tried to install VCL and got the same list of depends.. don't know where to start to fix this.
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libavcodec53 but it is not going to be installed or
 	libavcodec-extra-53 but it is not going to be installed
 Depends: libqtgui4 but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.10) but it is not installable
 Depends: libsdl1.2debian (>=1.2.10-1) but it is not installable
 Depends: libtar0  but it is not installable
 Depends: libva-x11-1 (>1.0.15~) but it is not installable
 Depends: libva1 (>1.0.15~) but it is not installable
 Depends: libxcb-keysyms1 (>=0.3.8) but it is not installable
 Recommends: vlc-plugin-notify but it is not going to be installed
 Recommends: vlc-plugin-pulse but it is not going to be installed

---

### Post by trash on 2013-08-04
Ok fixed it, I was having a signiture issue in apt-get so followed this [http://ubuntuforums.org/archive/index.php/t-1702803.html](http://ubuntuforums.org/archive/index.php/t-1702803.html)

Also added medibuntu following this [http://www.anthonynotes.com/2012/05/04/anthonys-xubuntu-12-04-post-installation-guide/](http://www.anthonynotes.com/2012/05/04/anthonys-xubuntu-12-04-post-installation-guide/)

VLC is now installed:D

---

