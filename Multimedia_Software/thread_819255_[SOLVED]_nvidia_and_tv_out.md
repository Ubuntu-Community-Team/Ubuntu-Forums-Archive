---
title: "[SOLVED] nvidia and tv out"
date: 2008-06-05
forum: Multimedia Software
---

### Post by stoppage on 2008-06-05
Hi, I'm running Ubuntu „Feisty“ with an Nvidia GeForce2 MX400 graphics card. To use my TV out I installed the „legacy“ driver from Synaptec and, lo and behold, resolution choices went down to the lowest choices of two, around 640x480. This is all before I come to the magnificent „Xorg.config“..... 
Only Linux could manage to make the configuration of TV out a half-way-'round-the-world-adventure playhouse. Could somebody  help me out here please, I've been tinkering around in the forum wilderness for the last seven hours. Any assistance very much appreciated

---

### Post by pedro_orange on 2008-06-05
Maybe enabling a different set of drivers restricted your choice of resolutions as a default.
However, perhaps if you ran a:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And chose some relevant resolutions you may be able to sort that aspect of it. It may be of note you should do the whole ALT+CTRL+F2 thing to be in a different shell before u start the command. Otherwise u have to worry about stopping X and all that jazz.

---

### Post by aeiah on 2008-06-05
does nvidia-settings give you anything useful?

---

### Post by aeiah on 2008-06-05
and what connection are you using? s-video, component, composite, hdmi? are you hoping to have a different resolution on your monitor than on your tv or are you just wanting to use it with your tv, with no monitor?

---

### Post by stoppage on 2008-06-06
sudo dpkg-reconfigure -phigh xserver-xorg allows me to choose resolution of 1280x1024 but I need previous res.of 1440x900
nvidia-settings returns...

$ nvidia-settings



ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required

       version is 1.9.



ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

and a GUI with no configurables. 

I'm optimistically hoping to use „Twin View“ cloned same res. on monitor and TV using "comp" connection
Included is sample from xorg.conf

---

### Post by stoppage on 2008-07-19
Solved! To anybody with a similar problem....
I used &#8222;Nvtv TVOut&#8220; available in Synaptec, I think it's more suitable to older graphic cards. This line entered in &#8222;xorg.conf&#8220; under &#8222;Monitor&#8220; brings back 1440x900 res....
# 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync

I used a low resolution 800x600 for proper video display on TV. It's probably not optimum config., but attached is copy of my xorg.conf in all its majesty. Some values you'll obviously need to change. Happy configuring, what a nightmare!

---

