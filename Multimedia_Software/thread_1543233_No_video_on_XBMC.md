---
title: "No video on XBMC"
date: 2010-07-31
forum: Multimedia Software
---

### Post by Andrash on 2010-07-31
I just posted this on the XBMC forum, but wanted to seek help here too...

I am new to XBMC (and relatively new to Linux) and was looking forward to trying it on my new  Ubuntu machine. Unfortunately, I am having problems: videos have sound,  but no picture. I'm using a Gigabyte motherboard with integrated ATI  video, and I've read before that XBMC (and Ubuntu in general) don't like ATI too much. Is there any hope left to make XBMC work?

I've tried the following:

1. Fresh Ubuntu installation, default ATI drivers. **Result**: when starting a video, audio is okay, but no video. Also, visibly slow graphics even while navigating XBMC menus

2. Installed ATI/AMD proprietary FGLRX driver via System->Hardware drivers. **Result**: significantly accelerated menu navigation, but no video still. **Note**: having no problems watching videos via VLC or Totem Movie Player (after downloading proper codecs)

3. Fresh Ubuntu installation, then downloaded and installed ATI's  proprietary Linux drivers from ATI's site  (ati-driver-installer-10-7-x86.x86_64.run). **Result**: yippee, I see some video, but wait: no color!! (all videos are in sepia-like mode)

4. Followed [these]("http://ubuntuforums.org/showthread.php?t=1464748") instructions to install the unofficial ATI drivers. **Result**: total failure, XBMC won't even start, says something about the need to have proper hardware OpenGL acceleration.

At this point I'm out of ideas. Please, help!

System info:
     
[LIST]
[*]GIGABYTE GA-MA785GMT-UD2H AM3 AMD 785G mobo with ATI Radeon HD 4200 onboard graphics
[*] AMD Phenom II X2 550 processor
[*] 4 gigs of DDR3 RAM
[*] Ubuntu Lucid 32 bit (2.6.32-24-generic-pae)
[/LIST]

---

### Post by Maletor on 2010-07-31
I just got that Motherboard too. I'm in the process of returning it because I could not get ubuntu to boot the 64 bit USB flash disk.
[http://www.tomshardware.com/forum/277834-30-boot-error#t1912394](http://www.tomshardware.com/forum/277834-30-boot-error#t1912394)

I'm going to get the ASUS board because I know that will work. I have an ASUS board that boots off it fine.

From what I understand the HD 4200 should just work. That what I've read at least. Maybe you need to install proprietary drivers but it works. Even with 1080p x264.

Perhaps it's your TV? Are you connected via HDMI?

---

### Post by Andrash on 2010-07-31
Well the graphics works in the sense that I am able to watch videos on VLC and other media players. It's XBMC that's acting up. And I'm not using a TV yet - right now the comp is connected to a regular monitor via  a regular d-sub.

---

### Post by Maletor on 2010-07-31
I would definitely recommend compiling XBMC from svn. It tends to run better IMHO. Try again after that.

---

### Post by Andrash on 2010-07-31
Unfortunately custom compilation is beyond my area of expertise...

---

### Post by Maletor on 2010-07-31
Try this:

[http://wiki.xbmc.org/index.php?title=HOW-TO_compile_XBMC_for_Linux_on_Debian/Ubuntu](http://wiki.xbmc.org/index.php?title=HOW-TO_compile_XBMC_for_Linux_on_Debian/Ubuntu)

---

### Post by Maletor on 2010-07-31
`

---

