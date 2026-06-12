---
title: "Lots of crashes,lock-ups, and restarts with nVidia driver on GeForce4 MX 4000"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Extreme Coder on 2007-08-26
Hello,
I installed the latest Feisty release, used the Restricted Drivers panel to install the driver for my GeForce4 MX 4000, and I installed all available updates.
But the thing is that the PC seems to be constantly crashing, either X crashes, or the whole PC. Sometimes it will just lock-up with no response at all. Sometimes it will just restart. Take your pick.

My system specs:
Soltek Motherboard with i865 chipset
P4 3.0 GHz with HyperThreading support
nVIDIA GeForce4 MX 400 128 MB graphics card
onboard sound
2 generic LAN cards


What makes me know the nVidia driver is the problem is that if I switch to the opensource "nv" driver, the PC is rock-stable with no crashes at all.
Although one of my friends suggested turning off the HyperThreading from the BIOS, I haven't tried it. Will it make a difference?

BTW, this happens also on the other distro I use, Mandriva. Same symptoms.


Thanks a lot for your help in advance,
Ahmad Yasser

---

### Post by K.Mandla on 2007-08-26
There may be a conflict between the default driver that's installed, and the one that your machine needs. Nvidia made a jump between drivers around four or five months ago, and left a lot of machines without proper support. I have the same problem with a Geforce4 440 Go.

You can try to manually uninstall the driver that Ubuntu used, and instead install *nvidia-glx*. You don't want *nvidia-glx-new*, or *nvidia-glx-legacy*. You'll have to check your machine to see which one is/was installed.

If that doesn't work for you it's possible to patch the 8776 driver against the newer Ubuntu kernels, and you get the last working driver (Edgy-era) that worked great with most Nvidia cards, before Nvidia made their switch. Here's a step-by-step set of instructions. ...

[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)

Good luck! ;)

---

### Post by Extreme Coder on 2007-08-26
I just tried installing nvidia-glx manually.
Still, same things. feels like the exact same driver I was using from the Restricted Drivers.
I'm going to try your compiling 8776 driver guide in a few minutes, as I don't think I need that DFP trick(since I already have a display)

Thanks!

---

### Post by Extreme Coder on 2007-08-26
[B]UPDATE:
[/B]Seems like HyperThreading is not the problem at all, since I just disabled it, and after 5 minutes of checking my e-mail, my PC locked up(with the Caps Lock and Scroll lock flashing). So now I KNOW it is the GeForce :/

---

### Post by Extreme Coder on 2007-08-27
Bump!
Anyone has an idea why this is happening?

---

### Post by K.Mandla on 2007-08-27
Did the rebuilt 8776 driver help at all?

---

### Post by Extreme Coder on 2007-08-27
I'm following your guide right now, but how would I immediately know if the lock-ups, X restarts/crashes are over?

Thanks again!

---

### Post by K.Mandla on 2007-08-28
Well, use it and see if they still happen, I guess. The only hope for curing the bad behavior is not to experience the bad behavior any more, I think. Aside from that, there's no real way of telling.

---

