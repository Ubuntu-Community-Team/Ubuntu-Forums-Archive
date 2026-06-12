---
title: "Wireless possible with command line only install?"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by rodreegez on 2009-11-16
Hello. 

I have a reall small Eee PC 701 2g surf. It's small. Really small. So small in fact that I couldn't fit a full install of Ubuntu Karmic on it. So I've would up with a GUI-less install from the mini .iso 

I really like it! All Ubuntu, no distractions. The only thing is I can't seem to get it to connect wire the wireless card. I'm not even sure how to go about it without network manager smoothing the way. 

Is it possible? Would I be able to run some magic command to look for and connect to available networks? Or am I insane and / or entering a world of pain?

Any help appreciated, 

Adam.

EDIT: 
* Following this guide I have tried installing the ath5k driver (using 'linux-backports-modules-karmic-generic package')
>> [https://help.ubuntu.com/community/EeePC/Fixes#Wireless](https://help.ubuntu.com/community/EeePC/Fixes#Wireless)

* Following this guide I have installed wireless-tools. Now, when I run 'iwlist wlan0 scanning' I get 'wlan0    Failed to read scan data : Network is down' 
>> [http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

* Judging by this post the above driver fix did not work.
>> [http://ubuntuforums.org/showthread.php?t=318725](http://ubuntuforums.org/showthread.php?t=318725)

EDIT 2: 
* After rebooting, when I run 'iwlist wlan0 scanning' I get 'wlan0    No scan results'. A new fail is a good fail.

Edit 3:
* Getting there! (sorry if this is getting annoying).
>> [http://ubuntuforums.org/showthread.php?t=1126372](http://ubuntuforums.org/showthread.php?t=1126372)

---

### Post by utc271 on 2009-11-16
[http://nixcraft.com/ubuntu-debian/12...em-ubuntu.htm]("http://nixcraft.com/ubuntu-debian/12020-usb-modem-ubuntu.html")l    ...try this thread..it has helped me

---

