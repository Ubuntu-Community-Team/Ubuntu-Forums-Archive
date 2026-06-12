---
title: "[SOLVED] Screen resolution with ATI video card."
date: 2009-01-05
forum: Multimedia Software
---

### Post by garrydog on 2009-01-05
Hi
I have been trying to fix the screen resolution problem omn my computer for days ,and nothing seams to work .My display is stuck on 800x600 or 640x480 ,If I load the ATI/AMD prorrietary FGLRXT grapgics driver ,then the monitor go's black with "cannot display this video mode",i get the moniter working agian with XFIX .I am now totally lost and do not know what to do to fix this ,can someone help please .

my video card i s a ATI RADEON HD 2400 PRO RV 610 .
Tanks .

---

### Post by bapoumba on 2009-01-05
Post moved to its own thread (to the OP: you posted in a solved thread, which was unlikely to bring you answers), moved to Video and title edited.

---

### Post by Tom Tiger on 2009-01-05
> **garrydog said:**
> Hi
I have been trying to fix the screen resolution problem omn my computer for days ,and nothing seams to work .My display is stuck on 800x600 or 640x480 ,If I load the ATI/AMD prorrietary FGLRXT grapgics driver ,then the monitor go's black with "cannot display this video mode",i get the moniter working agian with XFIX .I am now totally lost and do not know what to do to fix this ,can someone help please .

my video card i s a ATI RADEON HD 2400 PRO RV 610 .
Tanks .

Same problem here.... I get the black screen of death after upgrading my videocard to an ATI XT2400.... I removed compiz but it doesn't help...

I'm running Intrepid and I really REALLY hate that I can use the old dpkg-reconfigure xserver-xorg anymore....  I just want my resolution to be set at 1280X1024, which my monitor supports.... and xrandt keeps saying my display can't be opened.... even after stopping gdm....

Anyone a solution, I'm running out of ideas here....

---

### Post by Tom Tiger on 2009-01-07
Never mind, I allready fixed it.  I went back to the xorg.conf.failsafe. Xorg now starts in vesa, problem solved :-) 

Then I did an upgrade check, 8.10 came with xorg-ati and radeon drivers :-),  did that, went to synaptic to install compiz, restarted, activated the restricted drivers, restarted, activated advanced desktop effects and, back to my old desktop, with all the eyecandy and extra stuff :-)

So my problem solved.

---

