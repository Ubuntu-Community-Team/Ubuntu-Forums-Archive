---
title: "i855 chipset runs Google Earth"
date: 2014-01-07
forum: Multimedia Software
---

### Post by Handssolow on 2014-01-07
Background
Getting a Toshiba Satellite M35X-S114 working was not without problems as described below earlier. Booting with nomodeset then using the Glasen PPA Intel driver 855gm-fix-dkms package gave a working system. The issue is the i855 and similar graphics chipsets, found on my and others by now rather dated laptops.
[here](http://ubuntuforums.org/showthread.php?t=1699341&highlight=855)

Upgraded to 12.04 and Google Earth stopped working, crashing after about 10 seconds. The regular Ubuntu updates continued to throw up error messages about the 855gm-fix-dkms package, it being third party software etc. Running any version of Google Earth again on my laptop seemed unlikely. 

My thanks go to [Saurav Kumar](http://askubuntu.com/questions/336531/ubuntu-12-04-2-with-intel-i845-graphics-becomes-sluggish-after-few-minutes-of-sy) on askubuntu.com for his posting in August 2013 reporting his experiences of moving to the Raring Ringtail kernel.

 

In Synaptic I installed-
linux-generic-lts-raring (3.8.0.35.35) 
linux-headers-3.8.0-35 (3.8.0-35.50~precise1) 
linux-headers-3.8.0-35-generic (3.8.0-35.50~precise1) 
linux-headers-generic-lts-raring (3.8.0.35.35)
linux-image-3.8.0-35-generic (3.8.0-35.50~precise1) 
linux-image-generic-lts-raring (3.8.0.35.35)

Remove Glasen PPA and Authentication Key.
Remove 855gm-fix-dkms package (this process took several minutes here)

reboot

In the terminal install
sudo apt-get install libgl1-mesa-dri-lts-raring libxatracker1-lts-raring xserver-xorg-core-lts-raring xserver-xorg-input-all-lts-raring xserver-xorg-input-evdev-lts-raring xserver-xorg-input-mouse-lts-raring xserver-xorg-input-synaptics-lts-raring xserver-xorg-input-vmmouse-lts-raring xserver-xorg-input-wacom-lts-raring xserver-xorg-lts-raring xserver-xorg-video-all-lts-raring xserver-xorg-video-ati-lts-raring xserver-xorg-video-cirrus-lts-raring xserver-xorg-video-fbdev-lts-raring xserver-xorg-video-intel-lts-raring xserver-xorg-video-mach64-lts-raring xserver-xorg-video-mga-lts-raring xserver-xorg-video-modesetting-lts-raring xserver-xorg-video-neomagic-lts-raring xserver-xorg-video-nouveau-lts-raring xserver-xorg-video-openchrome-lts-raring xserver-xorg-video-r128-lts-raring xserver-xorg-video-radeon-lts-raring xserver-xorg-video-s3-lts-raring xserver-xorg-video-savage-lts-raring xserver-xorg-video-siliconmotion-lts-raring xserver-xorg-video-sis-lts-raring xserver-xorg-video-sisusb-lts-raring xserver-xorg-video-tdfx-lts-raring xserver-xorg-video-trident-lts-raring xserver-xorg-video-vesa-lts-raring xserver-xorg-video-vmware-lts-raring libxrandr-ltsq2 x11-xserver-utils-lts-raring xserver-common-lts-raring 

reboot

I can run Google Earth 6.0.3.2197. The fonts aren't the best but the panoramio pictures are displayed unlike on my desktop with GE 7.1.1

DVDs plays OK as does DVB-T under Kaffeine
There's life in an old laptop still.

Edit: For reasons I don't understand the Google Earth Search feature here works, some still using GE6 lost this feature and have to update or delete lib.so.4. Currently with GE7 the search fuction works but you're likely to have no panoramio pictures. I will post elsewhere on the Forum my experiences with libcurl etc. on my others PCs.

---

### Post by mörgæs on 2014-01-08
Thanks for posting.
If you mark the thread "solved" there's a better chance that people find your advice.

---

