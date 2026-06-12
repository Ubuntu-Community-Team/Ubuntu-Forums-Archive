---
title: "Problem enabling tv out with nvidia binaries"
date: 2008-09-19
forum: Multimedia Software
---

### Post by dmsuperman on 2008-09-19
I've got the nvidia binaries, from nvidia's website. I have version 173.14.09 installed. I'm using hardy with all the (as far as I know) updates installed.

All is working well, dual monitor set up using nvidia-settings, yada yada. I decided I wanted to use my s-video (tv) out and a secondary monitor instead of my normal monitor for a bit, to watch a movie on. I went into nvidia-settings and disabled my secondary monitor, then enabled my second one. I went through, change it from "Off" to "TwinView", then change the resolution from "Auto" to 1024x768. When I hit apply, X crashes. I've tried it with leaving it at Auto, but an error pops up saying it couldn't set the meta mode and X completely locks up (even ignoring Ctrl + Alt + Backspace).

Here is /var/log/Xorg.0.log:
[http://dmsuperman.pastebin.com/f52ab3d27](http://dmsuperman.pastebin.com/f52ab3d27)
and /var/log/Xorg.0.log.old:
[http://dmsuperman.pastebin.com/f7dec261a](http://dmsuperman.pastebin.com/f7dec261a)


What am I doing wrong?

---

