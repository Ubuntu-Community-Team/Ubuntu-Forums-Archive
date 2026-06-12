---
title: "Should I run aticonfig --initial?"
date: 2009-12-04
forum: Multimedia Software
---

### Post by Col-1023 on 2009-12-04
I'm running jaunty 64 bit with an ati 4870 card and I installed the proprietry ati drivers when I upgraded from intrepid

I believe the drivers are properly installed since if i type glxgears, i get the three rotating cogs and framerate.

I want to measure the temp and set fanspeed of my card if the temp is too hgih, so I need to use the aticonfig command.

When I run this command in the terminal, I get a message saying I need to run aticonfig --initial to change an xorg file.

I've read horror stories about messed up xorg files, so I'm wondering whether running this command on my system will mess up my graphics.

I'm happy with the graphics setup, I just want to make sure the card isn't overheating.

I DON'T overclock anything.

Any help appreciated.

---

### Post by Col-1023 on 2009-12-07
fglrxinfo produces this.


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series 
OpenGL version string: 2.1.8575

Jaunty says the proprietary drivers are activated and in use.

When I type the aticonig command to show the temp of the card, I get a reply saying I should run aticonfig --initial.

I thought you only had to do this if your were installing the drivers by terminal, not with the ubuntu hardware drivers gui.


As in my previous post, what I want to know is will running the aticonfig --initial command cause problems for my xorg.

Any help appreciated.

---

### Post by Yellow Pasque on 2009-12-07
IIRC, aticonfig backs up your xorg.conf, but you can back it up manually (if you even have an xorg.conf) just to be safe.

---

### Post by Col-1023 on 2009-12-09
thanks Temujin for your reply.

I read that aticonfig backs up the xorg file, but if the graphics system is trashed, how would I go about restoring the system with the command line?

Is this a very easy thing to do, or is it a real pain in the ****?

---

### Post by Col-1023 on 2009-12-21
I upgraded to karmic, ran the aticonfig --initial -f command and was able to get the fanspeed and temperature of my cards.

aticonfig had no bad effects on my system.

---

