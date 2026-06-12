---
title: "Kodi 17 Released! depot on PPA 16.04 pulls Kodi 18 Alpha binaries ?"
date: 2017-04-01
forum: Multimedia Software
---

### Post by donnywood-studio on 2017-04-01
HI all

I was using alpha Kodi 18 Alpha for couple of months  on my ubuntu 16.04 and lately crashing lots which is expected 

I was using the instruction at the kodi site previously to get Kodi 18 alpha
[https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa?field.series_filter=xenial).

I seem to get daily update of when ever i use kodi 18 alpha. 

I plan to use Kodi 17 final version .  I have not installed kodi 17 on ubuntu but have it on a Windows 10 PC. working fine

I removed Kodi 18  using sw updater gui 

[B]for Kodi 17 I followed the instruction listed at this site 
[http://ubuntuhandbook.org/index.php/2017/02/kodi-17-released-install-in-ubuntu-16-10/](http://ubuntuhandbook.org/index.php/2017/02/kodi-17-released-install-in-ubuntu-16-10/)[/B]

[B]sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt update[/B]
[B]sudo apt install kodi
[COLOR=#ff0000]
[/COLOR][/B][COLOR=#ff0000]but still getting kodi 18 Alph**a binaries**[/COLOR]
attach the dpkg version after installing Kodi 17 as per the instruction. 

**Any pointers to locate Kodi 17  Software Depot ?**

*************************************************************
```
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Setting up python-bluez (0.22-1) ...
Setting up python-simplejson (3.8.1-1ubuntu2) ...
Setting up libnfs8:amd64 (1.9.8-1) ...
Setting up kodi (2:18.0~git20170402.0200-fcfa9bc-0xenial) ...
Setting up kodi-peripheral-joystick (1.3.1-3~xenial) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for menu (2.1.47ubuntu1) ...
```
```
orcanet@hp8460p:~$ dpkg -l|grep kodi
ii  [COLOR=#ff0000]**kodi                                          2:18.0~git20170402.0200-fcfa9bc-0xenial **[/COLOR]      all          Kodi Media Center (arch-independent data package)
ii  kodi-bin                                      2:18.0~git20170402.0200-fcfa9bc-0xenial       amd64        Kodi Media Center (binary data package)
ii  kodi-peripheral-joystick                      1.3.1-3~xenial                                amd64        Joystick peripheral addon for Kodi
ii  kodi-pvr-hts                                  4.0.8-1~xenial                                amd64        TVHeadEnd PVR for Kodi
```

***********************************************************************

OS is Linux hp8460p 4.4.0-71-generic #92-Ubuntu SMP Fri Mar 24 12:59:01 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

much appreciated

Don

---

### Post by donnywood-studio on 2017-04-02
RESOLVED..just now 

Simple

1. Just remove all the non stable depot/repositories in the software policy database 
**sudo apt-cache policy | grep team-xbmc**

 Remove the unstable or nightly PPA where [B]there is team-xbmc in the string 
[/B]
sudo add-apt-repository -r [B]ppa:team-xbmc/xbmc-nightly

[/B]2. Add team-xbmc/ppa back and install kodi 17 stable version

[B]sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get remove kodi kodi-bin
sudo apt-get install kodi

Works perfect !

orcanet@hp8460p:~$ sudo apt-cache policy|grep team-x
[sudo] password for orcanet: 
 500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main i386 Packages
     release v=16.04,o=LP-PPA-team-xbmc,a=xenial,n=xenial,[COLOR=#ff0000]l=Kodi stable[/COLOR],c=main,b=i386
 500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main amd64 Packages
     release v=16.04,o=LP-PPA-team-xbmc,a=xenial,n=xenial,[COLOR=#ff0000]l=Kodi stable[/COLOR],c=main,b=amd64
orcanet@hp8460p:~$ dpkg -l|grep kodi
ii  kodi                                          [COLOR=#ff0000]2:17.1~git20170320.2031-final-0xenial[/COLOR]         all          Kodi Media Center (arch-independent data package)
ii  kodi-bin                                      2:17.1~git20170320.2031-final-0xenial         amd64        Kodi Media Center (binary data package)
ii  kodi-peripheral-joystick                      1.3.1-3~xenial                                amd64        Joystick peripheral addon for Kodi
ii  kodi-pvr-hts                                  4.0.8-1~xenial                                amd64        TVHeadEnd PVR for Kodi



[/B]

---

### Post by cybrsaylr on 2017-04-05
Used your link: [http://ubuntuhandbook.org/index.php/2017/02/kodi-17-released-install-in-ubuntu-16-10/](http://ubuntuhandbook.org/index.php/2017/02/kodi-17-released-install-in-ubuntu-16-10/)

To install Kodi 17.1 via Terminal on 16.04 and WOW!

Kodi works great and does quite a bit. There's a lot to learn on setting it up. 
Found this YouTube vid very helpful in setting Kodi up: [https://www.youtube.com/watch?v=NdYA1v8PcuM](https://www.youtube.com/watch?v=NdYA1v8PcuM)

FYI the first link for movies in the above tutorial is dead and does not work, so don't use it!
However the other links he listed worked very well

---

