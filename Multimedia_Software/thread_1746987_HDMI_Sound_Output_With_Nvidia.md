---
title: "HDMI Sound Output With Nvidia?"
date: 2011-05-02
forum: Multimedia Software
---

### Post by Nerotriple6 on 2011-05-02
So I try to make my friends see the light ...but they do not hear it. :P:P:P

In other words, I made a friend use Natty but couldn't enable sound through his HDMI. He has video, but no audio (through HDMI, laptop speakers works fine). In his sound preferences I did not see HDMI audio as an option and I tried Google-searching and video driver fiddling but all I came up with are Nvidia users saying the same thing. No audio..

Can I make him hear the light (so to speak:P) with his 8600M GS?

---

### Post by Nerotriple6 on 2011-05-03
Bump. :)

---

### Post by tjones00 on 2011-05-03
Haven't been able to test 11.04 with nvidia hdmi audio myself. I don't see a lot of posts here regarding it. Perhaps the methods used for 10.10 and 10.04 still work.

1) make sure you have the nvidia proprietary drivers installed.
2) make sure you're using alsa 1.0.23+ or a 2.6.35+ kernel (natty is 2.6.38)
3) discover which device on the card is responsible for audio.
4) direct audio to that device.

[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

---

### Post by Nerotriple6 on 2011-05-03
> Although this information is present in this forum in bits and pieces a new nvidia hdmi audio thread pops up every couple days. 

LOL ...sorry.. :p:p

But thanks for posting the link. Many, many thanks. :D
I will call him tomorrow.

---

### Post by tjones00 on 2011-05-03
No problem. Hope he gets it sorted out.

---

### Post by Nerotriple6 on 2011-05-05
Thanks again. I can't get it working though..
Aditional drivers tool says the driver is activated but not in use..
Xorg.conf says:
> 
Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection



I've updated Alsa but HDMI still doesn't show on aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
grep eld_valid /proc/asound/NVidia/eld*
```There is no Nvidia folder in /proc/asound/
```
bjornar@ubuntu:~$ uname -r
2.6.38-8-generic
bjornar@ubuntu:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
```What's wrong? I did the steps in the Terminal here: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Help please. :(

---

### Post by Nerotriple6 on 2011-05-07
Alright, so here is the deal. Nvidia drivers for Natty are bugged and as a result the aditional drivers tool says they are installed but not in use, even though they are in use. Launchpad is full of this bug..

I'm happy I have ATI... :D

---

### Post by solitaire on 2011-05-07
Long shot but check the BIOS
i know on my Zotac Nvidia ION board there's an option to switch between AC98(??) audio and HDMI audio pass through...

Try switching to HDMI pass through see if Ubuntu sees it now

---

### Post by Nerotriple6 on 2011-05-08
Acer Aspire didn't have any sound options but worth the try. Thanks anyway.:)

---

### Post by Nerotriple6 on 2011-05-16
My friend asked if I could help him to go back to Maverick until this issue is fixed. It's taking awfully long..

---

