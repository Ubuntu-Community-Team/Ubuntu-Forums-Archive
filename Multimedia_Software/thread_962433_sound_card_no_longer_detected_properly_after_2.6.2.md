---
title: "sound card no longer detected properly after 2.6.24-19"
date: 2008-10-29
forum: Multimedia Software
---

### Post by gnychis on 2008-10-29
Hi all,

After the newest kernels, my sound card has stopped working in Ubuntu.  It is an Intel 82801H, which from doing some research is supported in the snd_hda_intel module.

Following the comprehensive sound guide, when running the newest kernels it seems to be detected as generic which is incorrect:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci does display the correct information for it:
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fa220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

I have tried re-installing everything via the guide, like:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```

My concern is that I believe it uses the ICH8 chipset, which the alsa documents do not seem to list:
```

http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel

```

How did it work before then?  Any ideas?

Thanks!
George

---

### Post by gnychis on 2008-10-29
also, install backports did not help:
```

sudo apt-get install linux-backports-modules-hardy-generic

```

---

### Post by gnychis on 2008-10-29
here's what I get if I boot an old kernel, where the sound works:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

alsamixer:
```

AD1984A

```

---

