---
title: "Sound only plays static"
date: 2011-05-16
forum: Multimedia Software
---

### Post by renegaderebel on 2011-05-16
Hello all,
I recently installed 10.04 to a spare machine I had. Upon installing I discovered that I'm unable to get any audio. Well correction, I get "audio" just not usable audio. Whenever audio is supposed to be playing I get solid static. I've gone through and added my alsa module to no effect. I've tried every profile in the Sound Preferences -> Hardware setting tab with no luck.

here is my lspci -v output
```
Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 1001
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at 1040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

```

I would greatly appreciate any help offered. Thanks.

---

### Post by jazzwhiz on 2011-08-04
Bumpsies

---

### Post by t1mulid on 2011-08-22
I have the same problem.

SEE my BUG report 804051. I reported this some time ago. I still have the same problem but I guess sound using the ca0106 sound blaster is not important enough. I am still using windows as my primary system because of this problem. I doubt that this problem will ever get fixed.

---

