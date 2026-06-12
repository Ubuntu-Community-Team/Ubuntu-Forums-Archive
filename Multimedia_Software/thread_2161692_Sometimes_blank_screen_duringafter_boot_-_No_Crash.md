---
title: "Sometimes blank screen during/after boot - No Crash, System responding,X works"
date: 2013-07-11
forum: Multimedia Software
---

### Post by christian2002 on 2013-07-11
Hello,

I hope this is the correct forum for my problem.

I have Backtrack 5r3 installed which builds on Ubuntu 10.04.
Hope you can and want help me, because its Backtrack ;-)))

I'am very new to linux and a friend set my Videosettings for the TEXTMODE (Terminals) to the Framebuffer, so i can see more on my small 1024x600 netbook screen.
This works most time very fine, but sometimes the system boots with a blank screen and i can't see anything on the Terminals.

But, i can log in and start X. (I need to make this blind)

Gnome starts without any problems. The xorg driver loads normally and i can use the system (Only in Gnome) normally.
But the text Consoles are all blank :-(

I can't reach my friend the next time, so i'll try it myself :-)

The Kernel Version is 3.2.6
Its a Via Unichrome II Pro IGP Videocard.

Modprobe shows me "viafb" als loaded driver.
I think, this is the framebuffer driver for my Via Card.

I tried the "nomodeset" in grub. This works fine, but now i have only 40-50 rows in the Terminals. 

Perhaps someone can help me,

I'll try to provide all information needed. But at this point, i dont know which info is needed ;-) Sorry, iam very new to linux :D

Greetings

Chris

---

