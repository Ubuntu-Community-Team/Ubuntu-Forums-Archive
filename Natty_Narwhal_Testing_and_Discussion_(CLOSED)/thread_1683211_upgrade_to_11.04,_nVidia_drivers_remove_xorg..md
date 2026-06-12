---
title: "upgrade to 11.04, nVidia drivers remove xorg."
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dsevastakis on 2011-02-07
hello everyone! i have i little problem with my ubuntu setup! I decided to upgrade to 11.04, everything went smooth, until i had to install the nvidia drivers.. i rebooted only to find that the xorg had been removed, so i had to boot in terminal mode.. i did 
"sudo apt-get install xorg" and then rebooted.. logged in normally.. but the nVidia drivers had been uninstalled -.-   any ideas?

---

### Post by Kirboosy on 2011-02-07
I would not recommend upgrading to 11.04. The new Alpha version has seemed to break more than its fixed. For now I would recommend going back to 10.10

---

### Post by adriangonsalves on 2011-02-09
I had the exact same problem after upgrading to 11.04 Alpha2
I still dont have a solution but there is a work around.
Get to the terminal (Ctrl-Alt-f1) and login as root.

make sure you have the opensource version of nvidia driver (nouveau)

just install -

apt-get install ubuntu-desktop

this should install xorg srever back again.

then make sure that xorg is configured to load nouveau driver.

in 

/etc/X11/xorg.conf 

change "nvidia" to "nouveau"

restart now and you should be able to get a GUI.
you can also install nouveau 3D experimental package for 3D acceleration which seems to work well for me (nvidia 9500 GT). Howver nouveau seems to be having no capability to control fan speed so the fan runs at a max speed which is very noisy.

This seems to be a big deal breaker for me.  Without fan speed control the machine is extremely noisy. I hope this gets fixed soon.

---

### Post by mabloom on 2011-02-13
I've also got that problem, but the ''nouveau'' workaround does not cut it for me.

I've got some vertical line artifacts that make using the screen unpleasant, but worse than that,  when I try to set up a second monitor and set it to it's native geometry of 1280x1024,  Xorg seems to get a SEGV and restarts, then gets a SEGV and restarts, ad infinitum.

10.10 would have been OK, if only hplip at that level worked correctly with my printer.  The 11.04 hplip does work correctly, but with 11.04 I'm stuck with my ten inch 1024x768 HP tablet screen.

SO, I've got either a good display or a good printout, but not both.  I also tried just installing the 11.04 hplip,  but the act of doing so tries to upgrade 10.10 to 11.04.

It's a catch-22 for me (Hey, Zelmo!)

---

### Post by bprins on 2011-02-13
Same problem here. Nvidia current, 3d experimental driver, both result in a desktop that does only have a menu bar at the top of the screen. 

No unity bar to the left, no widget for system icons. Quite annoying.

I'll leave 11.04 til it goes beta and try again I guess.

---

### Post by Ryland on 2011-02-15
I have had the same issues with latest alpha 2. I hope it get fixed soon.

---

### Post by drs305 on 2011-02-15
Thread moved to Natty Narwhal.

---

### Post by keypox on 2011-02-15
> **bprins said:**
> Same problem here. Nvidia current, 3d experimental driver, both result in a desktop that does only have a menu bar at the top of the screen. 

No unity bar to the left, no widget for system icons. Quite annoying.

I'll leave 11.04 til it goes beta and try again I guess.

Just waiting for nvidia driver support.

---

