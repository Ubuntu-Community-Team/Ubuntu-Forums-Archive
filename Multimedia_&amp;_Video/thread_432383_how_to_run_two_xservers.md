---
title: "how to run two xservers"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by forchessonly on 2007-05-03
I want to be able to run some older windows95/98 games in wine or cedega. The problem is that some of them require 256 color mode, or run normally in 256 color mode at 800x600 resolution, so that when you try to run them in wine or cedega there is a huge performance hit when converting those games to a 1600x1200 and 24 bit mode. I've heard it's possible to run another xserver (xserver, is that right?)  at the same time, that runs at 800x600 and in 8-bit, 256 color mode. Supposedly, games like starcraft will run much faster if my xserver is running in 8bit color mode and a lower resolution. Does anyone know how to configure this type of setup?
 
I'm running dapper drake 6.06 using gnome.

Any help would be much appreciated, thanks.

---

### Post by blackened on 2007-05-04
Woudl lowering the current instance of X to 800x600 with 256 colors not accomplish the same thing?

If so, then you could just alter xorg.conf accordingly.

---

### Post by forchessonly on 2007-05-04
Then I would have to restart my computer every time I wanted to run a game. That wouldn't really be worth all the effort. If I set up another user does that user have its own xorg.conf file?

---

### Post by bukwirm on 2007-05-04
Examine the xinit command (ie, run "man xinit")

---

### Post by blackened on 2007-05-04
> **forchessonly said:**
> Then I would have to restart my computer every time I wanted to run a game. That wouldn't really be worth all the effort. If I set up another user does that user have its own xorg.conf file?

Could you not just change the resolution in your current session and run sudo /etc/init.d/gdm restart?

---

### Post by forchessonly on 2007-05-06
I don't know. Once I run either "sudo /etc/init.d/gdm restart" or "man xinit" will my color depth be 8bit? And once I'm using 8bit color do I just run the same command to return to my initial resolution and color depth?

---

### Post by blackened on 2007-05-07
> **forchessonly said:**
> I don't know. Once I run either "sudo /etc/init.d/gdm restart" or "man xinit" will my color depth be 8bit?
Not sure, try it and find out.

> And once I'm using 8bit color do I just run the same command to return to my initial resolution and color depth?

"man xinit" will only show you how to use the xinit command, but, in theory, changing settings back to the original and restarting gdm should take you back to the original resolution. It shouldn't hose anything to try it out.

---

### Post by iLoVe.cF- on 2007-05-07
hey.. i know what ya talking bout..


Starcraft right ?

Hehe..
 ive tried to 8 bit 640x480 res stuff.. DOESNT DO IT AT ALL.. ive tried several other games on this comp running smooth.. starcraft is just a game atleast i push too hard.. and i notice the slightest lagg xD..

And at 250and sometimes even 400 APM(Actions per minute) thats when you can set up a telt/tent between every frame :D


But.. I think.. dual x one without compositing would work.. since .. i just smashed in a 120 gb hdd for my laptop that i got as a spare hdd.. installed a old linux 5.04 updated abit installed new wine and cedega
cedega had best results though..

That worked MUUUUUUUUCH better..

---

