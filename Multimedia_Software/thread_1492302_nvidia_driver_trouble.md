---
title: "nvidia driver trouble"
date: 2010-05-24
forum: Multimedia Software
---

### Post by onsager on 2010-05-24
Hello,
I have an odd problem, but wont find the solution.. I have an nvidia 7600gs video card, and a fresh installed ubuntu lucid. I tried to install the nvidia-current driver from System->Administration->Hardware Drivers, it sets up the driver and asks for reboot. After reboot the boot process happens, but the monitor turns off (i am able to log in after ctrl+alt+F1, but after switch back to desktop: black screen again , after continuous pushing of ctrl+- buttons I am able to get a distorted image, but cannot read anything on it...)
The only way to have the desktop back if to reset the xorg.conf, purge nvidia* and restart.
So how can I use the nvidia drivers to have a hw acceleration?
BTW whats the difference between the three nvidia drivers? Can be any other good for me? 

thanks.

---

### Post by Failboat88 on 2010-05-24
I have had this happen to me when setting up tv-out. If you don't think that's a possibility; make sure your connection is in all the way. You would have trouble seeing your bios if it had something to do with your plug.

---

### Post by onsager on 2010-05-25
> **Failboat88 said:**
> I have had this happen to me when setting up tv-out. If you don't think that's a possibility; make sure your connection is in all the way. You would have trouble seeing your bios if it had something to do with your plug.

At startup the bios and the grub are OK, but as soon as the boot process starts the monitor switches off. But as soon as you push ctrl+alt+f1 the terminal comes out, so my proplem is with the video driver and the X...
Without nvidia driver everything seems to be ok, but if you would see something on youtube the cpu goes to 100%, and the stream goes sluggish. By seing videos the same happens, so I think I should use HW acceleration somehow...

---

