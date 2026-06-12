---
title: "VLC Player"
date: 2013-04-08
forum: Multimedia Software
---

### Post by Bobisha on 2013-04-08
I am trying to install VLC player in 12.04 64-bit, but I am having trouble. Here is what I keep getting:

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.5+git20130405+r552-0~r42~precise1) but 2.0.5+git20130405+r552-0~r42~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.6ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.6ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.4 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.4 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed
vlc-plugin-notify: Depends: vlc-nox (= 2.0.5+git20130405+r552-0~r42~precise1) but 2.0.5+git20130405+r552-0~r42~precise1 is to be installed
                   Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.3 is to be installed
                   Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is to be installed
                   Depends: libglib2.0-0 (>= 2.12.0) but 2.32.3-0ubuntu1 is to be installed
                   Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6 is to be installed
vlc-plugin-pulse: Depends: vlc-nox (= 2.0.5+git20130405+r552-0~r42~precise1) but 2.0.5+git20130405+r552-0~r42~precise1 is to be installed
                  Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.3 is to be installed
                  Depends: libpulse0 (>= 1:1.0) but 1:1.1-0ubuntu15.2 is to be installed

I have installed all the things that are needed, but I am still having trouble. 

Thanks for the help.

---

### Post by ibjsb4 on 2013-04-08
Try the universal fix for a start.

```
sudo dpkg --configure -a

sudo apt-get -f install
```

Did you install from the software center or the site?

---

