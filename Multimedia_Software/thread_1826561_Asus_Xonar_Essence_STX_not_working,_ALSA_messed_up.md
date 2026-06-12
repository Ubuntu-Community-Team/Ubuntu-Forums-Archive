---
title: "Asus Xonar Essence STX not working, ALSA messed up"
date: 2011-08-16
forum: Multimedia Software
---

### Post by Culler on 2011-08-16
I tried installing this new card and I don't have sound anymore, it seems nothing is there even when I reinstall ALSA. I tried enabling my motherboard audio again and its the same thing. 

alsamixer
cannot open mixer: No such file or directory

It says its not there but if I go into the directory I can see it. I have tried manually installing from the source and using the packages and its the same. 

aplay -l
aplay: device_list:223: no soundcards found...

lspci -v
Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Device 835c
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at de00 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-virtuoso

Any suggestions?

---

### Post by Culler on 2011-08-17
Solved this by reinstalling my kernel and kernel headers from a suggestion in this thread:

[http://ubuntuforums.org/showthread.php?t=1684576](http://ubuntuforums.org/showthread.php?t=1684576)

---

