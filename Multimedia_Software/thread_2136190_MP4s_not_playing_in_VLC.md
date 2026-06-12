---
title: "MP4s not playing in VLC"
date: 2013-04-16
forum: Multimedia Software
---

### Post by stevesy on 2013-04-16
Hi guys, I can't get mp4s to play properly in VLC player, keep getting choppy playback.  I've tried *sudo apt-get install lubuntu-restricted-extras* but no joy..  Any ideas?

---

### Post by papibe on 2013-04-16
Hi stevesy.

Could you paste what is says in 'VLC -> Tools -> Codec Information' (while trying to play the video)?

Also, could you post thre result of these commands?
```
lsb_release -a

sudo lshw -C cpu | grep product

lspci -nnk | grep -iA3 vga

apt-cache policy libva1

vainfo
```
Regards.

---

### Post by stevesy on 2013-04-17
> **papibe said:**
> Hi stevesy.

Could you paste what is says in 'VLC -> Tools -> Codec Information' (while trying to play the video)?

Also, could you post thre result of these commands?
```
lsb_release -a

sudo lshw -C cpu | grep product

lspci -nnk | grep -iA3 vga

apt-cache policy libva1

vainfo
```
Regards.

Hey Papibe,

VLC Codec Info

Stream 0
     Type: Video
     Codec: H264 - MPEG-4 AVC (part 10) (avc1)
     Resolution: 1920x1040
     Frame rate: 23.976023 
     Decoded format: Planar 4:2:0 YUV

Stream 1
     Type: Audio
     Codec: MPEG AAC Audio (mp4a)
     Language: English
     Channels: Stereo
     Sample rate: 48000 Hz



steve@steve-Inspiron-910:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise


steve@steve-Inspiron-910:~$ sudo lshw -C cpu | grep product
[sudo] password for steve: 
       product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz


steve@steve-Inspiron-910:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
    Subsystem: Dell Device [1028:02b0]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915


steve@steve-Inspiron-910:~$ apt-cache policy libva1
libva1:
  Installed: 1.0.15-4
  Candidate: 1.0.15-4
  Version table:
 *** 1.0.15-4 0
        500 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status


steve@steve-Inspiron-910:~$ vainfo
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/i915_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

---

### Post by papibe on 2013-04-17
Thanks.

Unfortunately, your computer is not powerful enough to play smoothly full HD video.

Mainly because your integrated graphic card does not support video hardware acceleration, and your processor by itself is not fast enough.

If you have a desktop, it may be possible to install a discrete graphic card. For instance, with around $40 you can get an Nvidia 620, or similar.

Regards.

---

### Post by stevesy on 2013-04-17
> **papibe said:**
> Thanks.

Unfortunately, your computer is not powerful enough to play smoothly full HD video.

Mainly because your integrated graphic card does not support video hardware acceleration, and your processor by itself is not fast enough.

If you have a desktop, it may be possible to install a discrete graphic card. For instance, with around $40 you can get an Nvidia 620, or similar.

Regards.

Ok papibe, thanks for looking into it for me.  A little off topic but I get choppy playback with *some* mp4s when playing them through my HDTV?!  I don't have a desktop and I'm guessing an external graphics card for a netbook would be a waste of time?

---

### Post by papibe on 2013-04-17
> **stevesy said:**
> I don't have a desktop and I'm guessing an external graphics card for a netbook would be a waste of time?
It is not impossible, but a bit unlikely that you can install a graphic card on a netbook. Nevertheless, I could be valuable to research the possibility since you could convert your machine in a powerful HTPC. 

> **stevesy said:**
> A little off topic but I get choppy playback with *some* mp4s when playing them through my HDTV?!
If you can play the video OK on you laptop screen, but have some issues on a HDTV, may is a [Tearing]("http://en.wikipedia.org/wiki/Screen_tearing") problem. This kind of problem may be solved by either adjusting the refresh frequency to properly match the HDTV's, or by setting up a feature called 'Sync to Vblank'. Sadly, I'm not familiar enough with the Intel driver to offer you specifics, but I hope it points you in the right direction.

Regards.

---

### Post by stevesy on 2013-04-18
> **papibe said:**
> It is not impossible, but a bit unlikely that you can install a graphic card on a netbook. Nevertheless, I could be valuable to research the possibility since you could convert your machine in a powerful HTPC. 


If you can play the video OK on you laptop screen, but have some issues on a HDTV, may is a [Tearing]("http://en.wikipedia.org/wiki/Screen_tearing") problem. This kind of problem may be solved by either adjusting the refresh frequency to properly match the HDTV's, or by setting up a feature called 'Sync to Vblank'. Sadly, I'm not familiar enough with the Intel driver to offer you specifics, but I hope it points you in the right direction.

Regards.

Many thanks papibe, I'll do some more research : ]

---

