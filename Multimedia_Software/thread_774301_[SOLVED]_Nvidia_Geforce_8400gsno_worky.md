---
title: "[SOLVED] Nvidia Geforce 8400gs????no worky????"
date: 2008-04-29
forum: Multimedia Software
---

### Post by rmhamm on 2008-04-29
Okay so I'm new to ubuntu. well sort of anyways I built a computer and installed our favorite os and all was well. Then something went horribly wrong!!!! I installed a Nvidia Geforce 8400gs 512 card in a pci express slot and it doesn't really work. It will go into low graphics mode only. I tried enabling and disabling proprietary drivers through the hardware support. Then tried downloading the drivers from the website and I have absolutely not idea how to get it working. Is this just a bad card for ubuntu??? any fixes???? am I doing something wrong?

specs are:
asus motherboard
amd dual core 2.8 (64bit but I running 32bit ubuntu)
2 gig of ram
and problem card.
ubuntu 8.04 32bit ubuntu gnome

*****Solved I guess*****
I kinda did this by accident and I guess it is the same thing really as damis648 said to do but I booted into recovery and did a recovery of the xconfig or xserver or something like that and when I booted back up into generic all was gravvy. So if that helps anyone then cool but I'd seek more detailed and in depth answers than this one. Stumbling across a solution is not a good as knowing how to fix it on purpose. I'm currently enjoying all of the desktop effects and functionality.

---

### Post by ihavenoidea on 2008-04-29
Hmm i just built one with this card too and my 7.10 32 bit wont even get any graphics up, i would be very interested to see how this plays out.

---

### Post by damis648 on 2008-04-29
Try downloading the official Nvidia driver: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
and select the 169.12 driver for your platform.

After you have downloaded it, move it to /home and rename it to nvid.run.

Now, close all applications and press ctrl+alt+f1 to drop back to terminal.

Now to stop the X server type
```

sudo /etc/init.d/gdm stop
```

then just run

```
sudo sh ./nvid.run
```

and follow the directions to install the driver. Let it automatically reconfigure the xorg.conf.

---

