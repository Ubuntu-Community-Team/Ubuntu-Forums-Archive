---
title: "1080p looks grainy 720p crystal clear....Help :("
date: 2011-08-16
forum: Multimedia Software
---

### Post by Levitys on 2011-08-16
Hey guys, 

I thought I'd see if anyone has had this problem and could help me.
When I play 1080p video The picture looks all.....pixelated....almost like 
watching a vhs or something. I was having horrible screen tearing issues until i turned off the desktop effects which took care of that problem. 720p looks great!
I have been testing with Arthur in 1080p. on my wdtv its crystal clear......not the case with my new htpc :(

_Here is some info:_

**MB/GPU (integrated)**
ASUS M4A88TM_LE
Integrated ATI Radeon™ HD 4250 GPU
Multi-VGA output support : HDMI/DVI/RGB ports 
- Supports HDMI with max. resolution 1920 x 1080 @ 60 Hz
- Supports DVI with max. resolution 2560 x 1600 @ 60 Hz
- Supports RGB with max. resolution 2048 x 1536 @ 85 Hz
Maximum shared memory of 1024 MB
Dual independent displays support with HDMI/DVI and D-Sub
Hardware Decode Acceleration for H.264, VC-1, and MPEG-2
Blu-ray playback support *1
Supports DirectX 10.1, OpenGL 2.0, Shader Model 4.1, Universal Video Decoder (UVD) 2.0

**CPU:**
AMD Black Phenom II 3.3 x2

**fglrxinfo**
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4250 
OpenGL version string: 3.3.10362 Compatibility Profile Context

I am using the proprietary driver......I tried open source and it froze the os up had to do a re-install.

I am running ubuntu 10.04 and using XBMC.
I think thats everything except I'm using HDMI to 1080p 37" panasonic.

Any help would be appreciated.
Thanks guys, 
Hope to hear some solutions soon :D

---

### Post by Levitys on 2011-08-17
Bumperooo

---

### Post by aeiah on 2011-08-17
does xbmc report that your screen res is 1920 x 1080?

---

### Post by Levitys on 2011-08-17
Yes it does

---

### Post by tjones00 on 2011-08-17
This might seem like a no brainer but are you positive it's a 1080**p** display and not 1080**i**?

To me it sounds like you're using a 1080i resolution on a 720p display.

---

### Post by Levitys on 2011-08-17
> **tjones00 said:**
> This might seem like a no brainer but are you positive it's a 1080**p** display and not 1080**i**?

To me it sounds like you're using a 1080i resolution on a 720p display.

I just looked at the manual it is definitely a 1080p.

Thanks :D

---

### Post by tjones00 on 2011-08-17
Is hardware acceleration enabled in xbmc?

---

### Post by Levitys on 2011-08-17
vdpau is selected.....
im not sure how exactly if u can tell if its working or not though :/

---

### Post by BicyclerBoy on 2011-08-18
VDPAU is an open specification designed by nVidia.
It could be possible for the VDPAU interface to work with other brands GPU.

VA-API is touted as the universal video decode/presentation API.
AFAIK You can't use VDPAU on AMD/ATI.

You have to make do with VA-API & this is not working out of the box..

There are good threads/posts about building VA-API support for AMD/ATI on XBMC forums.

---

### Post by Levitys on 2011-08-18
> **BicyclerBoy said:**
> VDPAU is an open specification designed by nVidia.
It could be possible for the VDPAU interface to work with other brands GPU.

VA-API is touted as the universal video decode/presentation API.
AFAIK You can't use VDPAU on AMD/ATI.

You have to make do with VA-API & this is not working out of the box..

There are good threads/posts about building VA-API support for AMD/ATI on XBMC forums.

So my Video Card isn't working at all with XBMC then?
If so that sucks. 
Do you think going out and getting a Nvidia Would be easier?

---

### Post by tjones00 on 2011-08-18
I'd try the VA-API route before spending any money. If it involves compiling it's not nearly as scary as it might sound. Many people over at the XBMC forum use a debian/ubuntu base so there should be debian/ubuntu instructions.

---

### Post by Levitys on 2011-08-19
> **tjones00 said:**
> I'd try the VA-API route before spending any money. If it involves compiling it's not nearly as scary as it might sound. Many people over at the XBMC forum use a debian/ubuntu base so there should be debian/ubuntu instructions.

It's like you read my mind lol.
The whole compiling xbmc seems pretty daunting.
I will look into it. :)

Thanks for your help
levitys

---

