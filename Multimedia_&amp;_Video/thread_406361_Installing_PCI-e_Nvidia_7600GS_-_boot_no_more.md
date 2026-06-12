---
title: "Installing PCI-e Nvidia 7600GS - boot no more"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by yves on 2007-04-10
I am running a 6.10 system with on board Nividia 6100 chipset.

Installed a brand new XFX card, Nvidia 7600GS PCI-e card and Ubuntu stop at the line : boot !

The card works OK when I dual boot on winXP. I knew I could get weird display behavior with Ubuntu, but not being able to boot at all !!

I have a Knoppix boot partition that worked before and after the install of my knew card.

So what should I do from here ?  How to proceed when one wants to install a new video card ?

---

### Post by barney_1 on 2007-04-11
Here's what I would do If I were you.  It may not fully fix the problem, but should get you started in the right direction:

Reboot your computer.  The GRUB menu should load (you might have to press ESC to get it to display):  Choose "recovery mode".

This will boot the computer to a black and white console.  Once you get to the console type:

```
sudo dpkg-reconfigure xserver-xorg/CODE]

Go through the configuration program that starts and make sure that when asked about your video driver you choose nvidia (might be just "nv").

Once that is done type:
[CODE]exit
```

This should start X for you.  Once you are back in, I would suggest downloading the "envy" script that tselliot wrote.  This is a script to automatically install the newest nvidia or ati drivers.

Good luck!

---

### Post by yves on 2007-04-13
Thanks, but I tried that. My problem seems to happen way before X come into play. The boot process, with recovery mode,  jams with :

PCI : Bridge: 0000:00:10.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
NET: Registered protocol family 2


and that's it.

The none recovery mode,  since it boots in quiet mode, just shows : boot.
The splash screen doesn't even come up !

---

