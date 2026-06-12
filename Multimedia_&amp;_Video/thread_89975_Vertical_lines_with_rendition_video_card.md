---
title: "Vertical lines with rendition video card"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by The Mad Scientist on 2005-11-13
I have just installed Breezy onto an old machine (Pentium MMX 200 with 64MBytes of RAM).  I used the server installation and tried both IceWM and XCFE4.  Both worked well.  However, my video card (Diamond Stealth II S220, Rendition 2100 chipset) does not appear to be well supported.  The display has vertical lines about every 50 pixels or so across the screen.  They fade and appear as I move the mouse around.  The display itself is also somewhat corrupted, making text fuzzy and giving shadows to things like the cursor.  This hardware works great under Windows 98SE (dual boot system).  I have tried the vesa, rendition, and vga drivers.  vesa and rendition both had the problem.  vga just didn't work (the X server kept repetitively booting).  I remember this problem on Win95 back in the early days of this card (~1997), but a driver upgrade fixed it.  Does anyone have any ideas how to fix this on Ubuntu?

---

### Post by mcduck on 2005-11-14
I've seen that happening, and I solved it by using a bit smaller refresh rate for my monitor. Change it in your xorg.conf or run 'sudo -dpkg-reconfigure xserver-xorg'

---

### Post by frodon on 2005-11-14
I give you the link to a similar thread : [http://www.ubuntuforums.org/showthread.php?t=89322](http://www.ubuntuforums.org/showthread.php?t=89322)

---

### Post by The Mad Scientist on 2005-11-14
I tried reducing my refresh rate and it didn't help.  The original refresh rate was 50-90.  I changed it a bit at a time until I got to 50-60.  The problem did not go away.  Any other ideas?

---

