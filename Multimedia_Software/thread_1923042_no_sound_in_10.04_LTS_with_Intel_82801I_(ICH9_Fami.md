---
title: "no sound in 10.04 LTS with Intel 82801I (ICH9 Family)"
date: 2012-02-09
forum: Multimedia Software
---

### Post by andoras on 2012-02-09
HI!
I'm sorry for disturbing you again, but I've just made a new installation of 10.04.3 LTS and I have no sound at all.
What should I do?
```
 lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1526
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 98a00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...

```
```
uname -r
2.6.32-38-generic

```

---

### Post by wolfen69 on 2012-02-09
> **andoras said:**
> HI!
I'm sorry for disturbing you again

You are not disturbing anyone, as this is what the forums are for. (help)

First, let's start at the beginning. Did you check your sound setting thoroughly?

---

### Post by andoras on 2012-02-09
Thanks!
But in this very moment I've found a solution, in another thread ([http://ubuntuforums.org/showthread.php?t=1467387]("http://ubuntuforums.org/showthread.php?t=1467387"))

So I made:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```
Then reboot.

That's just superb!

---

