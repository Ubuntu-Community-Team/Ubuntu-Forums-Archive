---
title: "Problems with NVIDIA GeForce GT 425M VDPAU"
date: 2011-08-26
forum: Multimedia Software
---

### Post by doestergaard on 2011-08-26
Hi fellow Ubuntu users!

I know there is several posts covering this issue, but I have almost read all of them and tried others solutions, but with no luck. I have also tried every driver from when my card was first supported, and neither of them works. Even the restricted driver Ubuntu suggests doesn't correct it either. I have a ASRock Vision 3D 137B, which have the following specs:

Processor: 2.40GHz Core i3 Intel Processor
Graphics: 1024MB NVIDIA GeForce GT 425M
RAM: 4GB
BluRay Combo Drive
500GB 7200RPM HDD
3x USB 3.0 ports
4x USB 2.0 ports
1x HDMI 1.4 Output
1x Optical Digital 7.1 Channel Surround Sound
LAN + WiFi Onboard

This is basically what my system looks like. It's an HTPC which I run a Ubuntu 10.10 i386 (x86) system. This is how I installed my system:


1) Installing Ubuntu 10.10 on HDD

2) Updating system with all newest updates from Update Manager

3) Installing NVIDIA Driver (certified and original .run package from NVIDIA driverpage) Again, have tried all of them except betas + restricted from Additional Drivers.

4) Installed XBMC

5) Installed LIRC drivers for ASRock Vision 3D Remote

6) Test with playing HD Content and the playback is laggy and one of my CPU's is showing 100%, so I know it is the VDPAU which isn't working correctly, but I'm lost from here!

7) Tried all Sync-to-VBlanc


Any help is appreciated! :)


Thanks in advance!

---

### Post by realzippy on 2011-08-26
Did you try adding xswat ppa to sources and installing vdpau-video package?

and welcome to UF

---

### Post by doestergaard on 2011-08-27
Thank you for your reply. Tried it out and it didn't make any difference, still laggy, and there is a wierd thing i discovered:

When playing a 1080p HD video, on different chapters, it randomly selects cors, e.x.:

Chapter 2: Core 0: 2,4%, Core 1: 100%, Core 2: 4,8%

Chapter 3: Core 0: 100%, Core 1: 6,7%, Core 2: 9,4%

The GPU core stays at 99,9% all the time :confused:


The framedrops counts like hell, so it is really bad! If I'm lucky, I can at max get 10,58 fps in scenes with a lot of angels and fast movement, it stays stable in quiet scenes approx 24 fps.


When changes nvidia-settings Sync to Vblank in OpenGL, the above changes to:

Chapter 2: Core 100%:, Core 1: 2,4%, Core 2: 4,8%

Chapter 3: Core 0: 9,4%, Core 1: 6,7%, Core 2: 100%

The GPU core stays at 99,9%.


This is the wierdest problem I have ever seen.

Thanks again!


EDIT: The PPA for 10.10 MM doesn't include the vdpau-video package?

---

### Post by realzippy on 2011-08-27
Tried VLC and ticked the checkbox
Input & Codecs Settings => use GPU acceleration ?

---

### Post by doestergaard on 2011-08-27
Nope, VLC runs smoothly, so could it be XBMC?

It uses libvdpau1, which I think VLC does too?


Even though if I don't install the libvdpau1 package, XBMC installs it automaticly when installed on my system.

---

### Post by realzippy on 2011-08-27
sorry,not using XBMC.
Anybody else maybe ?

---

