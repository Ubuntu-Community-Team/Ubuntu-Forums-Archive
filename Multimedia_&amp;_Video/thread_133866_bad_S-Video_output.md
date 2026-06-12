---
title: "bad S-Video output"
date: 2006-02-20
forum: Multimedia &amp; Video
---

### Post by FleetwoodMan1968 on 2006-02-20
I posted on the other s-video thread and got no response so I'll post my own new one here.  i?m running a 9200 SE ati card but the s-video is in bad shape when ubuntu boots up, the load screen and mem check is all ok.  When i treyd what was posted on there i got this...........

brett@brettmedia:~$ sudo apt-get install linux-restricted-modules-i686-GNU-linux -xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules-i686-GNU-linux-xorg-driver-fgl rx
brett@brettmedia:~$ sudo apt-get install linux-restricted-modules-2.6.10-5-386 x org-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.10-5-386 is already the newest version.
The following NEW packages will be installed:
xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 3185kB of archives.
After unpacking 10.2MB of additional disk space will be used.
0% [Connecting to security.ubuntu.com (1.0.0.0)]
0% [Connecting to security.ubuntu.com (1.0.0.0)]^[[3~
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted xorg-driver-fglrx 6.8.0 -8.8.25-0ubuntu11.1
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/po...l/linux-restri](http://security.ubuntu.com/ubuntu/po...l/linux-restri) cted-modules-2.6.10/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11.1_i386.deb Could n ot connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

am i doing something wrong?????  Please advise on what else i can do to make this work, i'm starting to get a bit flustered because i cann't use ati's drivers either and i'm running out of options.  Tanx

---

