---
title: "sound card found but not found in Ubuntu 10.10"
date: 2010-12-19
forum: Multimedia Software
---

### Post by 6py7 on 2010-12-19
I have my sound card being detected on a fresh install of 10.10, however I don't get any sound from it.

Here's some information:
aplay -l
```
aplay: device_list:235: no soundcards found...
```

lspci -v
```
02:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at b800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

```

Following the "Comprehensive Sound Problem" thread, I got to the modprobe for sudo modprobe snd-cmipci which returns nothing.

I added snd-cmipci to /etc/modules, rebooted, and still the same results. 

After rebooting I can get into alsamixer and it recognizes the sound card, I can adjust the volume settings, but the desktop still wont recognize it nor will any sound come out.  

What do I need to do to fix this?

---

### Post by 6py7 on 2010-12-19
Got it solved.  After re-booting again suddenly I had sound.  The desktop side of things isn't working, but I'm using this as a HTPC so I can use alsamixer anyway.

---

