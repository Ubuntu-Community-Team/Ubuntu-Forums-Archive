---
title: "Ubuntu Server Sound Issues with Intel 82801BA/BAM AC'97"
date: 2011-10-13
forum: Multimedia Software
---

### Post by adidas56 on 2011-10-13
I am at my wits end with this sound issue, and I am probably missing something really obvious. I went through the [comprehensive sound problem guide]("http://ubuntuforums.org/showthread.php?t=205449"), and I am just stumped.

So first step

```

adidas@test:~$ aplay -l
aplay: device_list:240: no soundcards found...

```

Then

```

lspci -v
...
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)
	Subsystem: Dell Device 010c
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at dc40 [size=64]
	Kernel driver in use: oss_ich
	Kernel modules: snd-intel8x0

```

```

adidas@test:~$ sudo modprobe snd-
[sudo] password for adidas: 
FATAL: Module snd_ not found.

```

I then followed the directions to refresh the kernel with no results. I then tried to compile the ALSA driver, but I ran into the following error while it was compiling with module-assistant.

```

@CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory

```

So what am I doing wrong? Can anyone provide any tips to get me headed in the right direction? I am a bit of a linux newbie and laziness might be getting the best of me, but I have no idea what to do next. Besides the guide says to start a thread, so here it is.

---

### Post by adidas56 on 2011-10-13
I think this is probably a obvious observation

```
adidas@test:~$ lsmod | grep snd_
snd_page_alloc         14036  0 

```

That's it. I assume this is because I don't have the drivers installed?

---

