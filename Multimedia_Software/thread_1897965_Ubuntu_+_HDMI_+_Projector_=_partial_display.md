---
title: "Ubuntu + HDMI + Projector = partial display"
date: 2011-12-20
forum: Multimedia Software
---

### Post by PeterTaps on 2011-12-20
Folks,
 
I have Ubuntu 11.10 desktop version on my machine. The motherboard supports on-board HDMI 1.3a. My projector also supports HDMI 1.3a. When I connect the HDMI output of my server to the projector, I only see top half of the screen. On the login dialog box, I can see username field but password and everything else is not seen.
 
Occassionally, I also see a screen flicker although I do not touch anything.
 
If I replace this machine with another that is running Windows 7, there is no problem. The screen appears to be normal.
 
I don't understand this behavior. Is it possible that my Ubuntu video settings have some bogus values?
 
I would appreciate your help in resolving this problem. Perhaps I can simply delete some video configuration file that Ubuntu can rebuild on reboot.
 
Thank you in advance for your help.
 
Regards,
Peter

---

### Post by BicyclerBoy on 2011-12-20
It will help if you can reveal the computer h/w chipset & graphics.

This could be close:
lspci
xrandr


Are you using the projector as the only display?

The boot/greeter screen may not be using the correct driver or video mode..

---

### Post by PeterTaps on 2011-12-21
Thank you for your help.

The motherboard is Intel Desktop DH67BL. The projector is for TI and supports HDMI 1.3a. I don't have the model number as I am away from the computer.

I will try out the commands you suggested.

Regards,
Peter


> **BicyclerBoy said:**
> It will help if you can reveal the computer h/w chipset & graphics.

This could be close:
lspci
xrandr


Are you using the projector as the only display?

The boot/greeter screen may not be using the correct driver or video mode..

---

