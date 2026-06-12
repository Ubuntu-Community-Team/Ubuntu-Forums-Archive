---
title: "Can't use text console unless I stop gdm..."
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by Keyper7 on 2007-06-15
Hello everyone, long time reader but first time poster here. Before I ask my questions,
I feel obligated to thank the community here for all the ready answers I could find in
this forum so far. And they were more than a few, so thanks. ;) Anyway, here it goes:

PROBLEM:
Machine completely freezes in a blue or red screen if I try to switch
to a text console. Can't go back to graphical mode with CTRL-ALT-F7
and can't type commands blindly: it's really frozen and the only thing I
can do when that happens is use the power button.

CONTEXT:
- HP Pavilion dv6258se (Turion X2, NVIDIA GeForce Go 6150)
- Ubuntu Feisty Fawn with updated kernel (2.6.20-16-generic)
- NVIDIA proprietary driver installed through restricted manager
- webcam, usb, media buttons, touchpad, lightscribe all working
- two cores detected, powernowd and laptop-mode enabled
- needed noapic noirqdebug to install (more on that below)

OBSERVATIONS:
- I can use the text console if I boot in text mode or if I simply stop
gdm. Apparently, the problem is just on switching.
- Problem does not happen if I boot with noapic noirqdebug. I
needed those to install the livecd, but after upgrading the kernel
and installing the drivers I found out I could boot without those
parameters. So I removed them, because without APIC one of
the cores would go crazy handling hardware interruptions.
However, I recently found out that putting them back on allowed
me to switch to text console again.
- Beryl is not installed yet and desktop effects are not enabled
(in fact, I can't switch to text mode even from the login screen)
- booting without splash or with vga=normal had no effect

WORTH TO MENTION:
- If I remember correctly, the restricted driver manager installs
nvidia-glx. I've tried nvidia-glx-new in a previous installation and
got the well-known "garbled screen of death" (text terminal is
garbled but if you type blindly the commands will work and
CTRL-ALT-F7 also works). Better than hanging, perhaps, but 
it happened in all contexts, even with noapic noirqdebug and
even when I stopped gdm.
- Suspend and hibernation are working perfectly, which
surprised the hell out of me.

So... what seems to be the problem? :(

Thanks in advance,
-Keyper7

---

### Post by iqag1060 on 2007-06-19
I have the same problem but specifically only with Desktop Effects enabled. (This seems to be the same as [this]("http://ubuntuforums.org/showthread.php?t=213341&highlight=compiz+screen+freezes+on+switch+to+console") unsolved thread.)

---

