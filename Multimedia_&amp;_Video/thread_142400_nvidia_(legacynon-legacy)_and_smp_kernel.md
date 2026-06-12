---
title: "nvidia (legacy/non-legacy) and smp kernel"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by killercow on 2006-03-10
Hi,

My workstation is an SMP machine on which i installed an smp-kernel.

On this system i had a legacy nvidia quadro 2 pro (and thus installed the nvidia-legacy-smp drivers), this didn't work as planned, as the module did not get loaded, and if i didn't manually select the extra needed packages it would install a normal kernel along with it.

Thus i simply used the nv driver, not a problem, since im a programmer, not an autocad whiz :P

The old card was getting a bit loud due to a broken fan, and i replaced with a geforce 4 mx4000,

This new card obviously needs the non-legacy drivers, ad thus i installed them, along with the rest of the needed packages.
After doing a modprobe, and a change in the xorg.conf to use the nvidia driver i restarted gdm,
Everything loaded, and i worked two days with that setup, (and thus shutdown for the night, and booted the following morning withaout a problem).

Now i booted the machine again this morning, but this time gdm would crash the moment it was loaded, i would see the usual xorg retry loop kick in, but to no avail.
The system hard-locks on the console with half the screen white, and a cursor in the top left.

Rebooting in safe mode, works like it should.

Changing the driver in xorg to nv works, and allows me to works.
doing an lsmod shows the nvidia kernel loaded as normal, and dmesg doesn't give me any errors, besides some spurious acks from my serial port.

I would be happy to work with the nv driver on this new card aswell, but as it turns out this new card gives me a couple of scanlines walking down the screen.

The scanlines exist every 5 cm's to the right, and are about 2 pixels high, and 100 pixels wide, they display what is being displayed about 10cms to the left of them.

The walk down about 5 cm's in one sec, and then jump back up.

They seem more evident, if there's a big color difference between the right side and lifet side of the screen, couse that will cause part's of the left image to be redrawn on the right side of the screen.

fiddling with the refresh rates and resolutions doesn't resolve this, altough i does increase the speed and amount of lines. (found no specific mode to make them less prominent)

Strange thing is, i also had these problems with this card when i had a 17" TFT hooked up to it. (also ubuntu, also nv driver)

any info on this?

---

