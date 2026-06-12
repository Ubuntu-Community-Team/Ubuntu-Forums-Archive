---
title: "speakers on laptop still playing when plugging in earphones"
date: 2009-08-02
forum: Multimedia Software
---

### Post by Cozze on 2009-08-02
Hi, I am using a fujitsu siemens amilo xi3650 notebook

when plugging in my earphones the speakers of my notebook keep on producing sound, whereas they shouldn't. Any idea how come and what to do about it?

Thanks, cozze

---

### Post by martinbaselier on 2009-08-02
There's probably an option for the driver.

First find out which driver you are using.

```

lspci | grep Audio -i
**00:1b.0** Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
*use the number from this output to get more details*
lspci -s **00:1b.0** -v
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: **oss_hdaudio**
	Kernel modules: snd-hda-intel

```
In my case the kernel driver in use is "oss_hdaudio"
**modinfo oss_hdaudio**
will show more information about the parameters
If you see a parameter which is likely to fix the problem, you can add it like this:
create a file to add options to the driver:
gedit /etc/modprobe.d/sound.conf
to add option you add a line to the file. 
options drivername option
example:
options oss_hdaudio hdaudio_jacksense=1

---

