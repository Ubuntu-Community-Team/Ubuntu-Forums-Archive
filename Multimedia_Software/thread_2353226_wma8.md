---
title: "wma8"
date: 2017-02-20
forum: Multimedia Software
---

### Post by christon74 on 2017-02-20
Good morning fellow ubunters :)
I'm dead sure this has been already discussed and I am not the first one to encounter this problem. Rhythmbox once used to play wma files but for some reason it no longer will. Each and every time I try to play them I get the following notice:

Required plugin could not be found

Rhythmbox requires to install plugins to play media files of the following type: Windows Media Audio 8 decoder

Have a nice Monday.

---

### Post by mc4man on 2017-02-20
Decoded by gstreamer1.0-libav & atm that plugin is broken in 16.04, I reported & a fix has been done but not yet released. You can get the new package from the -proposed repo or wait a bit for it to make the main repos, likely this week

Bug for reference - [https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842](https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842)

The new package version is 1.8.3-1ubuntu0.2

Otherwise instead of enabling -proposed or waiting  just go here, pick your arch to download the .deb. 
[https://www.ubuntuupdates.org/package/core/xenial/universe/proposed/gstreamer1.0-libav](https://www.ubuntuupdates.org/package/core/xenial/universe/proposed/gstreamer1.0-libav) 
Then install the downloaded .deb with apt, example here with 64 bit, downloaded to ~/Downloads, 
 > sudo apt install ./Downloads/gstreamer1.0-libav_1.8.3-1ubuntu0.2_amd64.deb

---

### Post by christon74 on 2017-02-20
Thank you mc4man :) 
I've just tried the line command and it says this:
Reading package lists... Done
E: Unsupported file ./Downloads/gstreamer1.0-libav_1.8.3-1ubuntu0.2_amd64.deb given on commandline
root@hp1:/home/christophe# 

I guess I am with 32 bits and not 64

---

### Post by Yellow Pasque on 2017-02-20
> **christon74 said:**
> I guess I am with 32 bits and not 64

Then use the i386 version: [http://security.ubuntu.com/ubuntu/pool/universe/g/gst-libav1.0/gstreamer1.0-libav_1.8.3-1ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/g/gst-libav1.0/gstreamer1.0-libav_1.8.3-1ubuntu0.2_i386.deb)

..or just wait for it to come through the official repo if you can't figure it and/or don't feel comfortable using a proposed package.

---

