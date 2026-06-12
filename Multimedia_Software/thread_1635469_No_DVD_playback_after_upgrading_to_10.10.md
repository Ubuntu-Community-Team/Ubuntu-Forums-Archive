---
title: "No DVD playback after upgrading to 10.10"
date: 2010-12-01
forum: Multimedia Software
---

### Post by tinker123 on 2010-12-01
Hi;

I upgraded from Ubuntu 10.04 to 10.10.

I could play a particular DVD in totem without any problems immediately before the upgrade.  Immediately after the upgrade I could not play that particular DVD.  I got the error message below

> 
~$ totem
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: KUNG_FU_SEASON_3
libdvdnav: DVD Serial Number: 32b8976c
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/steve/.dvdnav/KUNG_FU_SEASON_3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f00000. Regions: 1 2 3 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000036f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000007d8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002fd96d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002fe963
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
**libdvdnav: Suspected RCE Region Protection!!!**


- other DVDs from the same box set ( for US & Canada ) get the same error messages from totem 

- I was able to play another DVD with totem, but with *SLIGHTLY* choppy and grainy video playback.  I am pretty sure I have DMA enabled.

- Totem played an *.avi file I had on my hard drive just fine

- Youtube videos work just fine

- I ran regionset, my dvd player is set to region 1, as appropriate, as I am in the US ( I set it again, no change ).  I reset my DVD player anyway and rebooted.  No change.

- I ran sudo /usr/share/doc/libdvdread4/install-css.sh and rebooted.  No luck.

- I deleted my ~/.dvdcss directory and rebooted.  No luck.

- I installed the VLC, which was able to play the DVD, but Totem still can't.

- I reinstalled totem through synaptic and rebooted.  No change.

- I reset the permission on my dvd player as per instructions
chmod 660 /dev/sr0; chgrp cdrom /dev/sr0

- I reinstalled all of the medibuntu stuff through the Ubuntu software center and rebooted.  No change.

- I went to the medibuntu site and installed all of the software there and rebooted.  No change:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Here are the commands I ran from that sight ( logged in as root ) and the outputs I got:

> 
**Adding The Repository**

[B]root@Wisdom:~# sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-12-04 16:38:46-- [http://www.medibuntu.org/sources.list.d/maverick.list](http://www.medibuntu.org/sources.list.d/maverick.list)[/B]
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 286 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 286 --.-K/s in 0s

