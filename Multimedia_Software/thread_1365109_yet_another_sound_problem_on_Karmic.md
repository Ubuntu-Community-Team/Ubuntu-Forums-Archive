---
title: "yet another sound problem on Karmic"
date: 2009-12-26
forum: Multimedia Software
---

### Post by markiangooley on 2009-12-26
I installed 9.10 on a new disk a few weeks ago and put it aside in case I needed it (the old disk seemed to be getting flaky).  This morning I copied my user directory to the new disk, shut the machine off, disconnected the old disk, booted from the new disk, and started installing software that I hadn't already installed.  As before with 9.10, the sound didn't work.

I tried the method on unixmen.com that had worked before.  It didn't work this time. That's:

[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

I tried the methods in the Comprehensive Sound Problem Solution Guide.  No luck, although I may have messed up the driver compilation.

aplay -l gives me "no soundcards found."  Looking in the System->Preferences->Sound thing shows no hardware.

lspci -v concludes with:

05:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: HT OMEGA Inc. Device 8384
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at e800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: oss_cmpci
	Kernel modules: snd-cmipci

Sometimes sudo modprobe snd-cmipci works.  Last try got me a mess of warnings and then a fatal error.

Any ideas?  I was getting audio yesterday.  I'd rather not go back to that flaky disk, but it seems to contain some magic combination of settings...

Mark.
gooley at gator dot net

---

