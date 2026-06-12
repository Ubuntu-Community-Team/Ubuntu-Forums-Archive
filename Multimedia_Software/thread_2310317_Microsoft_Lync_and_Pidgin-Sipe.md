---
title: "Microsoft Lync and Pidgin-Sipe"
date: 2016-01-18
forum: Multimedia Software
---

### Post by Constantinopolitan on 2016-01-18
Dear all,

I've been convoked to a team meeting via Microsoft Lync web app, but that application is incompatible with Linux. The first page shamelessly says "you can optimise your experience if using a compatible operating system and browser", which is another wording for "Linux users not admitted". 

So I browsed the Internet and found that apparently you can worm your way in using Pidgin-SIPE. I tried to get and install it, but nothing worked. Here are the terminal records:
"constantinopolitana@Constantinopolitana:~$ sudo apt-get install pidgin-sipe
[sudo] password for constantinopolitana: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freeciv-data freeciv-server libart-2.0-2 libcdr-0.0-0 libevdev2
  libhsqldb1.8.0-java libllvm3.5 liblua5.1-0 libmspub-0.0-0 liborcus-0.6-0
  libservlet3.0-java libvisio-0.0-0 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-31
  linux-headers-3.16.0-31-generic linux-headers-3.16.0-43
  linux-headers-3.16.0-43-generic linux-image-3.16.0-30-generic
  linux-image-3.16.0-31-generic linux-image-3.16.0-43-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-31-generic
  linux-image-extra-3.16.0-43-generic python-imaging python-pexpect python-pil
  python-renderpm python-reportlab python-reportlab-accel
Use 'apt-get autoremove' to remove them.
Recommended packages:
  gstreamer0.10-ffmpeg
The following NEW packages will be installed:
  pidgin-sipe
0 upgraded, 1 newly installed, 0 to remove and 43 not upgraded.
Need to get 252 kB of archives.
After this operation, 1187 kB of additional disk space will be used.
Get:1 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) trusty/universe pidgin-sipe i386 1.17.3-1 [252 kB]
Fetched 252 kB in 3s (63.1 kB/s)      
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "es:tr:de:fr:en",
        LC_ALL = (unset),
        LC_TIME = "es_BE.UTF-8",
        LC_MONETARY = "es_BE.UTF-8",
        LC_ADDRESS = "es_BE.UTF-8",
        LC_TELEPHONE = "es_BE.UTF-8",
        LC_NAME = "es_BE.UTF-8",
        LC_MEASUREMENT = "es_BE.UTF-8",
        LC_IDENTIFICATION = "es_BE.UTF-8",
        LC_NUMERIC = "es_BE.UTF-8",
        LC_PAPER = "es_BE.UTF-8",
        LANG = "es_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package pidgin-sipe.
(Reading database ... 326798 files and directories currently installed.)
Preparing to unpack .../pidgin-sipe_1.17.3-1_i386.deb ...
Adding 'diversion of /usr/bin/pidgin to /usr/bin/pidgin.orig by pidgin-sipe'
Unpacking pidgin-sipe (1.17.3-1) ...
Setting up pidgin-sipe (1.17.3-1) ...
constantinopolitana@Constantinopolitana:~$ sudo apt-get -f install^C
constantinopolitana@Constantinopolitana:~$ "

Blabla.
What means all this stuff about "locale settings"?
And then, once I got it installed, how to proceed for getting to Lync? 

Thanks already A LOT for any help you can provide!

Best regards,

Eva

---

