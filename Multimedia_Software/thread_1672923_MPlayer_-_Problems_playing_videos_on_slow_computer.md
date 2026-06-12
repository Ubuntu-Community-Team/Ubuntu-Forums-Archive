---
title: "MPlayer - Problems playing videos on slow computer"
date: 2011-01-21
forum: Multimedia Software
---

### Post by WeAreLinux on 2011-01-21
Hey & Happy New Year! (haven't been on here since).

-Ubuntu 10.04 with MPlayer/Smplayer & VLC installed via the repos.

-Installed the Ubuntu Restricted Extras package (everything except flash, extra fonts, & java) & w32codec packgae (medibuntu).

-Computer in question is 800mhz Celeron, 256MB RAM & one of those basic Intel Integrated Graphics Chip.

I'm having problems playing some video files. When trying to play these files with Smplayer, I get a blue screen but can still hear audio (default video output). After switching the video output to x11(slow), I can now see the picture but it's not playable (some video will show maybe one frame every 2 seconds, some video would play for half-a-second then just freeze). This happens mainly with large files (not 100% accurate, but in general files over 300MB).

Mplayer log gives the "Your system is too slow to play this file" & "Bad alloc:insufficient resources" messages. So I'm guessing this is not a codec problem, but a system resources problem?

Is there any option, trick, tweaks, etc. I can use to play these problematic files or is it just not possible because of my system specifications?

Is there a way I could tell mplayer to play these files with lower bitrates & resolution? Maybe this could reduce the resources needed to play?

TIA

---

### Post by SeijiSensei on 2011-01-21
The only files you *might* be able to play on that machine are AVI files with XviD encoding.  Anything with H.264 encoding, or much bigger than 640x480 or perhaps 320x240, will bring your computer to its knees. Even then, I doubt they'll play well.  Installing a recent NVIDIA video card *might* help, since you could use the NVIDIA "VDPAU" driver to offload the video processing to the card's graphics controller.  Even then, I doubt it will help much, and I wouldn't invest the money in a new graphics card.  I'd save up to buy a modern computer.  Even a sub-$400 desktop would run rings around what you're using now.

---

### Post by andrew.46 on 2011-01-21
There are a few notes on this problem here:

[http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ#General_Questions](http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ#General_Questions)

Andrew

---

### Post by WeAreLinux on 2011-01-25
> **andrew.46 said:**
> There are a few notes on this problem here:

[http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ#General_Questions](http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ#General_Questions)

Andrew

Thanks. I'll try some of those tips and see what happens (don't have access to the machine @ the moment).

I also found this: [http://www.mplayerhq.hu/DOCS/HTML/en/xv.html#intel](http://www.mplayerhq.hu/DOCS/HTML/en/xv.html#intel)

What exactly does the xorg.conf modification do? I really don't like to modify config files unless I'm sure what I'm doing. Any insight?

> ...much bigger than 640x480 or perhaps 320x240, will bring your computer to its knees.

Yup, you are correct. Most of the problematic files have bigger resolutions. Once I have some $$, I'll look into buying a new machine.

---

