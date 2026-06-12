---
title: "Nicities lost with graphics card upgrade - X starting on reboot and panning screen"
date: 2009-08-10
forum: Multimedia Software
---

### Post by Fraoch on 2009-08-10
I just upgraded my graphics card from an ancient ATI 8500 LE to an nVidia 9400 GT.

After sorting through some minor initial problems caused by the chair-to-keyboard interface, I am left without some niceties I had with the old card.

1.  As of the update to 9.04, X would automatically start regardless of any monitor connected.  For various reasons I'm running this machine headless and connecting to it remotely through TightVNC.  Until 9.04 if I rebooted the machine I had to connect a monitor on startup to automatically get X back.  After 9.04, X automatically started whether or not a monitor was connected.  This was great for VNC.  However I've lost that ability now.  I have tried the "startx" command to fire up X manually over SSH but it doesn't seem to work.

2.  When I do start up, I get an odd screen with my command bar and icons wayyy off to the left corner, cut off.  I can pan around if my pointer comes up against an edge to get my normal screen back, but it's cumbersome - every time I touch the command bar it pans up and my background image is way too big.  It looks like my 1024 X 768 command bar and icons are placed on a 1400 X 1050 screen that I have to pan around.  The command bar and icons are not smaller, they are just placed on a much larger desktop that I am forced to pan around.  I can correct this oddity by going into the NVIDIA X Server Settings item in Control Panel, setting the resolution to something else, then resetting it back to 1024 X 768, but on reboot it's back to panning again.

How do I resolve these two issues?  I have a feeling all this can be set in /etc/X11/xorg.conf but nothing specific to either of these issues was changed.  The xorg.conf documentation is massive but neither of these issues are addressed.

Any pointers?

Thank you.

---

### Post by Fraoch on 2009-08-11
No ideas?:(

---

