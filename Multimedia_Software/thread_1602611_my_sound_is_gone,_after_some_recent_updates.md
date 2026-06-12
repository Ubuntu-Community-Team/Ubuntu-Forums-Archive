---
title: "my sound is gone, after some recent updates"
date: 2010-10-21
forum: Multimedia Software
---

### Post by f4bm4n on 2010-10-21
Hello,

i'm **totaly** new to ubuntu. I'm running ubuntu 10.04 (via wubi-installer) on a lenovo g560. I was quite comfortable on ubuntu and thought about switching from win7. I was proud, because i fixed a problem (almost) myself. My speakers and headphones were playing sound simultaniously, so i followed [this solutions]("http://ubuntuforums.org/showthread.php?t=1366524&highlight=mute+speaker+when+headphones&page=4")

Now i lost my faith: Since yesterday, my sound is totally gone. I assume, this problem appeared because of some recent "updates" i blindly accepted. Now, i have no idea where to start...

aplay -l: "no soundcard found..."
lspci -v: i seem to have two soundcards: 
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Lenovo Device 38af
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at db100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

and

```
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Lenovo Device 392d
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

i do not know how to "read" with this information. i am unable to find the correct drivers for my soundcard here: [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

so i followed this guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and did

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 

```
and
```
sudo apt-get install linux-sound-base alsa-base alsa-utils

```

but it did not solve my problem.

And this is where i was tired of tapping in the dark. So i would kindly like to ask you guys for help, because i have no clue how to figure out anything.

---

### Post by Yellow Pasque on 2010-10-21
What updates did you install? If it was a new kernel, try booting into the kernel you were using. BTW, your sound card is snd-hda-intel.

---

### Post by f4bm4n on 2010-10-22
Thank you for your advice. And thank you for telling me, what my sound card is. I guess i should not be using linux. :( As i mentioned i "blindly" accepted a bunch of updates. I installed ubuntu via wubi last week. Neither do i know, what kernel i was using, nor how to boot into it, nor what a kernel is. 

My guess was, it had something to do with the options i have, when booting (Gnu Grub?)
i am currently using 2.6 32.25 generic.
i failed booting 2.6.32.24, because it said "udevdm trigger is not permitted while udev is unconfigured" bla bla bla (did not write it down, sorry) "cat/proc/modules; Is/dev"

sorry, but im not a "crazy horse", thinking "oh.. udevdm trigger is not permitted while udev is unconfiguered, i just have to configure udev by doing this and that, and then i can boot into the kernel i was using before i installed some updates, and then i can finally figure out, why the f*'* my sound disappeared, and then i can solve the problem". 

No, i'm like "O_o" feeling stupid. I tried to boot in recovery-mode, but (almost) failed. "Almost", because the only command i know by heart is "sudo reboot". -.-

Do i have to boot into the kernel i was using permanently from now on? If so: Why? Do i have to fix my sound problems, every time i get  install updates?

---

### Post by f4bm4n on 2010-10-23
SOLVED. i just deinstalled ubuntu:mad:. i saw no point in spending hours/days/weekends figuring out, how to solve my sound problem, if i could use my former operating system: win7.

---

