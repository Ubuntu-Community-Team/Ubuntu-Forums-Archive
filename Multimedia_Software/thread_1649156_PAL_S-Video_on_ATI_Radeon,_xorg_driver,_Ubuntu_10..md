---
title: "PAL S-Video on ATI Radeon, xorg driver, Ubuntu 10.10 64-bit"
date: 2010-12-19
forum: Multimedia Software
---

### Post by Jack Kelly on 2010-12-19
I'm trying to convert my Home Theatre PC from Windows Vista to Ubuntu.  My main problem is that I can't get a stable, colour picture on my widescreen SD CRT PAL TV, connected to the HTPC over S-video.  I've been trying for 3 days and  I've now run out of ideas!  I'd really appreciate any help!  Have you gotten S-video to work on a Radeon card?

**Specs**

[LIST]
[*]ATI Radeon x1250 (RS690) (onboard motherboard)
[*]Open source "radeon" driver
[*]AMD dual-core 64-bit processor, 2GB RAM
[*][BioStar TA690G AM2 motherboard]("http://www.biostar.com.tw/app/en/mb/bios.php?S_ID=17") (with latest BIOS)
[*]mythbuntu 10.10 64-bit
[/LIST]
**What I've tried:**

**Windows Vista Media Centre 64-bit**
S-Video and component output both work fine

**Ubuntu with AMD/ATI's latest closed-source driver**
Component output shows a stable, colour image but no acceleration works and video playback is very juddery.  ATI's configuration software claims it can't find a supported device.   It turns out my x1250 is a "legacy device" so I installed the "legacy" drivers but these were built for an old version of Ubuntu and didn't install correctly.

**Ubuntu with the radeon (open source) driver**
Works beautifully when outputting to a VGA monitor.  But shows an unstable, black-and-white image on my TV over S-video.  I *think *the reason the image is unstable is because the card isn't using the correct timings, although I have no way to measure the S-video timings.  I've tried both the "stock" radeon driver (installed with Ubuntu 10.10) and the [latest radeon driver from git]("http://wiki.x.org/wiki/radeonBuildHowTo").  I've tried:

[FONT=Courier New]$ xrandr --output S-video --set "tv standard" pal
$ xrandr --newmode "720x576@25i" 13.5 720 732 795 864 576 581 586 625 interlace -hsync -vsync
$ xrandr --addmode S-video 720x576@25i
$ xrandr --output S-video --mode 720x576@25i[/FONT]

(I've tried [all the PAL modelines listed on the MythTV wiki]("http://www.mythtv.org/wiki/Modeline_Database#PAL625_itu-r.2Fbt:_470_601_656") and I've tried extracting a modeline from Windows using powerstrip).

Setting "tv standard" to pal actually makes the image totally unusable.  pal-m is reasonably stable, as is ntsc.

I've tried turning Kernel Mode Setting off but that didn't help and actually seemed to make X go very slowly

I've tried [adding Kernel lines]("https://wiki.archlinux.org/index.php/ATI#Force_TV-out_in_KMS") to configure the S-video output but no joy

I've tried all manor of xorg.conf settings but they seem to do very little

I've tried changing my BIOS's TV-Format settings to PAL and NTSC (and others)

Possibly of interest is[ this EDID bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376"), but I doubt it is relevant for my problem.

I've attached my dmesg log, Xorg.0.log and xorg.conf

----

So, please, if anyone has any ideas please let me know!  Could this be a bug??

---

### Post by Jack Kelly on 2010-12-22
Humph.  I've just tried [installing the latest kerne]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds")l (2.6.37) but this hasn't helped matters.

Any tips?!

---

### Post by Jack Kelly on 2010-12-22
Ah, this appears to be a known bug: [https://bugs.freedesktop.org/show_bug.cgi?id=21948](https://bugs.freedesktop.org/show_bug.cgi?id=21948)

I've submitted my log files etc

---

