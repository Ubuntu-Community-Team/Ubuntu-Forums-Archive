---
title: "Audio hardware not showing. Driver maybe not installed?"
date: 2011-04-02
forum: Multimedia Software
---

### Post by IsmAvatar on 2011-04-02
I'm not getting sound out of my speakers. The Sound Preferences > Hardware tab is not listing anything. I know these speakers are good, and I know they cooperated with the hardware at one point, but after some playing around with oss/pulse/etc back in the days of Ubuntu 8/9, they haven't been working since, and a full purge and reinstall of pulse did not seem to fix it.
lspci -v lists the following for my audio controller

```
$ lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at ffaffc00 (32-bit, non-prefetchable) [size=512]
	Memory at ffaff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: oss_ich
	Kernel modules: snd-intel8x0
```

So the card (or technically, chipset) is there. It looks like it might be trying to use oss still, maybe.

```
$ alsamixer
cannot open mixer: No such file or directory
```

I'm still not completely terminal savvy with linux, so if you want anything from me, try to walk me through how to do it, like at least give me the terminal commands.

Please help me get my sound working again.
-IsmAvatar

---

### Post by IsmAvatar on 2011-04-02
Disregard. After fiddling around a bit and rebooting, I got it to work, kinda. Now my music isn't playing, but system sounds seem to be working.

If I get a better idea of what is wrong, I'll open another thread. You can close this one or whatever you do with solved threads.


SOLVED.

---

