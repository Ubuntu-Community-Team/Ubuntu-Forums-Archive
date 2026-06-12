---
title: "Possible video tearing solution???"
date: 2009-11-29
forum: Multimedia Software
---

### Post by urbanus on 2009-11-29
[SIZE=4]**Motivation & revelation**[/SIZE]

Lets just admit it right away! 3D acceleration and video tearing is a big pain in the behind. If you use the Open Source video drivers with ATI and Nvidia cards, you "loose" 3D rendering (slow and sluggish), I have a HD4870x2, and cant play Open Arena on it with these drivers. If I however use the Closed Source binary drivers from ATI and Nvidia them selfs, you get greater 3D acceleration power, but then Video Tearing a big issue, even noticed it dragging a window with Compiz enabled.

**UPDATE! Check the updates at the end of the guide about ATI. In short, use open source drivers for video tearing free playback and older cards also gets good 3D. Use binary for over/underscan capabilies!**

However, when installing Ubuntu 9.10 on my old computer, former Media Centre PC, retired because of instability, resurrected when 2 components and 4 fans where removed and became stable in Ubuntu a bit unexpectedly. I'm using the two components in the "new" Media Centre PC without issues if anyone wondered.

But I really wanted to use the Nvidia GeForce 6800GT fully, so I stared testing an idea I got on how I might be able to solve this. To my surprise it worked better than expected (or I dared to hope). Here is what I did!

**[SIZE=4]Guide[/SIZE]**
1. Install the binary drivers for your video card, Nvidia is what I've tested. Use the "Hardware Drivers" tool in Administration menu or this command:
```
sudo apt-get install nvidia-glx-185
```2. Install the compiz settings manager:
```
sudo apt-get install compizconfig-settings-manager
```3. Note down what's the refresh rate your using:
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138062&stc=1&d=1259540543[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=138062&stc=1&d=1259540543")
PS! It says CRT in the menu, but It is a LCD monitor connected from It's VGA-port to the DVI-port on the video card using an adapter!

4. Enable the Video Blitter setting (A bit unsure about the usefulness of this):
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138063&stc=1&d=1259540543[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=138063&stc=1&d=1259540543")

5. Adjust Compiz "Refresh Rate" and enable "Synch To VBlank":
**UPDATE! It might also be advisable to disable "Detect refresh rate".**
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138064&stc=1&d=1259540543[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=138064&stc=1&d=1259540543")

6. Reboot the machine (restarting X may suffice).


**[SIZE=4]Success(?) and user responses[/SIZE]**

This made my Ubuntu pc much more useful in a painless way. I've tried to do the whole xorg.conf thing many times, but with mixed results to say the least (and a HUGE time waster). This method should work on any Nvidia card in Ubuntu 9.10 at least, but probably other versions and distros as well. If the ATI driver have the same options, it might work there as well. I'm planning on testing this soon.

**UPDATE! The Binary ATI Driver will let you Overscan and Underscan, but it didn't do well when it came to video tearing. Use the open source driver then. (ATI 3850 AGP)**

[B]UPDATE2! Installing Ubuntu 9.10 and Linux Mint 8 on my old Laptop with Ati X600 gave me Compiz and Video Tearing FREE playback out of the box (Open Source default driver). So using older ATI cards works well :-D

UPDATE3! I installed Linux Mint 8 (Ubuntu based distro) on my desktop machine which has a ATI HD4870x2 graphics card. Using the open source driver gave me good video playback, but choppy 3D. Installing the binary ATI 9.11 driver gave me good 3d and Compiz, but video playback with tearing :-( [/B]

But I'm interested to hear from all of you Linux users out there, any distro and video card, if this works for you, or what you did different to get it working. I would like to get a list going on what video cards and distros (I know this is a Ubuntu forum, but still) this works on :D.

Good luck!


PS! I know there might be issues with performance in games because of games and such. But I haven't been able to do a comprehensive test yet.
PPS! Also I'm Norwegian, so my English isn't perfect, be nice ;-)

---

### Post by lidex on 2009-11-29
In CCSM I would uncheck option "detect refresh rate". I ran across a tutorial awhile back that recommended that plus the changes you mention in CCSM. After applying, my video tearing issues were history.

---

### Post by urbanus on 2009-11-29
Noted and added :-)
I did notice that setting, but forgot to test/change it.

---

### Post by Zibex on 2009-11-30
[http://ubuntuforums.org/showpost.php?p=8365753&postcount=4]("http://ubuntuforums.org/showpost.php?p=8365753&postcount=4")

Can you try this?
Does it solve the problem?

---

### Post by Yellow Pasque on 2009-11-30
> If you use the Open Source video drivers with ATI and Nvidia cards, you lose 3D rendering

Not sure about the 4870X2, but most other RadeonHD cards can get 3D in Karmic by installing a 2.6.32 kernel and using the xorg-edgers PPA.

---

### Post by urbanus on 2009-11-30
> [http://ubuntuforums.org/showpost.php...53&postcount=4](http://ubuntuforums.org/showpost.php...53&postcount=4)

Can you try this?
Does it solve the problem?
I didn't really notice any difference wathing a video with or without the Benchmark using the settings I have in my guide. But then again I get smooth video with them, so I don't need further improvements really.

> Not sure about the 4870X2, but most other RadeonHD cards can get 3D in Karmic by installing a 2.6.32 kernel and using the xorg-edgers PPA.
Ok! When I say you loose 3D rendering, I mean the one you get is to slow for practical use, even screen savers. But I haven't tried this yet. Will take a look at it :-)

---

### Post by urbanus on 2009-12-01
Found this guide on ATI open source driver with 3D.
[http://www.phoronix.com/forums/showthread.php?t=17603]("http://www.phoronix.com/forums/showthread.php?t=17603")

I'm however using the ATI Binary driver with my ATI HD3850 AGP card in Ubuntu 9.04 (hd-idle doesn't play well with 9.10 it seems). It allows me to do Underscan/Overscan with my LCD TV (basic tv, and cant do it on its own), wohooo :-) Performance/video tearing isn't all great. But I'm still setting it up (changed the GeForce 6800 because of the overscan possibility with ATI), so it's connected with VGA cable. DVI-HDMI might be different!

But ATI & Overscan FTW!!! :D

---

### Post by urbanus on 2009-12-01
Here are some more ATI sources:

radoen & radeonhd experimental 3D:
[http://www.x.org/wiki/radeonhd%3Aexperimental_3D](http://www.x.org/wiki/radeonhd%3Aexperimental_3D)

radeon info and 3D support references:
[http://dri.freedesktop.org/wiki/Radeon](http://dri.freedesktop.org/wiki/Radeon)

---

