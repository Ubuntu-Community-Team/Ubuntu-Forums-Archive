---
title: "Twinview - avi &amp; other problems"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by mageus on 2006-12-30
Finally got Twinview to work but still having problems.

Specs:
Ubuntu 6.10 Edgy
NV 1.0-9631
GeForce 7600GT 2 DVI ports
	LCD attached to DVI 1
	plasma display attached via VGA to DVI 2 with VGA->DVI adapter plug

WORKS:

- Twinview displays a desktop in clone and side-by-side modes.
- Panning works (if the TV resolution is smaller, and they are in clone mode)

PROBLEMS:

1) When Twinview is enabled, any video media file (AVI, OGM, MKV, MP4) shows a black video, with/without sound, and the system grinds to a halt, sometimes freezing the mouse.

When the video plays (in twinview) I can hit ctl-alt-f1 to get a console, but only after about 10 seconds.  VLC works the best - it will respond after about 10-20 seconds if I hit the close button many times.  Totem & Mplayer just freeze the whole desktop completely.

With twinview not enabled, video playing (and everything else) works fine.


2) With twinview not enabled, and the plasma plugged in, I get no xwindows output to either display.

When I installed Ubuntu (with twinview not enabled, of course), I had the plasma unplugged, and everything worked fine.  If I plug the plasma into DVI2 then I get no X or TTY on either display.

Enabling twinview fixes this problem.

I assume this has to do with the fact the the NV driver always assumes that VGA is the main display, so it's trying to output to the plasma, but is screwing up.


3) Side-by-side mode always puts the panel on the plasma.

I understand that this is because the nv driver always assumes that VGA is the primary display.  I also know that you can add a panel to the second display.  However, I'd like a setup where the LCD shows a panel, and the plasma is just a blank desktop.  Any way to do this?



My main goal right now is getting video to play properly in Twinview mode (otherwise, what's the use?).


Attached are my xorg.conf's.  xorg.conf.nvworks is for twinview disabled, and xorg.conf.tv1024works is with twinview.


TIA

---

