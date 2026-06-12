---
title: "Trouble - lirc;  10.04; 64 bit;  mceusb"
date: 2011-01-09
forum: Mythbuntu
---

### Post by JWB47 on 2011-01-09
I just built a new mythbuntu backend running Ubuntu 10.04.1 LTS 64 bit and MythTV 0.24+fixes. I have a frontend running on the machine for testing purposes.

On this machine, I am unable to get any response from the MCE Remote.

After searching this forum and other sources, I tried the solution discussed in the following thread: [http://ubuntuforums.org/showthread.php?t=1597886&page=1](http://ubuntuforums.org/showthread.php?t=1597886&page=1). This solution did not work on the new backend. I get no response from testing using an irw command. It does, however, work on another PC running the 32 bit version  of the same OS/kernel version.

I  would appreciate any suggestions as to how to get the remote working. My preference is to stay on the LTS version, if at all possible.

Here is detailed information about the problem setup.

```
uname -a
Linux mmbe 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
``````
dpkg -l | grep myth
rc  libmyth-0.23-0                        0.24.0~trunk26882-0ubuntu0~mythbuntu1              Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                        2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                        2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A python library to access some MythTV features
ii  libmythtv-perl                        2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A PERL library to access some MythTV features
ii  mythbrowser                           2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A web browser for MythTV
ii  mythbuntu-common                      0.50-0ubuntu1                                      Mythbuntu application support functions
ii  mythbuntu-control-centre              0.62-0ubuntu1                                      Mythbuntu Configuration Application
ii  mythbuntu-lirc-generator              0.25-0ubuntu1~ppa1                                 Mythbuntu Lirc Configuration Generator
ii  mythbuntu-repos                       8.8-0ubuntu0+mythbuntu~auto20101122003009          Mythbuntu repository installer
ii  mythgallery                           2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Image gallery/slideshow add-on module for MythTV
ii  mythmovies                            1:0.24.0+fixes27204-0ubuntu0+mythbuntu1            Find nearby movies and cinema listings
ii  mythmusic                             2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Music add-on module for MythTV
ii  mythnetvision                         2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A Internet Video Player plugin for MythTV
ii  mythnews                              2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 An RSS feed news reader module for MythTV
ii  mythtv-backend                        2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A personal video recorder application (server)
ii  mythtv-backend-master                 2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Metapackage to setup and configure a "Master Backend" profile of
ii  mythtv-common                         2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A personal video recorder application (common data)
ii  mythtv-database                       2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A personal video recorder application (database)
ii  mythtv-frontend                       2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A personal video recorder application (client)
ii  mythtv-transcode-utils                2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Utilities used for transcoding MythTV tasks
ii  mythvideo                             2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 A generic video player frontend module for MythTV
ii  mythweather                           2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Weather add-on module for MythTV
ii  mythweb                                 2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu1 Web interface add-on module for MythTV

``````
dpkg -l | grep lirc
rc  gnome-lirc-properties                 0.4.0-0ubuntu1                                     Control panel to configure remote controls
ii  liblircclient0                        0.8.6-0ubuntu4.1                                   infra-red remote control support - client library
ii  lirc                                  0.8.6-0ubuntu4.1                                   infra-red remote control support
ii  lirc-modules-source                   0.8.7~pre3-0ubuntu1~janvitus+lucidppa2             infra-red remote control support - kernel modules
ii  mythbuntu-lirc-generator              0.25-0ubuntu1~ppa1 Mythbuntu Lirc Configuration Generator

``````
ps ax | grep lir
11079 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0

``````
lsmod | grep lir
lirc_mceusb            14428  0 
lirc_dev               11788  1 lirc_mceusb

``````
lsusb
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 008: ID 147a:e03e Formosa Industrial Computing, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 2040:7200 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```*NOTE* The Remote is the Formosa 147a:e03e device. It appears to be a HID device, but does not show up in /proc/bus/input/devices.

Thanks for your help.

John

---