2010-12-04 16:38:46 (22.3 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [286/286]

Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x libevent-execflow-perl python-evince libdiscover2 twolame
  dvdrip-utils vcdimager libsvga1 libanyevent-perl libintl-perl libcdt4
  transcode-utils discover kdesudo libasync-interrupt-perl python-gnomedesktop
  libevent-rpc-perl libxcb-shape0 python-metacity netpbm python-mediaprofiles
  libgvc5 python-bugbuddy python-totem-plparser libxdot4 libmagickcore3-extra
  libevent-perl python-evolution libvdpau1 libnetpbm10 update-manager-kde
  imagemagick discover-data libgraph4 libgtk2-ex-formfactory-perl
  libboost-filesystem1.42.0 mkvtoolnix libcommon-sense-perl libpathplan4
  libboost-system1.42.0 python-gtop libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Reading package lists...
root@Wisdom:~#


> 
**root@Wisdom:~# apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu**
Reading package lists... Done
Building dependency tree
Reading state information... Done
app-install-data-medibuntu is already the newest version.
apport-hooks-medibuntu is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x libevent-execflow-perl python-evince libdiscover2 twolame
  dvdrip-utils vcdimager libsvga1 libanyevent-perl libintl-perl libcdt4
  transcode-utils discover kdesudo libasync-interrupt-perl python-gnomedesktop
  libevent-rpc-perl libxcb-shape0 python-metacity netpbm python-mediaprofiles
  libgvc5 python-bugbuddy python-totem-plparser libxdot4 libmagickcore3-extra
  libevent-perl python-evolution libvdpau1 libnetpbm10 update-manager-kde
  imagemagick discover-data libgraph4 libgtk2-ex-formfactory-perl
  libboost-filesystem1.42.0 mkvtoolnix libcommon-sense-perl libpathplan4
  libboost-system1.42.0 python-gtop libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@Wisdom:~#







> 
**root@Wisdom:~# apt-get install libdvdcss2**
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdcss2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x libevent-execflow-perl python-evince libdiscover2 twolame
  dvdrip-utils vcdimager libsvga1 libanyevent-perl libintl-perl libcdt4
  transcode-utils discover kdesudo libasync-interrupt-perl python-gnomedesktop
  libevent-rpc-perl libxcb-shape0 python-metacity netpbm python-mediaprofiles
  libgvc5 python-bugbuddy python-totem-plparser libxdot4 libmagickcore3-extra
  libevent-perl python-evolution libvdpau1 libnetpbm10 update-manager-kde
  imagemagick discover-data libgraph4 libgtk2-ex-formfactory-perl
  libboost-filesystem1.42.0 mkvtoolnix libcommon-sense-perl libpathplan4
  libboost-system1.42.0 python-gtop libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@Wisdom:~#



> 
**root@Wisdom:~# apt-get install w32codecs**
Reading package lists... Done
Building dependency tree
Reading state information... Done
w32codecs is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x libevent-execflow-perl python-evince libdiscover2 twolame
  dvdrip-utils vcdimager libsvga1 libanyevent-perl libintl-perl libcdt4
  transcode-utils discover kdesudo libasync-interrupt-perl python-gnomedesktop
  libevent-rpc-perl libxcb-shape0 python-metacity netpbm python-mediaprofiles
  libgvc5 python-bugbuddy python-totem-plparser libxdot4 libmagickcore3-extra
  libevent-perl python-evolution libvdpau1 libnetpbm10 update-manager-kde
  imagemagick discover-data libgraph4 libgtk2-ex-formfactory-perl
  libboost-filesystem1.42.0 mkvtoolnix libcommon-sense-perl libpathplan4
  libboost-system1.42.0 python-gtop libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@Wisdom:~#


> 

**root@Wisdom:~#  sudo apt-get install libdvdread4**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x libevent-execflow-perl python-evince libdiscover2 twolame
  dvdrip-utils vcdimager libsvga1 libanyevent-perl libintl-perl libcdt4
  transcode-utils discover kdesudo libasync-interrupt-perl python-gnomedesktop
  libevent-rpc-perl libxcb-shape0 python-metacity netpbm python-mediaprofiles
  libgvc5 python-bugbuddy python-totem-plparser libxdot4 libmagickcore3-extra
  libevent-perl python-evolution libvdpau1 libnetpbm10 update-manager-kde
  imagemagick discover-data libgraph4 libgtk2-ex-formfactory-perl
  libboost-filesystem1.42.0 mkvtoolnix libcommon-sense-perl libpathplan4
  libboost-system1.42.0 python-gtop libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@Wisdom:~# 



> 
**root@Wisdom:~# /usr/share/doc/libdvdread4/install-css.sh**
--2010-12-06 14:56:34--  [http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages](http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8065 (7.9K) [text/plain]
Saving to: `/tmp/dvdcss-CNCUtv/Packages'

100%[======================================>] 8,065       --.-K/s   in 0.1s    

2010-12-06 14:56:35 (66.8 KB/s) - `/tmp/dvdcss-CNCUtv/Packages' saved [8065/8065]

--2010-12-06 14:56:35--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-CNCUtv/libdvdcss.deb'

100%[======================================>] 38,036       106K/s   in 0.3s    

2010-12-06 14:56:36 (106 KB/s) - `/tmp/dvdcss-CNCUtv/libdvdcss.deb' saved [38036/38036]

(Reading database ... 330621 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-CNCUtv/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@Wisdom:~# 




> 
**root@Wisdom:~# apt-cache policy ubuntu-restricted-extras**
ubuntu-restricted-extras:
  Installed: 42
  Candidate: 42
  Version table:
 *** 42 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse i386 Packages
        100 /var/lib/dpkg/status
root@Wisdom:~# 


---

### Post by gordintoronto on 2010-12-02
Open accessories/terminal and paste this in:
sudo /usr/share/doc/libdvdread4/install-css.sh

If the file is not found, use synaptic to install libdvdread4 and try again.

You probably need to reboot.

---

### Post by tinker123 on 2010-12-02
Moderators please delete this post.  Thank You

---

### Post by tinker123 on 2010-12-03
Moderators please delete this post.  Thank You

---

