---
title: "I fubared my display options"
date: 2009-04-25
forum: Multimedia Software
---

### Post by UltraZone on 2009-04-25
So.... I managed to fubar my display options...  Here's the story, last night I decided to plug in my laptop to my 720p tv to watch a movie, had to adjust the resolution with Nvidia X Server Settings.  No problem so far.  Afterwards, I had trouble going back to the native laptop resolution (1920x1200).  Anyway after extensive searching the forums I found the way to edit the Xorg.conf and everything seem to be ok.  So this morning I decide to upgrade to Jaunty.  Now the problem that I have is that after I restart, the display resolution goes to 320x240.  The weird thing is that the log in screen is in the proper resolution, yet after I log in the resolution gets switched to the lowest possible.  Now using the keyboard I'm able to launch Nvidia X Server Settings, and scoot the window so that I can change the resolution to the proper format.  So after I change this I click the "Save to X Configuration file" but I get an error that it cannot create the backup file.  So as a workaround I had the genius idea of to "gksudo gedit /etc/X11/xorg.conf" and just copy and paste in the text that the preview button in the X Server Settings shows.  This does not work.  

So in summary, I tried editing the xorg.conf file but nothing seems to work.  In fact I'm pretty confident that I messed it up. \\:D/ And I'm pretty sure that I messed up the backup copies that it made. 8-[=D>

Everytime I restart the computer the resolution goes back to 320x240, altough the log in screen appears normal.

Does anybody have clue how to make the X Server Settings "stick" for good?

Here's the specs of my puter:
Dell M1710
Jaunty 32-bit
NVidia GeForce Go 7900 Gs
Graphics Drivers: 180.44

If possible somebody could post the "clean" Xorg settings as I had to graphics issues whatsoever when I installed (for the first time) Intrepid.

---

