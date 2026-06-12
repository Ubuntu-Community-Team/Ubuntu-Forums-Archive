---
title: "Jittery DVD playback."
date: 2011-01-28
forum: Multimedia Software
---

### Post by ShadowTek on 2011-01-28
I'm having jittery DVD playback, and I don't know what the problem is. I tried switching to metacity, but that didn't help. I tried copying the whole disk to local drive with dvdbackup, but the local files displayed the same effects.

I tried mplayer and vlc, but no difference. Totem, however, is really bad with jitters. With totem, I tried checking 'Disable deinterlacing of interlaced videos', which I saw someone recommend in another thread, but that didn't help either.

I also have all the codecs from this forum's how-to sticky.

A video capture of the jitters while playing with vlc:
[http://img13.imageshack.us/img13/7234/nj8.mp4](http://img13.imageshack.us/img13/7234/nj8.mp4)

Any idea what's causing this?

I'm using Ubuntu 10.10 Desktop 32-bit.

---

### Post by ShadowTek on 2011-01-29
Bump.

I still don't know what the problem is.

---

### Post by TBerk on 2011-01-29
I see you have 32bit 10.10, but it might help to also know more about your hardware too.

- Video card
- Processor & speed
- Total system RAM (memory)

Etc, etc.


TBerk

---

### Post by BicyclerBoy on 2011-01-29
Are you sure this video wasn't shot with a camcorder at the back of the cinema !
It looks like a conversion from film using a shaking screen.

---

### Post by ShadowTek on 2011-01-30
This is the retail DVD, which plays smoothly in a stand-alone DVD player.


Video Card:  GeForce GTS 250
CPU:  Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
RAM:  4 GBs of DDR2 with PAE kernel

More is attached:

---

### Post by BicyclerBoy on 2011-01-30
The nvidia GTS250 should be able to decode/play DVD mpeg2.

The GTS250 is a NOT capable of purevideo4 vdpau feature set C.
It is too slow for a gaming card.

IMO This card is a mistake like the GT210.

Have you installed proprietary drivers via jockey?
Have you installed libdvdcss libdvdnav ?

Read ubuntu website restricted formats & medibuntu.

---

### Post by ShadowTek on 2011-01-30
> Have you installed proprietary drivers via jockey?
The current version of the nvidia proprietary driver was installed from the GUI.
 System > Additional Drivers

> Have you installed libdvdcss libdvdnav ?Yes.
```
$ apt-cache policy libdvdcss2
libdvdcss2:
  Installed: 1.2.10-0.3medibuntu1
  Candidate: 1.2.10-0.3medibuntu1
  Version table:
 *** 1.2.10-0.3medibuntu1 0
        500 http://packages.medibuntu.org/ maverick/free i386 Packages
        100 /var/lib/dpkg/status
```
```
$ apt-cache policy libdvdnav4
libdvdnav4:
  Installed: 4.1.3-7
  Candidate: 4.1.3-7
  Version table:
 *** 4.1.3-7 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/universe i386 Packages
        100 /var/lib/dpkg/status
```

> Read ubuntu website restricted formats & medibuntu. I assume that you're referring to the following pages?
[https://help.ubuntu.com/9.10/add-applications/C/restricted-software.html](https://help.ubuntu.com/9.10/add-applications/C/restricted-software.html)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The only thing I saw that I hadn't yet tried was xine, but I tried it, and the result was just as jittery.

---

### Post by cchhrriiss121212 on 2011-01-30
Off topic slightly:
> The GTS250 is a NOT capable of purevideo4 vdpau feature set C.
Do you have a source for this?

---

### Post by ShadowTek on 2011-01-30
This is the one that I have:
[http://us.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&cat3_no=&prod_no=1953](http://us.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&cat3_no=&prod_no=1953)

I states having "PureVideo™ HD2 technology".

---

### Post by BicyclerBoy on 2011-01-30
Marketing speak...
I said Nvidia Purevideo 4 vdpau feature set C..

This card is fine for mpeg2 DVD.

AFAIK Xine is used in Maverick Totem player.

Post your /var/log/Xorg.0.log
maybe your video driver is sick

glxgears
vdpauinfo
vdpautest
vainfo

---

### Post by NightwishFan on 2011-01-30
Try setting VLC to use "x11 video" instead of "xvideo". Does that help?

---

### Post by ShadowTek on 2011-01-30
> **BicyclerBoy said:**
> Marketing speak...
I said Nvidia Purevideo 4 vdpau feature set C..Uhh, I was just talking about my card, dude. I wasn't disputing your opinion of set-C.


> **BicyclerBoy said:**
> Post your /var/log/Xorg.0.log
maybe your video driver is sick

glxgears
vdpauinfo
vdpautest
vainfo

Where is vdpauinfo and vdpautest?
`apt-cache search` shows nothing.

```
$ vainfo
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

---

### Post by ShadowTek on 2011-01-30
> **NightwishFan said:**
> Try setting VLC to use "x11 video" instead of "xvideo". Does that help?
Nope.

---

### Post by NightwishFan on 2011-01-30
Then this possibly has nothing to do with GPU, as the x11video driver just uses CPU (I believe).

(I had terrible grammar there, not sure what got into me! :D )

---

### Post by BicyclerBoy on 2011-01-30
@OP
Your attached files look fine..
video hardware & driver looks okay.
vainfo relates to VAAPI mostly pointless if you have vdpau.

VLC can play a DVD fine without any video card decode support. 

Is this problem universal or just one DVD ?

---

### Post by sudoCrushMS on 2011-02-01
Bump. 

Been happening to me too, not too noticable on a 26" Vizio, but print on the screen is very annoying. Does this happen at all in Fluendo? I figure with a 100% free setup so far it would be worth the $35 for HD and no problems.

---

### Post by sudoCrushMS on 2011-02-01
> **sudoCrushMS said:**
> Bump. 

Been happening to me too, not too noticeable on a 26" Vizio, but print on the screen is very annoying. Does this happen at all in Fluendo? I figure with a 100% free setup so far it would be worth the $35 for HD and no problems.


I found the solution to my problem. I installed the full Medibuntu repository (just to be thorough) and disable deinterlacing of video in MPlayer. Worked like a charm, been trying to find a fix for that issue on and off for a couple months now.

Here is the terminal command for the Medibuntu repository:
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

### Post by adduds on 2011-02-01
> **sudoCrushMS said:**
> I found the solution to my problem. I installed the full Medibuntu repository (just to be thorough) and disable deinterlacing of video in MPlayer. Worked like a charm, been trying to find a fix for that issue on and off for a couple months now.

Here is the terminal command for the Medibuntu repository:
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

I was having the same issue, checked forums, went through this post found this....

used exact copy of terminal post... and disabled deinterlacing of video in MPlayer

works great for MPlayer

try to play dvd in VLC but there's no dialogue...I've got soundtrack audio but no speech...it sounds very quiet and muffled....

---

