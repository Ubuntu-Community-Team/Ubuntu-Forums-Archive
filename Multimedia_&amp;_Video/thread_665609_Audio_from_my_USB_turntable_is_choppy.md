---
title: "Audio from my USB turntable is choppy"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by DennisSullivan on 2008-01-12
I got an ION USB turntable hooked up to my AMD AM2 CPU through the built-in USB ports in my NFORCE6M-A NVIDIA nForce 520 LE motherboard.  My input source in Audacity is ALSA: USB Audio CODEC : USB Audio (hw:1,0).  I get choppy audio from the turntable, I suspect USB bandwidth issues.

How can I check to see if my USB ports are configured to use USB 1.1 or 2.0?  Here is some basic data from my machine:

dennis@dennis-64-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 08bb:2900 Texas Instruments Japan 
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  

dennis@dennis-64-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dennis@dennis-64-desktop:~$ lspci -v
...
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
...

Dennis

---

### Post by DennisSullivan on 2008-01-13
After a day of research I have some answers.

USB interfaces come in three speeds: Low, Full, and High.  My USB Turntable connects at the middle speed (Full) which, at 12 MBits/s should be plenty fast enough for USB Audio (sample rate of 44100 Hz).

System->Preferences->Hardware Information has a section for my USB controller.  When I plug in the USB cable a new subsection appears for my USB Audio.  It is definitely connecting at USB 1.1 Full speed.

As for troubleshooting issues with Audacity, use the wiki at:
[http://audacityteam.org/wiki/index.php?title=Troubleshooting_Recordings](http://audacityteam.org/wiki/index.php?title=Troubleshooting_Recordings)
This is an excellent write-up discussing a myriad of potential issues.

Dennis

p.s.  My audio is still choppy, but now I have some ideas on how to proceed.

---

