---
title: "No X at all"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by squirrelplayingtag on 2006-01-29
I just attempted an install of Ubuntu 5.10 after fighting with Debian to get X to start and not having any luck. I didn't do anything special with the installation but when X tries to start it just goes to a black screen. No errors and I don't get dumped into the terminal.

Now ussually I'd provide some information about my video card, but I'm in another sticky situation. I acquired this computer from work since they got a new one. It was running Windows 2000 and worked fine when I got it. I have installed WinXP to make sure the video card wasn't completely screwed and everything worked fine. I have been able to find very limited information on it. I can't even locate a serial number for the computer, only certain parts (hard drive and power supply mostly). But it's a compaq Deskpro EN pIII. It looks like just the standard Compaq VGA controller. (It's integrated).

---

### Post by MartinG on 2006-01-29
Try the command "discover video" (discover should be part of your base install), and this should tell you what video card/controller you've got.

---

### Post by squirrelplayingtag on 2006-01-29
Well, it uses the Intel Corporation 82815 CGC and my xorg.conf uses the i810 driver.

---

### Post by MartinG on 2006-01-29
Try running dpkg-reconfigure xserver-xorg with different values (especially framebuffer or not).  Do this from a console log-in.

---

### Post by squirrelplayingtag on 2006-01-29
I tried using the vesa driver instead of the i810 which gives me vertical colored lines. I turned off frame buffering and left everything else as the default.

---

### Post by squirrelplayingtag on 2006-01-29
Problem sorta solved. Somethings messed up with the monitor. Tried a new monitor and it worked so I went to another old monitor I had laying around and that worked as well.

---

