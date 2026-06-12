---
title: "No access to 'nvidia-settings'  for install"
date: 2006-03-01
forum: Multimedia &amp; Video
---

### Post by dave_567 on 2006-03-01
I'm a newbe so I'm missing something simple I hope....:mrgreen: 

I can't find the nvidia-settings package in the Synaptic Package Manager.   I have  performed an update and got the nvidia-glx to install.  Possible problems that I can think of are with the video card (G-Force FX 5700 LE (AGP 8x))  Do I need a different driver.  It was not lilsted directly on the legacy video cards but I could be missing something.  Below is the terminal output that I performed trying to install the driver.  

Any help on this one???      


dave@ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Fetched 1B in 2s (0B/s)
Reading package lists... Done
dave@ubuntu:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@ubuntu:~$ sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree... Done
Package nvidia-settings is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-settings has no installation candidate
dave@ubuntu:~$

---

### Post by dave_567 on 2006-03-01
Ohhh.  The reason for the post is that I can not get to my higher resolutions. I'm stuck in SVGA.  I'd like to get up higher.

---

### Post by dave_567 on 2006-03-01
Well I figured out how to finish the nvidia settings.  After the install I'm still stuck in svga.  Any Idea on how to get to the higher resolutions of this vidio card?  :confused:

---

### Post by Aewheros on 2006-03-02
This is just a guess, but I suppose you are trying to increase your screen resoulution via the menus, right? The resolutions displayed there are the ones  enabled in the xorg configuration.

To add additional resolutions run:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or go through the whole wizard by leaving out -phigh:
(If you don't know what to select/type, just go by the default/autodetect by pressing enter without changing anything.)```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dave_567 on 2006-03-11
It worked!!!!  Thanks for the information.   

There is a down side.  The video card went into a very high resolution and it blew the monitor.   :-( 

It took some time to relize that the black screen of death on the system was not a motherboard issue but a monitor problem.  So everyone out there should take it slow and not just set it to the highest resolution at first.

---

