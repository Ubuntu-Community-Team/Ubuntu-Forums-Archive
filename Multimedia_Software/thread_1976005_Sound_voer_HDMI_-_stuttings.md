---
title: "Sound voer HDMI - stuttings"
date: 2012-05-08
forum: Multimedia Software
---

### Post by trikolon on 2012-05-08
Hallo everybody.
I have asystem which i use as a HTPC with xbmc. Installed is ubuntu 12.04 (64 bit) with fglrx driver (ATI 5450). Video is working so far, but I cant get the sound working. The sound starts and after 0.5 sec. the sound starts to repeat itselfs. in xbmc the video totally hangs after that. I have a working xubuntu 11.10 with this HW, any ideas why it is not working on 12.04?

Here are some morge informations:

```
00:05.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Device e157
	Flags: bus master, fast devsel, latency 64, IRQ 65
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f3000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at c200 [size=256]
	Expansion ROM at f3020000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] #1002
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx_updates, radeon

00:05.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: PC Partner Limited Device aa68
	Flags: bus master, fast devsel, latency 64, IRQ 64
	Memory at f3040000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] #1002
	Capabilities: [aa4] #2000
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

aplay -l
```
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Generic [HD-Audio Generic], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
```

Entering some informations in asound.conf did not solve this issue. I think the problem is not, that i dont have any sound, bacause i am hearing something, i think the issue is based on a driver problem. maybe wrong options?

Ben

---

