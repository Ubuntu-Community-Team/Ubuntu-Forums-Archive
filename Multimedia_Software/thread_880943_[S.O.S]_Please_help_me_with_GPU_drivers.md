---
title: "[S.O.S] Please help me with GPU drivers"
date: 2008-08-05
forum: Multimedia Software
---

### Post by project6 on 2008-08-05
Hi.

I'm on the verge of giving up on Ubuntu right now. I think I tried ten various guides on installing Nvidia drivers and get the hardware acc. to work. Nothing seems to go my way.

The first thing I did was goind into hardware drivers and enabling them, leading to Ubuntu getting nvidia-glx-new and rebooting. If I do this, the screen gets no signal after reboot and I have to boot into recovery and reset X to get back.

I tried downloading Envy and letting it handle this, the same error occurs - no signal to my monitor.

I tried manually getting both nvidia-glx-new and nvidia-glx legacy as well as nvidia-glx, installing these and rebooting sets low graphic mode.

I have Ubuntu 8.04.1 and my GPU is a GeForce 6800XT AGP.

If I were to say what I think is wrong, my motherboard has both a PCI-E slot and AGP. Maybe the PCI-E gets priority somehow, although it's empty and the AGP is what should be used. I'm not sure though, and have no clue how to handle that anyway.

Please throw me some carrots here. I'm not too familiar with the Linux way, but after spending a day with these issues I've become familiar with some of the more common syntaxes and how to edit xorg.conf, how to get packages with apt-get or Synaptic etc.

S.O.S :-({|=

/p6

Edit: details on my GPU

```
$ lspci -n | grep 0300
01:00.0 0300: 10de:00f6 (rev a2)

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6800 GS] (rev a2)

```

---

### Post by xc3RnbFO8P on 2008-08-05
I have been searching this card,
and my advice is buy a new one.
[http://ubuntuforums.org/showthread.php?t=605460]("http://ubuntuforums.org/showthread.php?t=605460")

---

### Post by project6 on 2008-08-05
*snap* my usual bad luck. :(

Thanks for the link anyway, now I don't have to feel like an idiot not getting it to work.

---

