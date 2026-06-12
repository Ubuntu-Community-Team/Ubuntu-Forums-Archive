---
title: "Access denied to sound card."
date: 2008-12-17
forum: Multimedia Software
---

### Post by the.lazy.boi on 2008-12-17
Hello, I am fairly new to the world of ubuntu. My sound is not working at all at the moment. When I started the evening, I had sound when I first logged in, before I type my usr/pass. After trying to fix it using this ```
http://ubuntuforums.org/showthread.php?t=205449'
```
More specifically '```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils'
```
and
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

So, now I have nothing. 

When I run  
```
lspci -v
```

I get the following output
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 1034
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e000 [size=256]
	I/O ports at e400 [size=64]
	Memory at e8001000 (32-bit, non-prefetchable) [size=512]
	Memory at e8002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0



02:03.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at c400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106



```

The soundblaster card is the card I am looking to use. The intel card is my onboard, but I can't use that because the jacks are no good. Why is my access denied, and how might I remedy this? Someone point me in the right direction please!

---

### Post by the.lazy.boi on 2008-12-17
I fart around with it for 8 hours, 13 minutes after I ask for help I get it working properly. Problem solved.

---

