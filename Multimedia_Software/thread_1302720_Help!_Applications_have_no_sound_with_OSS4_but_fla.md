---
title: "Help! Applications have no sound with OSS4 but flash streams do."
date: 2009-10-27
forum: Multimedia Software
---

### Post by danutzmilea on 2009-10-27
Hello! I'm quite new to Linux and I'm running Xubuntu atm just because it's lighter (crappy pc). I just installed it yesterday and the alsa drivers were just not working for me. I got a lot of fuzzy noise whenever i played a tune, so I installed OSS4 as this worked great for me on Ubuntu.

The problem is, all the programs that were supposed to play music and movies have no sound. Nothing! The funny thing is, when i browse YouTube or any other flash stream thingie, the oss driver works.

I also ran this command through the terminal "lspci -v" and sure enough there it was, my sound card:

```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 3800
	Flags: medium devsel, IRQ 10
	I/O ports at d400 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: oss_via823x
```

Can anyone help me? Please?:-S

UPDATE: Now there's also no sound in flash streams.

UPDATE 2: Nevermind. I found the glitch. Aparently i had to set the output driver to OSS for the software i used (vlc and movie player).

---

