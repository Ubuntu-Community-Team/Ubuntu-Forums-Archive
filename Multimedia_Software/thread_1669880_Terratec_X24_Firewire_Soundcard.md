---
title: "Terratec X24 Firewire Soundcard"
date: 2011-01-18
forum: Multimedia Software
---

### Post by weissnich on 2011-01-18
Hi,

I search at FFado.org for this soundcard and it says that it's fully supported, but I can't get it to work.
Has somebody tried it and can give me some help?

---

### Post by cchhrriiss121212 on 2011-01-18
What version of Ubuntu are you using? The setup has changed from 10.04 to 10.10.
Do you have jack + ffado installed?

---

### Post by weissnich on 2011-01-20
> **cchhrriiss121212 said:**
> What version of Ubuntu are you using? The setup has changed from 10.04 to 10.10.
Do you have jack + ffado installed?

I have 10.04 and jack + ffado installed, but the phase x24 is not recognized.

---

### Post by weissnich on 2011-01-20
> **cchhrriiss121212 said:**
> What version of Ubuntu are you using? The setup has changed from 10.04 to 10.10.
Do you have jack + ffado installed?

I have 10.04 and jack + ffado installed, but the phase x24 is not recognized.

---

### Post by weissnich on 2011-01-20
> **cchhrriiss121212 said:**
> What version of Ubuntu are you using? The setup has changed from 10.04 to 10.10.
Do you have jack + ffado installed?

I have 10.04 and jack + ffado installed, but the phase x24 is not recognized.

---

### Post by weissnich on 2011-01-20
I have 10.04 and jack + ffado installed, but the phase x24 is not recognized.

---

### Post by cchhrriiss121212 on 2011-01-20
What does lspci -v show you from a terminal window?

---

### Post by weissnich on 2011-01-20
Only thing in connection with firewire is this:

03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Flags: bus master, medium devsel, latency 32, IRQ 23
	Memory at e1604000 (32-bit, non-prefetchable) [size=2K]
	Memory at e1600000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

---

### Post by cchhrriiss121212 on 2011-01-21
I assume you had the device connected and powered, so now I would try to use the device on another machine, or on Windows if you have a dual boot.

After that try following this guide:
[https://help.ubuntu.com/community/FireWire]("https://help.ubuntu.com/community/FireWire")

---

