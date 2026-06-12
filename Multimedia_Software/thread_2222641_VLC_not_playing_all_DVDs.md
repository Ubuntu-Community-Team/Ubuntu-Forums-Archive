---
title: "VLC not playing all DVDs"
date: 2014-05-07
forum: Multimedia Software
---

### Post by SuperFreak on 2014-05-07
Not sure how to get VLC to play all DVDs as some don't work. here is what I tried

```
david@MainSqueeze:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 unrar
Recommended packages:
  libavcodec-extra-53
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.1-0
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 ubuntu-restricted-extras unrar
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 395 kB of archives.
After this operation, 1,175 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ trusty/multiverse libfaac0 amd64 1.28-6 [35.8 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe libmjpegutils-2.1-0 amd64 1:2.1.0+debian-2.1 [23.8 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe libmpeg2encpp-2.1-0 amd64 1:2.1.0+debian-2.1 [70.2 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe libmplex2-2.1-0 amd64 1:2.1.0+debian-2.1 [43.5 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ trusty/multiverse gstreamer0.10-plugins-bad-multiverse amd64 0.10.21-1ubuntu3 [83.1 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ trusty/multiverse ubuntu-restricted-extras amd64 60 [2,902 B]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ trusty/multiverse unrar amd64 1:5.0.10-1 [136 kB]
Fetched 395 kB in 3s (102 kB/s)
Selecting previously unselected package libfaac0:amd64.
(Reading database ... 209300 files and directories currently installed.)
Preparing to unpack .../libfaac0_1.28-6_amd64.deb ...
Unpacking libfaac0:amd64 (1.28-6) ...
Selecting previously unselected package libmjpegutils-2.1-0.
Preparing to unpack .../libmjpegutils-2.1-0_1%3a2.1.0+debian-2.1_amd64.deb ...
Unpacking libmjpegutils-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package libmpeg2encpp-2.1-0.
Preparing to unpack .../libmpeg2encpp-2.1-0_1%3a2.1.0+debian-2.1_amd64.deb ...
Unpacking libmpeg2encpp-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package libmplex2-2.1-0.
Preparing to unpack .../libmplex2-2.1-0_1%3a2.1.0+debian-2.1_amd64.deb ...
Unpacking libmplex2-2.1-0 (1:2.1.0+debian-2.1) ...
Selecting previously unselected package gstreamer0.10-plugins-bad-multiverse.
Preparing to unpack .../gstreamer0.10-plugins-bad-multiverse_0.10.21-1ubuntu3_amd64.deb ...
Unpacking gstreamer0.10-plugins-bad-multiverse (0.10.21-1ubuntu3) ...
Selecting previously unselected package ubuntu-restricted-extras.
Preparing to unpack .../ubuntu-restricted-extras_60_amd64.deb ...
Unpacking ubuntu-restricted-extras (60) ...
Selecting previously unselected package unrar.
Preparing to unpack .../unrar_1%3a5.0.10-1_amd64.deb ...
Unpacking unrar (1:5.0.10-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libfaac0:amd64 (1.28-6) ...
Setting up libmjpegutils-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up libmpeg2encpp-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up libmplex2-2.1-0 (1:2.1.0+debian-2.1) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.21-1ubuntu3) ...
Setting up ubuntu-restricted-extras (60) ...
Setting up unrar (1:5.0.10-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode
Processing triggers for libc-bin (2.19-0ubuntu6) ...
david@MainSqueeze:~$ sudo apt-get install libdvdcss2 libdvdnav4 libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdnav4 is already the newest version.
libdvdread4 is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@MainSqueeze:~$ sudo apt-get install libavformat-extra-53 libavcodec-extra-53 libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec-extra-53 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libav-tools:i386 libav-tools

Package libavformat-extra-53 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libavformat-extra-53' has no installation candidate
E: Package 'libavcodec-extra-53' has no installation candidate
david@MainSqueeze:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2014-05-07 12:26:21--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [text/plain]
Saving to: ‘/tmp/dvdcss-XcpbMN/Packages’

100%[======================================>] 3,520       --.-K/s   in 0.1s    

2014-05-07 12:26:21 (23.4 KB/s) - ‘/tmp/dvdcss-XcpbMN/Packages’ saved [3520/3520]

--2014-05-07 12:26:21--  http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44462 (43K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-XcpbMN/libdvdcss.deb’

100%[======================================>] 44,462      91.1KB/s   in 0.5s   

2014-05-07 12:26:22 (91.1 KB/s) - ‘/tmp/dvdcss-XcpbMN/libdvdcss.deb’ saved [44462/44462]

(Reading database ... 209340 files and directories currently installed.)
Preparing to unpack .../dvdcss-XcpbMN/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
david@MainSqueeze:~$ 

```

---

### Post by dmbNCSU on 2014-05-07
Are some of your DVD's from different regions? i.e. NTSC (USA) or PAL (Europe), although I am not sure why that would matter with VLC, pretty sure it plays everything.

---

### Post by SuperFreak on 2014-05-07
I thinkl it's all NTSC (USA)

---

### Post by mezuss on 2014-10-03
In case you or anyone still has that NTSC problem....here's a very good read: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

