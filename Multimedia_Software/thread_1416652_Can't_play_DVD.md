---
title: "Can't play DVD"
date: 2010-02-26
forum: Multimedia Software
---

### Post by Cnaeus on 2010-02-26
Hi! The problem is, that for some reason no copy protected DVD s are playing. No VLC, no Totem works, and its quite annoying that my original DVDs cannot be played... :( Every audio/video formats woks fine, but some newer DVDs with copy protection are unreadable. Do you have any clues what causes this? Plz help
Thank you very much! :)

---

### Post by puskax on 2010-02-26
I did this and it works

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

It works in ubuntu 9.04

If you have another distribution try the oficial help 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

I hope it works for you

---

### Post by Sodear on 2010-02-26
I followed your instructions exactly but I still cannot play some DVD's: need some more plug ins, specifically gstreamer plugins base: but cannot find them except as a download file in GStreamer - not ready for that yet without some guidance.  Here is what I got after following your instructions:  am using 9.1 karmic koala

sudhir@Sudhir-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudhir@Sudhir-desktop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2010-02-26 14:09:09--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36812 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-5sqvHQ/libdvdcss.deb'

100%[======================================>] 36,812       107K/s   in 0.3s    

2010-02-26 14:09:10 (107 KB/s) - `/tmp/dvdcss-5sqvHQ/libdvdcss.deb' saved [36812/36812]

dpkg: warning: downgrading libdvdcss2 from 1.2.10-0.3medibuntu1 to 1.2.10-0.2medibuntu1.
(Reading database ... 180721 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-5sqvHQ/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sudhir@Sudhir-desktop:~$

---

### Post by ratcheer on 2010-02-26
Make sure you have libdvdcss2 installed.

Tim

---

### Post by efflandt on 2010-02-26
I never have been able to play DVD's properly with totem.  Depending upon which mutually exclusive gstreamer modules I have (installing one removes the other), I either have no sound, or I have sound, and no DVD menu access.

But vlc works fine.

---

### Post by natachinha on 2010-03-13
> **puskax said:**
> I did this and it works

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

It works in ubuntu 9.04

If you have another distribution try the oficial help 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

I hope it works for you

Dude! You're awesome!!! I searched everywhere, tried everything and nothing helped. Your solution got it working! Thank you so much!

---

### Post by wolvenfamily on 2010-12-08
> **puskax said:**
> I did this and it works

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

It works in ubuntu 9.04

If you have another distribution try the oficial help 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

I hope it works for you

Yes, thank you.....after kissing off my m$ pc, and enjoying my android phone (i am guessing it is based on linux), my wife got me a new dell vostro with ubuntu on it, i was having a heck of a time trying to get dvd's to play...you saved this newbie alot of headaches :D ACES!!

---

