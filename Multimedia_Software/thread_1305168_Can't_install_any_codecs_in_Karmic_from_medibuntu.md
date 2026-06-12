---
title: "Can't install any codecs in Karmic from medibuntu"
date: 2009-10-29
forum: Multimedia Software
---

### Post by dj-toonz on 2009-10-29
Hi all, I'm trying to install the codecs in karmic so I can play DVD's / MP3's & the likes but this is the error I'm getting are the repos down

After this operation, 111kB of additional disk space will be used.
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free libdvdcss2 1.2.10-0.3medibuntu1
  404  Not Found [IP: 88.191.79.39 80]
Failed to fetch [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)  404  Not Found [IP: 88.191.79.39 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
toonz@toonz-laptop:~$ 

I've tried update about 5 times & all goes though OK but then that error 

cheers

---

### Post by andrew.46 on 2009-10-30
Hi dj-toonz,

Possibly MEdibuntu had some heavy use while everybody was installing and setting up their new copies of Karmic? I have installed the w32codecs from there just recently, perhaps the wave has passed now :). If there are problems there is always MEdibuntu on irc: #medibuntu on irc.freenode.net. I had a brief chat there a while ago and they seem very obliging.

Andrew

---

### Post by howefield on 2009-10-30
Something to remember for the next upgrade :) download them manually before the rush


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[I]"Installing Individual Packages

Most Ubuntu users will only require a few packages from the Medibuntu repository; nonetheless, it's easier simply to add the repository to your setup as detailed above. The most common packages are libdvdcss2 for playing DVDs and the non-native codecs packages (w32codecs, w64codecs, ppc-codecs) for playing non-native media formats. If you wish to install individual packages, then follow the steps below.
    *      With your favourite web browser, go to [http://packages.medibuntu.org/](http://packages.medibuntu.org/).
    * Choose the Ubuntu version you're currently using.
    * Find the package for your architecture in the listing, and save it to your personal directory on your hard drive. You may need to also download any dependencies that are also in medibuntu.
    * Right click on the package you just downloaded.
    * Select Ubuntu Package Menu.
    * Choose Install Package. "[/I]

---

