---
title: "[SOLVED] sound issues after empathy"
date: 2008-07-08
forum: Multimedia Software
---

### Post by guhanr on 2008-07-08
On an Ubuntu 8.04 install, I could play music perfectly using RythmBox. And then I wanted to "talk" using GoogleTalk. Reading this post - [http://ubuntuforums.org/showthread.php?t=819046](http://ubuntuforums.org/showthread.php?t=819046), I installed Empathy (it did ask me something about restricted modules and I said yes...)and all was well - I managed to get into GTalk. And then my sound problems started. 

I realized my microphone didnt work [tested via App>Sound&Video>sound recorder]. So, I googled some more and did a bunch of fiddling around (no installs or wgets, though) - only setting changes thro alsamixer and the likes. 

After all that, now both my speakers and my mic dont work! Rythmbox says "Playback Error: Failed to connect stream:Invalid Argument"

I read a lot of the posts, but I am not sure I understand what needs to be done. I tried alsamixer and Unmuted all the channels. Screenshots of my alsamixer output [2 screens] included. Could someone please guide me?

Hoping to "hear" a response <weak grin>

```
 aplay -l
``` results in 

> **** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
 lspci -v
``` results in 

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ed98 [size=8]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 01d5
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
	Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: Dell Unknown device 01d5
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at df40 [size=64]
	Capabilities: <access denied>


---

### Post by guhanr on 2008-07-08
UPDATE: **When I boot and login Ubuntu, I can hear sound -Ubuntu startup music**. So, I dont know if it is just a Rythmbox issue [for speaker]  + Empathy Issue [for mic]. 

Any assistance/guidance would be appreciated.. Thanks

---

### Post by guhanr on 2008-07-09
I figured it out! :) <Pat on back>

When the sound recorder was on, I kept trying to record and assumed that since I didnt see any fancy lights (like in windows sound recorder)  that it wasn't recording. While in fact, it was. I later found out it was a bug. 

When I rebooted, I could hear the logon music - so I realized it was a setting problem. More fiddling later, realized that I had switched the "Sound Capture" from System>Preferences>Sound, under Audio Conferencing to Pulse Audio. I changed that to ALSA and **I killed the PulseAudio process in sysmon**. 

I didnt get the Rythmbox error any more and my sound started working!! So, then for a lark, I tried the recorder and pressed "Save" and tried playing back it worked!!! :guitar:

Now when I rebooted I had the same problem (no sound, no mic) - when I killed the pulseaudio process on sysmon, all is well with the world. 

Maybe someone has insight? :confused:

---

