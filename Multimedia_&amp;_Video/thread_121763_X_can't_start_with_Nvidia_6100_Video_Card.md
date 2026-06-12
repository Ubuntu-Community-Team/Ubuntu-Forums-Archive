---
title: "X can't start with Nvidia 6100 Video Card"
date: 2006-01-25
forum: Multimedia &amp; Video
---

### Post by ewebull on 2006-01-25
I recently bought a computer.
CPU:AMD Sempron 2500+
Video Chipset: Nvidia 6100
-------------------
I tried to install Ubuntu 5.10 both x86 and 64bit editions.But X can't start everytime.
Any one can help me?:confused:

---

### Post by rjwood on 2006-01-26
need more info. When you say it does not start, does that mean that you get an error message? Does it bring you to the command line? If an error message appears, from the command line type 'sudo dpkg-reconfigure xserver-xorg' let x detect all the hardware and when it gets to video drivers choose 'nv'. When the process completes, just reboot--type 'sudo reboot'. See if that works for you and post the results here. Good Luck!!!

---

### Post by Sefianix on 2006-03-07
I'm having the same problem:
emachines T6216 AMD 64 nforce 410 with nvidia 6100 gpu

The ubuntu 5.10 install chooses the nv driver, however this fails.  (sorry, can't remember the exact error in the log.  Been having all kinds of problems with this machine; in the middle of a re-install.)

However, I do know that the vesa driver works.  not the best, but at least you can get X-windows up and running (and thus gdm/kdm as well).

I thought I could use the nvidia driver from Nvidia's website but the 6100 is not supported.  so i'm guessing it's not supported by the nvidia-glx driver in the repositories either.

btw, you might check out:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

when i'm done with my (re)installation, I might look into the nvidia-glx-legacy driver.  but I don't see the 6100 on that list either.

so does anyone know what driver can be used for the 6100 gpu that's better than the vesa driver??  :-k

---

### Post by Sefianix on 2006-03-08
posted to the following thread:
[http://ubuntuforums.org/showthread.php?t=119650](http://ubuntuforums.org/showthread.php?t=119650)

I got things working.

---

