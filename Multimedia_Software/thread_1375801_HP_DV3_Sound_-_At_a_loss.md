---
title: "HP DV3 Sound - At a loss"
date: 2010-01-08
forum: Multimedia Software
---

### Post by TyCowboy on 2010-01-08
I will be the first to admit, I am giving Ubuntu a try.  I have always been a Windows guy (it's what I migrated to for business reasons early in my career).  Either way, when a Win7 from Vista upgrade bricked my laptop, I figured why not.

I downloaded 9.10/Karmic and installed it with no issues.  After a little hiccup with wireless (fixed easily) because I'm using a broadcom wireless adapter, I noticed something...no sound.

I have tried, at this point, just about every solution proposed, and I'm obviously doing something wrong or I am so Ubuntu ignorant that I just don't know what I'm doing wrong.

Could really use some help, but I have no idea what information I would need to put in here to have anyone steer me in the right direction.

I used the comprehensive guide stickied to the top, and I can confirm that I had success, it does show my drivers:

tyler@Tyler:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Yet I get no sound.  Nothing.  I have checked alsamixer, and everything appears to be set up properly, but I still get no sound.  Nothing at bootup, nothing when I attempt to play a music file, load a video file, nothing in youtube, nada.

And to clarify, I get nothing out of the headset jack either, so there's just - well, no sound.

Thanks in advance.
Ty

---

### Post by lidex on 2010-01-09
Run these commands in a terminal:
```
sudo apt-get remove sl-modem-daemon
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

One at a time please. Then **Reboot**


Next try upgrading your alsa drivers here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

