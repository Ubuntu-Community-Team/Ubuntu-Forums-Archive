---
title: "nVidia GeForce FX5200"
date: 2008-06-19
forum: Multimedia Software
---

### Post by jedi22 on 2008-06-19
Hey Everybody.

I've had a nVidia GeForce 5200FX for a while without 3D acceleration.  Long story short, I would much like to have it working.

I have tried installing the drivers from the repos and using the restricted drivers and enabling some basic animations but when I reboot it works for about 3 Seconds then crashes!

Is there any way I might be able to get this card to function properly in my computer.

---

### Post by jrusso2 on 2008-06-19
I know that card uses the legacy nvidia drivers so make sure those are the ones you have.

---

### Post by jedi22 on 2008-06-19
How would I go about installing and using those drivers?

---

### Post by feenicks on 2008-06-19
Have you tried installing with Envy?  I'm using an old 4400 card and that worked okay.  However, I can't run it at any 16:9 resolutions.

---

### Post by jedi22 on 2008-06-20
So I install the Envy drivers then see if my card supports direct rendering?

---

### Post by Wabla 123 on 2008-06-20
hi im not too sure how to fix your problem but im having a problem of my own.
i have Ubunut 8.04 on my computer and i have an nvidia GeForce 4 graphics card but when i was finnaly able to install the driver with envy i get this massive black bar cuttin off about 2 centimetres of my screen on the right and my whole screen looks like its been zoomed in.
 Its really buggin me and if someone knows how to fix it id really apreciate the help ;)
thanks

---

### Post by jedi22 on 2008-06-20
Ok I installed the drivers using automatic hardware detection with envy and now I have 3D effects working except it basically crashes when I use them(1 frame every 20 seconds).  Anybody have any ideas?

---

### Post by aeiah on 2008-06-20
i have an fx5200 in my bedroom pc and have no problems with the restricted drivers (although i dont run compiz) and i have no problems running at 1440x900 resolution. its running xubuntu 7.10 for what its worth, and the driver is just from the restricted driver manager thing. have you tried launching compiz from the terminal? what errors does it throw at you? have you considered tracking down some kind of hardware fault checking software to see if its actually faulty? it must be a pretty old card.

---

### Post by Victormd on 2008-06-20
I used an FX5200 with Gutsy and never had a problem with it... Now I've upgrade (graphics card and distro) and again, no problem. Though I never got to use the FX5200 with hardy, I have seen a lot of posts complaining about it...

I would try Envy-NG (envyng in the repos) and see if that works.

---

### Post by Pjotr123 on 2008-06-20
You definitely do *not* want to use Envy for an older card that needs the legacy driver. Envy is an emergency measure for *brand new* cards that need the very latest driver from Nvidia.

Do this:
- remove the Envy driver (back to the nv driver)
- reboot
- System - Administration - Hardware Drivers
and follow the instructions.

Afterwards, disable the 3D visual effects. Too taxing for this old card.

---

