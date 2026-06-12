---
title: "Flash Plugin in live CD"
date: 2008-09-17
forum: Multimedia Software
---

### Post by phoenixankit on 2008-09-17
I want to use Flash Plugin in  firefox, in the Live CD. I installed flash plugin nonfree using synaptic(it was only ~18kb). But I still cant view flash in firefox.

---

### Post by phoenixankit on 2008-09-17
OKay, so I uninstalled it from synaptic, and installed it from the terminal, this is what i get:

> ubuntu@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 130 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 92206 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--16:23:11--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 122.252.138.70
Connecting to fpdownload.macromedia.com|122.252.138.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   31.12 KB/s
   50K .......... .......... .......... .......... ..........  3%   53.54 KB/s
  100K .......... .......... .......... .......... ..........  5%   24.72 KB/s
  150K .......... .......... .......... .......... ..........  6%   35.03 KB/s
  200K .......... .......... .......... .......... ..........  8%   37.72 KB/s
  250K .......... .......... .......... .......... .......... 10%   47.27 KB/s
  300K .......... .......... .......... .......... .......... 11%   34.28 KB/s
  350K .......... .......... .......... .......... .......... 13%   26.41 KB/s
  400K .......... .......... .......... .......... .......... 15%   33.58 KB/s
  450K .......... .......... .......... .......... .......... 16%   43.58 KB/s
  500K .......... .......... .......... .......... .......... 18%   40.20 KB/s
  550K .......... .......... .......... .......... .......... 20%   33.71 KB/s
  600K .......... .......... .......... .......... .......... 21%   32.58 KB/s
  650K .......... .......... .......... .......... .......... 23%   30.34 KB/s
  700K .......... .......... .......... .......... .......... 25%   38.54 KB/s
  750K .......... .......... .......... .......... .......... 26%   42.27 KB/s
  800K .......... .......... .......... .......... .......... 28%   48.33 KB/s
  850K .......... .......... .......... .......... .......... 30%   41.46 KB/s
  900K .......... .......... .......... .......... .......... 31%   45.25 KB/s
  950K .......... .......... .......... .......... .......... 33%   46.23 KB/s
 1000K .......... .......... .......... .......... .......... 35%   48.98 KB/s
 1050K .......... .......... .......... .......... .......... 36%   47.45 KB/s
 1100K .......... .......... .......... .......... .......... 38%   38.21 KB/s
 1150K .......... .......... .......... .......... .......... 40%   32.63 KB/s
 1200K .......... .......... .......... .......... .......... 42%   49.60 KB/s
 1250K .......... .......... .......... .......... .......... 43%   50.25 KB/s
 1300K .......... .......... .......... .......... .......... 45%   50.94 KB/s
 1350K .......... .......... .......... .......... .......... 47%   37.39 KB/s
 1400K .......... .......... .......... .......... .......... 48%   46.25 KB/s
 1450K .......... .......... .......... .......... .......... 50%   41.08 KB/s
 1500K .......... .......... .......... .......... .......... 52%   44.41 KB/s
 1550K .......... .......... .......... .......... .......... 53%   34.85 KB/s
 1600K .......... .......... .......... .......... .......... 55%   46.99 KB/s
 1650K .......... .......... .......... .......... .......... 57%   33.06 KB/s
 1700K .......... .......... .......... .......... .......... 58%   64.19 KB/s
 1750K .......... .......... .......... .......... .......... 60%   38.44 KB/s
 1800K .......... .......... .......... .......... .......... 62%   55.26 KB/s
 1850K .......... .......... .......... .......... .......... 63%   49.50 KB/s
 1900K .......... .......... .......... .......... .......... 65%   40.18 KB/s
 1950K .......... .......... .......... .......... .......... 67%   45.67 KB/s
 2000K .......... .......... .......... .......... .......... 68%   50.08 KB/s
 2050K .......... .......... .......... .......... .......... 70%   35.07 KB/s
 2100K .......... .......... .......... .......... .......... 72%   39.49 KB/s
 2150K .......... .......... .......... .......... .......... 73%   47.99 KB/s
 2200K .......... .......... .......... .......... .......... 75%   33.23 KB/s
 2250K .......... .......... .......... .......... .......... 77%   47.03 KB/s
 2300K .......... .......... .......... .......... .......... 79%   47.20 KB/s
 2350K .......... .......... .......... .......... .......... 80%   38.49 KB/s
 2400K .......... .......... .......... .......... .......... 82%   37.85 KB/s
 2450K .......... .......... .......... .......... .......... 84%   33.09 KB/s
 2500K .......... .......... .......... .......... .......... 85%   44.86 KB/s
 2550K .......... .......... .......... .......... .......... 87%   46.24 KB/s
 2600K .......... .......... .......... .......... .......... 89%   32.29 KB/s
 2650K .......... .......... .......... .......... .......... 90%   46.13 KB/s
 2700K .......... .......... .......... .......... .......... 92%   46.91 KB/s
 2750K .......... .......... .......... .......... .......... 94%   38.45 KB/s
 2800K .......... .......... .......... .......... .......... 95%   49.17 KB/s
 2850K .......... .......... .......... .......... .......... 97%   39.70 KB/s
 2900K .......... .......... .......... .......... .......... 99%   55.83 KB/s
 2950K .......... .......... ...                             100%   37.76 KB/s

16:24:25 (40.37 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


---

### Post by gandaran on 2008-09-17
you must be using the live ubuntu 7.10 cd, correct?
the link for installing adobe flash in gutsy 7.10 is broken, try running the synaptic update command **sudo apt-get update** (remove the flashplugin-nonfree first, must be a complete removal or you'll land up installing the same broken package again) run the update command, then you can reinstall.
note: I don't really know if this works using the live cd, try it, if it doesn't you'll have to download direct from adobe.

---

