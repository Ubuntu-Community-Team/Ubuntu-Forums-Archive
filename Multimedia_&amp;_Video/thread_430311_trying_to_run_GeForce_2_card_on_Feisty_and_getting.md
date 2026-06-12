---
title: "trying to run GeForce 2 card on Feisty and getting nowhere fast!"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by sansrage on 2007-05-02
Hey People! I've just gotten my old college computer back up and running and since M$ can't support Win98SE anymore I decided to go with Ubuntu Feisty. (I'm running a P3 500 mhz, 256MB ram, 12 gb hd, and a GeForce2 64MB)

When I first started with the Live CD, it wouldn't go beyond the black screen and not knowing much about Ubuntu after pulling my hair, I decided to pull the GeForce card out instead, and the CD loaded up just fine!! Now, everytime I decide to plug the card back in, I just get a black screen. I've installed the restricted pack from the application/add-remove and I've installed the nvidia-glx-legacy drivers from the add-remove too. after typing in the sudo commands like the description box for nVidia driver says, the terminal pauses for a few moments, and goes back to the empty line of text.
But I'm doing this all without the card in the PC....which isn't right, is it?

I've re-installed the GeForce2 and booted into recovery mode and inputted the commands to get/install nvidia legacy drivers.I then tried to modify the xorg.conf drivers to say "nvidia" instead of "nv" but I haven't even made it that far!! What "Device" line are they referring to? and does it need to carry throughout the xorg.conf? I'm so noob and stupid when it comes to this part. Instead of anything nVidia, the device section reads:

Section "Device"
Identifier "Intel Corporation 82810 PC-100 CGC [Chipset Graphics Controller]"
driver "i810"
Busid "PCI:0:1:0"
EndSection

What do I do? I'm pretty sure I need to install the GeForce2 card before installing (or uninstalling) the drivers again. But if the black screen pops up again, how do I get around it? Or what do I need to do after writing the xorg.conf?

I'm so freaking confused at this point. I'm just not following what I've been reading but I'm not ready to re-install Windows again.

Thanks!!

---

### Post by MilosDusan on 2007-05-02
Eh.. That looks like it's reading an 'on-board' video chip.. 

Regardless, try this..

In console, type:
```
uname -r
```

That will show the kernel version you need for your restricted module pack..

then type:
```
sudo apt-get install linux-restricted-modules-x.x.xx-xx-xxx
```

where the x's are the kernel base you have (2.6.15-17-686 for example)

Since you have a GF2 card, run the legacy pack

```
sudo apt-get install nvidia-glx-legacy
```

Edit your /etc/X11/xorg.conf and look for a line the says something like:

```
Driver      "nv"
```

and then edit it to specify the nvidia driver:
```
Driver      "nvidia"
```

Hit Ctrl+Alt+Backspace to kill X and log back in... As X restarts, you should then see a NVidia logo show up.. 

Once in, open terminal again, and type:

```
nvidia-settings
```

The rest should be cakewalk ;)

---

### Post by sansrage on 2007-05-02
sweet!! Thanks for the quick response! I tried running those commands first thing this evening and after I downloaded the nVidia legacy pack and inputted the commands, I couldn't find anything in xorg except the onboard Intel thing. Which threw me off....I couldn't see ANY device that read "nv" or anything. I thought for sure I was in the wrong place. I wrote it out the best I could to try and force it, ya know, but it showed me who was the boss!!

---

