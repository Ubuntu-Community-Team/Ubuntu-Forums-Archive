---
title: "Video going in and out constantly"
date: 2010-11-13
forum: Mythbuntu
---

### Post by dublea on 2010-11-13
So I'm new to mythbuntu but not linux.  I've got an ASUS 8400GS hooked up to my RCA HDTV.  When I first installed mythbuntu the screen keeps going in and out... every few seconds.  It almost seems like it's doing it every time it probes.  I've searched around but I can only find those with no video, or a blank screen.  I wonder if this is an issue with HDMI and linux.  Any help would be great!

So, if I leave the system untouched, the screen doesn't go in and out.  But if I move around the menu, get out of the frontend, open a window, it goes in and out.  My tv responds with unusable signal and then goes back to the startup.  If anything moves, a vlc bar, anything, it goes in and out.

---

### Post by nickrout on 2010-11-13
not sure what you mean by "in and out"

linux has no problems with your card, or with hdmi.

Are you using the nouveau driver or the nvidia driver with that card?

---

### Post by dublea on 2010-11-13
what I mean by "in and out" is that there is the MythTV menu.  I hit the down arrow and the screen goes blank then comes back.

At the desktop, I click Applications and the drop down menu come up, BUT then the screen goes blank and my RCA L32WD22 pops up "Unsupported Input" and then the desktop comes back up.  

It does this every few seconds.  If need by I will video it and put it on youtube so you can see it happen.

Edit:  I thought it was when I messed with a menu or window but when I attempted to make a video of it happening, it just goes in and out on it's own.

---

### Post by dublea on 2010-11-13
Here's a video:

[http://www.youtube.com/watch?v=o8qQH5fhvbI]("http://www.youtube.com/watch?v=o8qQH5fhvbI")

---

### Post by LowSky on 2010-11-13
looks like a loose cable or a bad video card to me or your using the wrong resolution

---

### Post by dublea on 2010-11-13
This does not happen in windows.  I just installed in on a secondary HDD just to test.  So I doubt it's either of the above.

Edit:

Here is a complete setup of my system

Mobo:  Intel DG31ID
CPU:  Pentium D 820
Memory:  2GB PC6400
HDD:  250GB x2 SATA
Video:  ASUS 8400GS AKA G100
Television:  RCA L32WD22
Current connection is DVI to HDMI / Have been using VGA for debug with HDMI as secondary, just set that up.


I've attempted two different HDMI cables and DVI - HDMI adapters.  I've connected the box to a computer monitor that has HDMI and made sure it wasn't the system causing it.  It's only allowing me to put out 60hz refresh rate.  I feel as though this TV needs something lower, like 55hz or lower.  I can't remember how to force this or add different refresh rates.

---

### Post by dublea on 2010-11-14
Ok, so here are the differences in setup between Mythbuntu and Windows:

(Mythbuntu/Windows)
Resolution:  1176 x 664 @ 59Hz / 1280 x 720 @ 60Hz
HDMI:  Video w/o Audio / Video w/ Audio

I need to be able to add different resolutions, refresh rate, and turn off audio (audio is the biggest thing) to stop the video going in and out.

---

### Post by nickrout on 2010-11-14
try xrandr (commandline) and nvidia-settings

---

### Post by dublea on 2010-11-15
Thanks for the help but I've found that the main issue is the spdif sound that comes over the hdmi.  I've attempted to disable it via an edid hack but it was a no go.  Getting nvidia to work with xorg.conf is a pain in the *** and I said screw it.  I'll just be using Windows till I either get another tv or hook it up via component cables.

---

