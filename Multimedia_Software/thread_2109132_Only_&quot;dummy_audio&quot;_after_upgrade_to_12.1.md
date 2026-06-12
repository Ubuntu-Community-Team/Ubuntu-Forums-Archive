---
title: "Only &quot;dummy audio&quot; after upgrade to 12.10"
date: 2013-01-26
forum: Multimedia Software
---

### Post by brifra on 2013-01-26
after upgrading to 12.10 my audio has stopped working. It was fine before. No, it's not muted. Yes I've gone through [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) to no avail and filed a bug report.

It looks like [http://ubuntuforums.org/showthread.php?t=2075427](http://ubuntuforums.org/showthread.php?t=2075427) is the same problem and we have the same device listed "HDA Intel" with the chip"Realtek ALC880". 

Any ideas at all?

---

### Post by fsm on 2013-01-29
I have the same problem.  Audio worked fine under 12.04, but no longer functions under 12.10

Running pavucontrol I can only see the Dummy Output device. 
lspci -v shows:
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 0900
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

Any thoughts?

---

### Post by brifra on 2013-01-31
Folks here [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1106334](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1106334)

solved this problem for me! the solution was to:

edit /etc/modprobe.d/alsa- base.conf 
and add the following line
 options snd-hda-intel model=3stack

---

