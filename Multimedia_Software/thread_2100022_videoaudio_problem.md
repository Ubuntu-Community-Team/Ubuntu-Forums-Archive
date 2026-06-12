---
title: "video/audio problem"
date: 2012-12-31
forum: Multimedia Software
---

### Post by KegHead on 2012-12-31
Hi!

I built a new system over the holidays;

msi mobo
amd quad 4
4 gb ram

ubuntu 12.10 (64)

I'm getting a screeching sound with video playback.

Any ideas?

Thanks!

KegHead

---

### Post by Luigi2012SM64DS on 2012-12-31
please give output of:
```
lspci -v | grep -A7 -i "audio"
```
(Paste that into a terminal)

---

### Post by KegHead on 2012-12-31
jim@jim:~$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
	Subsystem: Micro-Star International Co., Ltd. Device f641
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

jim@jim:~$

---

### Post by sudodus on 2012-12-31
Do you get the screeching sound only, or can you hear the desired audio, but have the screeching sound along with it?

Have you set reasonable gain levels internally (for example with the Pulse Audio Control Panel)? Too high levels tend to cause distorsion.

---

### Post by KegHead on 2012-12-31
Hi!

 you hear the desired audio, but have the screeching sound along with it.

Only while playback of avi, mpg ect.

KrgHead

---

### Post by sudodus on 2012-12-31
1. Then I suggest you tweak the settings with the Pulse Audio Control Panel.

2. Or do you get a closed loop with feedback via loudspeakers and microphone? In that case use a headset or disable the microphone temporarily.

---

### Post by KegHead on 2012-12-31
Hi!

Thanks!

I'll at it on 1-1-13!

KegHead

---

### Post by KegHead on 2013-01-01
Hi!

For some reason when I loaded 12.10 the restricted extras were not loaded.

Installed them...I'll give feedback.

KegHead

---

### Post by KegHead on 2013-01-02
Hi!

1. Then I suggest you tweak the settings with the Pulse Audio Control Panel.

It worked!

KegHead

---

