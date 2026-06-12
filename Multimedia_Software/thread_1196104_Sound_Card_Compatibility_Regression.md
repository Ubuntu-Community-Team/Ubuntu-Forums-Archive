---
title: "Sound Card Compatibility Regression"
date: 2009-06-24
forum: Multimedia Software
---

### Post by Scouto2 on 2009-06-24
Hi,

My sound card is no longer compatible with Ubuntu. I just recently updated ubuntu (I believe 47 packages), as directed by the updater that popped up. Now, my sound card does not work.

What can I do to alleviate the situation?

UPDATE (No pun intended!):
Okay, I just loaded the live CD of Jaunty Jackalope (9.04), and lo and behold, the sound works fine! I played some music also on it and it works great. Is there any way (short of rewrite of disk) that I can copy the sound-related settings over to my harddrive from here? I think I have this solved.

---

### Post by Scouto2 on 2009-06-25
Bump.

---

### Post by tixetsal on 2009-06-27
Ditto on this.  Only one of my two jaunty boxes did this.  My intel machine with ASUS P5N-7AVM MOBO took the update fine, but the ECS MOBO w/geforce 8200 chipset, can't detect sound card after updates.  We need to file a bug report.

---

### Post by tixetsal on 2009-06-27
I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel. I have another box with Asus P5N7A-VM MOBO, and this bug did not effect that machine. My AMD geforce 8200 will not play nice with 28-13 though. My sound card shows up in lspci, but aplay -l tells that I have no sound card.

---

### Post by raboofje on 2009-06-27
> **tixetsal said:**
> I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel.

That is good information!

On 2.6.28-13, which kernel module is providing support for your sound card?

One way of finding out is doing 'lspci -v', look for the section describing your sound card. Perhaps just paste all of it here? It should contain something looking something like

```
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
```

---

### Post by tixetsal on 2009-06-27
raboofje,

lspci -v on 2.6.28-13 yields:

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2646
	Flags: 66MHz, fast devsel, IRQ 21
	Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

lspci-v on 2.6.28-11 yields:

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2646
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

*UPDATE*

So, I noticed that there was no kernel driver in use in 2.6.28-13.  I also noticed that I should have sudo'd, so i rebooted in order to load 2.6.28-11, and I daydreamed a bit and missed the grub menu.  When the login screen was rendered, BEHOLD, i heard the drums!  

Now, sudo lspci -v in 2.6.28-13 yields:

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2646
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

raboofje, thanks for your help.  There was no Kernel Driver in use, for some reason, and now things have "magically" been fixed.  Does anyone have any theories as to why this occurred?

*BAD NEWS*

After a reboot I am without sound again, and sudo lspci -v shows that there is no kernel driver in use again.  What in the world is going on?

---

