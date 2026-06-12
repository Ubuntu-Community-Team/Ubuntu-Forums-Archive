---
title: "mplayer, vidix, and newer nvidia cards"
date: 2009-01-07
forum: Multimedia Software
---

### Post by patsissons on 2009-01-07
I was getting pissed off when my box was struggling with a 720p video that i was trying to watch with mplayer.  I have an GeF8600GT (G86 chip) and a 2GHz dual core server cpu, so i was a little puzzled why things were getting choppy.  I know this isn't the highest end gear, but it should be good enough for 720p.  

Anyways, i know im running the xv drivers, the x11 ones are no good since you can't zoom.  So i looked into the vidix, which i remember worked really well, but you had to run it with root privileges since it needs direct access to the video hardware.  The vidix failed right away (i.e. no video at all). So i grabbed the mplayer source from subversion and started poking around.  I soon realized that mplayer is CODED to fail on anything in the 8x00 series or higher.  Basically, when checking for a valid card on the PCI bus, it checks any nvidia hardware matches a list of card (device) id's.  Since none of the new device id's are in the list, it obviously fails.

I can't find any info on whether or not vidix was discontinued or whatever on these new cards, anyone know anything about it?  Also, anyone know a better way to play 720p and 1080p mkv files without the choppiness?

---

### Post by evil-noxx on 2009-10-03
Hi,
I've a similar machine to your and never had any issues playing any video (720p or any other resolution). I usually use Totem-gstreamer to play all my videos.
However i would like to give vidix a try since everyone says it's so CPU efficient and i would also like to see what cvidix is like...

---

