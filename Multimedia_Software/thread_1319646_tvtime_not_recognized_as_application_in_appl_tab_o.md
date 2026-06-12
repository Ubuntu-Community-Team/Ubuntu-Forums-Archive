---
title: "tvtime not recognized as application in appl tab of gnome-volume-control"
date: 2009-11-08
forum: Multimedia Software
---

### Post by marc.verwerft on 2009-11-08
Hello all,

To make things clear, my "sound" mostly works - I hear the music when I log on to my box, I can play rhythmbox, etc.

But when using tvtime, I have NO sound. On further investigation, I found that when I run rhythmbox, that application appears on the applications tab of the sound applet (gnome-volume-control I think). However, when I start up tvtime, this app doesn't show up.

I am running a vanilla Karmic, freshly installed (no upgrade) all fixes applied. I have a Bt878 and a SAA7134 card. Both work, both without sound. I've looked at a lot of threads with pulseaudio and tvtime but no solutions found. Any idea's on how to investigate this further?

Tecnical data:
uname -a: Linux marc-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
I've also included 2 screenshots, one with rhythmbox and gnome-volume-control and one with tvtime.

Regards,

Marc

---

### Post by xc3RnbFO8P on 2009-11-08
Try in Terminal:
> alsamixer
see if got AUX, use arrow keys and m for unmute
or read this:
[http://ubuntuforums.org/showthread.php?t=884438]("http://ubuntuforums.org/showthread.php?t=884438")

---

### Post by marc.verwerft on 2009-11-09
> **Ringi said:**
> Try in Terminal:
```
alsamixer
```see if got AUX, use arrow keys and m for unmute
or read this:
[http://ubuntuforums.org/showthread.php?t=884438](http://ubuntuforums.org/showthread.php?t=884438)
Alsamixer sess AUX, it was unmuted.

But I tried 
```
$tvtime -M | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:surround51
```And that worked. The weird thing is that it works equally well for the Bt878 while the discussion in the thread you pointed out is all about the saa7134 card.

And although I got sound now, it still doesn't explain why tvtime does not register as an application in gnome-volume-control.

Thanks a lot!

Regards,

Marc

---

### Post by Uncle Spellbinder on 2009-11-17
Sorry.  Wrong thread................

---

