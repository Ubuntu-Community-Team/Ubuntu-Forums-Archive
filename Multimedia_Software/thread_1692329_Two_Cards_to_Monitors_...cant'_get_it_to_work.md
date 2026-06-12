---
title: "Two Cards to Monitors ...cant' get it to work"
date: 2011-02-21
forum: Multimedia Software
---

### Post by porridgeorange on 2011-02-21
Hello All,
My problem is as follows I have an NVIDIA 730a MB with a GeForce 8200 nGPU as my onboard and a GeForce 9800GTX+ discrete motherboard dual booting Windows XP pro and Ubuntu 10.10 64 bit. I have one monitor (and old MEGAVISION junker) plugged into the onboard video and the other a pretty nice ACER 21 inch monitor in the 9800 GTX+. I have read through all of the forums trying to get both of these to display to no avail. the Nvidia Settings console shows the Acer as disabled but when i try to enable it  the twinview option is disabled. I activate it using a separate screen config write tot xorg file and reboot. However, when I reboot i just get the command prompt. I can get back to my graphic display by running the NVIDIA install utility and re-writing the config file but that only gets me where I started with on monitor only. I got the proper x64 driver from the NVIDIA site. Any help would be appreciated. if it helps here is a look at what the config file looks like before and after I change the settings:

---

### Post by ACMarina on 2011-02-21
The 9800GTX+ has two outputs - why use the onboard for the mobo when you can just run both off monitors from the video card?

---

### Post by porridgeorange on 2011-02-22
The 9800 does not have a VGA output only HDMI and my older monitor is VGA. Besides, the 9800 is the card I'm currently getting no output from. Thanks

---

### Post by ken_23434 on 2011-02-28
I have no experience with Ubuntu and dual displays.
 
I would disconnet the VGA monitor and the boot up the computer.  Does Ubuntu see the 9800 now?
 
If so, I would use a DVI to VGA adapter and plug in your VGA monitor into the 2nd port of your 9800.  (My 9800GT has 2 DVI outputs, but come with a DVI to VGA adapter and that is how my monitor is hooked up).
 
You might need to disable the integrated video in the Bios.  I did not disable the integrated video on my computer, and Ubuntu is only showing the Discrete video.

---

