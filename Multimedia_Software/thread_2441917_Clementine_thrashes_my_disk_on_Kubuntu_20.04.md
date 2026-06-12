---
title: "Clementine thrashes my disk on Kubuntu 20.04"
date: 2020-04-27
forum: Multimedia Software
---

### Post by zaivala on 2020-04-27
I installed Kubuntu 20.04 as soon as it became official. I set up Clementine as my music player, and installed all the Studio tools. I am running stock Kubuntu, except for running Sweet theme, changing the wallpaper (to one supplied by the distro), and installing the Studio apps and Clementine.

I have all my music on an external SSD attached through a "toaster", external dock with space for 2 drives as well as extra card and USB ports. It worked fine the first time I used it (which, incidentally, was before I installed the Studio tools).

This morning I tried to play something and it just thrashed the heck out of the SSD, with more notifications than I could keep up with and, eventually, it said that my disk was empty. I booted to another distro (I have 6 on this machine), pulled the drive out of the toaster, and ran my backups. As soon as I pulled the other drive, the drive with my music on it showed up again with all the files. I took the opportunity to make sure my other backup drive was up to date, and tried again. Same thing. It works fine in Mint 19.3, OpenMandria Lx 4.1, Bodhi 5.1.0, and I didn't try either of the other two. It's either a Clementine issue or a Kubuntu 20.04 issue, I'm not sure which (I don't use Clementine on my other distros).

Ay help would be appreciated.

---

### Post by zaivala on 2020-05-01
Apparently it is a problem with Clementine, either because of some change in 20.04 (there were a few problems in some programs when I moved from 16.04 to 18.04) or just a bug in Clementine. I noticed that sneekylinux mentioned that Clementine got wonky on him on Xubuntu 20.04 so he replace it with Strawberry.

---

### Post by guiverc on 2020-05-01
I don't have any clues on your issue, but `clementine` is my default music player on Lubuntu 20.04 systems and I've not noticed anything unusual.  My clementine on this box is "1.4 rc1" (this box has bumped to *groovy*) but it'll be the same on other boxes too (using *focal*).

```
guiverc@d960-ubu2:~$   apt-cache policy clementine
clementine:
  Installed: 1.4.0~rc1+dfsg-1
  Candidate: 1.4.0~rc1+dfsg-1
  Version table:
 *** 1.4.0~rc1+dfsg-1 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) groovy/universe amd64 Packages
```

---

