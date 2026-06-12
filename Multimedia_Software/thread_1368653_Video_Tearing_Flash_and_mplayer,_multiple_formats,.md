---
title: "Video Tearing Flash and mplayer, multiple formats, no compiz"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Jerrac on 2009-12-30
I've been having this problem for, probably, years now. When I am watching videos, they will 'tear'. As in a horizontal line will appear like two frames are being shown on different parts of the screen. Hopefully you know what I mean, since that was a bad description...

This has been happening at least since 9.04. I don't have compiz effects turned on. It doesn't seem to matter what format the videos are in, flash, avi, mkv, and mp4 all do it. It's been a while since I tried, but I believe it happens in both totem and vlc. I mainly use smplayer, so it definitely happens there.

Graphics card is an integrated GeForce 8200. NVIDIA driver 185.18.36.

I've tried switching the the output driver smplayer uses to all the different gl options, as well as xv.

Anything else I can try?

---

### Post by lovinglinux on 2009-12-31
[http://ubuntuforums.org/showpost.php?p=7950332&postcount=2](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2)

---

### Post by Jerrac on 2010-01-01
> **lovinglinux said:**
> [http://ubuntuforums.org/showpost.php?p=7950332&postcount=2](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2)

Thanks for the reply, but the chmod 666 thing didn't change anything. I also tried syncing to vblank as they described in [this]("http://ubuntuforums.org/showthread.php?p=7781484#post7781484") topic. That didn't change anything either.

---

### Post by TiPy on 2010-01-04
Same here. I'm using Ati mobility radeon x1400.

It's got awefull tearing... don't know what to do. Tried radeon and radeonhd drivers. Tried a lot of different stuff in xorg.conf and it still does it. It's the most annoying thing.

---

### Post by Jerrac on 2010-01-16
> What is "Tearing"?
When your graphics card is working faster than your monitor, the graphics card can produce more frames in the frame buffer than the monitor can actually display. When the monitor grabs a new frame from the graphics card's primary buffer, the frame may be made up of two or more different frames which overlap. This results in the screen image appearing out of alignment, or "torn". This is especially noticeable in games or video where there is rapid movement.
From [https://wiki.ubuntu.com/X/Glossary?action=show&redirect=X/CommonErrors#What]("https://wiki.ubuntu.com/X/Glossary?action=show&redirect=X/CommonErrors#What")

Any suggestions on how slow my graphics card down?

---

