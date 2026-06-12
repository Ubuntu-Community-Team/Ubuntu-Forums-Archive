---
title: "sound card apparently stopped working"
date: 2009-06-15
forum: Multimedia Software
---

### Post by eheitner on 2009-06-15
Hi. I have a dell xps m140, been running ubuntu for a year or so, not had any problems similar to this in the past.

My sound card apparently stopped working.
All I get is sort of a low buzzing/sputtering sound when I try to play any sound file or when firefox tries to play sounds. The sound settings are all on "autodetect", where they've been, but none of the options for various interfaces seem to improve the situation. It is the sound card and not the speakers because the audio-out jack also produces the same sputtering buzzing sound.

Any thoughts?

---

### Post by kopus on 2009-06-16
I have the exact same problem. It just happened for no reason. Any one else having this problem? Possible solution?

---

### Post by kopus on 2009-06-16
Here is the solution: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
It worked for me.

---

### Post by mister_p_1998 on 2009-06-16
Just try booting to an earlier kernel, it always does that to mine after a kernel update, then comes back on again in a day or two!
Wierd eh?

Steve

---

### Post by eheitner on 2009-06-16
Hey-
I'm running jaunty. I ran the first part of the instructions, didn't fix the problem.

---

### Post by tixetsal on 2009-06-27
Mister p is right!  I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel. I have another box with Asus P5N7A-VM MOBO, and this bug did not effect that machine. My AMD geforce 8200 will not play nice with 28-13 though. My sound card shows up in lspci, but aplay -l tells that I have no sound card.

---

### Post by eheitner on 2009-06-27
Hey- for a complete newb, how do I reboot to an earlier kernel?

---

### Post by tixetsal on 2009-06-27
> **eheitner said:**
> Hey- for a complete newb, how do I reboot to an earlier kernel?

After your computer goes through POST and initializes your hardware, you should see the grub boot menu before the ubuntu splash screen appears.  Choose "2.6.28-11 generic."  Check out my next post though for more info.

---

### Post by tixetsal on 2009-06-27
> **mister_p_1998 said:**
> Just try booting to an earlier kernel, it always does that to mine after a kernel update, then comes back on again in a day or two!
Wierd eh?

Steve

Steve, check this out:

lspci -v on 2.6.28-13 yielded:

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
Subsystem: Elitegroup Computer Systems Device 2646
Flags: 66MHz, fast devsel, IRQ 21
Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel modules: snd-hda-intel

lspci-v on 2.6.28-11 yielded:

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
Subsystem: Elitegroup Computer Systems Device 2646
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

So, I noticed that there was no kernel driver in use in 2.6.28-13. I also noticed that I should have sudo'd before issuing the commands, so i rebooted in order to load 2.6.28-11, and I daydreamed a bit and missed the grub menu. When the login screen was rendered, BEHOLD, i heard the drums!

Now, sudo lspci -v in 2.6.28-13 yields:

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
Subsystem: Elitegroup Computer Systems Device 2646
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

There was no Kernel Driver in use, for some reason, and now things have "magically" been fixed. Does anyone have any theories as to why this occurred?

*UPDATE*

OK, so after a reboot, now sudo lspci -v shows that there is no kernel driver in use again.  What is going on here?

---

### Post by raboofje on 2009-06-28
That is odd: linux-image-2.6.28-13-generic certainly does contain the snd-hda-intel driver:

```
$ dpkg -L linux-image-2.6.28-13-generic | grep snd-hda-intel
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko
```

Perhaps for some reason it is no longer automatically loaded? Does anything happen when you load it by hand:

```
$ sudo modprobe snd-hda-intel
```

---

### Post by tixetsal on 2009-06-28
raboofje,

Thanks for the suggestions, man.  I appreciate it.

sudo modprobe snd-hda-intel didn't return any errors, but didn't give me any audio.  

Now, sudo lspci-v yields: (shows kernel driver)

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2646
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f8d78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

sudo aplay -l yields:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now it's only showing the HDMI again, and I haven't tested it, but I could probably get audio via the HDMI cable - this phenomenon is how I first noticed this whole issue.

I am thoroughly confused.  Somehow I have come back around to the place where I started...

---

