---
title: "Pinnacle 800i not working Ubuntu Lucid 10.04"
date: 2010-07-27
forum: Multimedia Software
---

### Post by jpgunter on 2010-07-27
The steps I have taken so far:

installed the firmware file located here: [http://www.kernellabs.com/firmware/xc5000/]("http://www.kernellabs.com/firmware/xc5000/")
to /lib/firmware

I also install the linuxtv v4l-dvb drivers located here:
[http://linuxtv.org/hg/v4l-dvb]("http://linuxtv.org/hg/v4l-dvb")

The pertinent info from lspci -v
```
02:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: Pinnacle Systems Inc. Device 0051
	Flags: bus master, medium devsel, latency 20, IRQ 10
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel modules: cx8800

02:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device 0051
	Flags: bus master, medium devsel, latency 4, IRQ 10
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel modules: cx88-alsa

02:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device 0051
	Flags: bus master, medium devsel, latency 6, IRQ 10
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel modules: cx8802

```

---

