---
title: "[SOLVED] Sound in Windows, None in Hardy Heron Ubuntu 8.04"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Thirdman03 on 2008-07-09
I dualboot like a lot of people, but now I have no sound in Linux (from the startup screen to starting an audio program like Rhythmbox or Totem or Pandora in Firefox). Windows XP has sound and is not muted.

I have gone through the steps of the Comprehensive Sound Problem Solutions and it has not worked. Really, everything looks like it should be working, I just can't hear a thing. I've tried killing Pulseaudio as a backup, and while it worked well when I had some sound (read: my problem was that Firefox audio and Rthyhmbox would block one or the other out), now there is simply no sound. Right now, everything is switched from Default (read: Pulseaudio) to ALSA, if that's important to the solutions that will hopefully come in response to this thread.

Like others in the forums, I have tried reverting to previous kernels I had when the sound worked, but that has not fixed the problems, so the problem is different than that. I guess I'm calling for a thinking-outside-the-box approach.

For any help it is--if it's not help just ignore it--I will chronicle the specifics of my system (possibly to show how I followed the instructions and invoke pity for my situation):

(code in terminal)
aplay -l
(result)
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

(code in terminal)
lspci -v
(result)
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: f9f00000-f9ffffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f9c00000-f9efffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f81fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: f9b00000-f9bfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=16]
	I/O ports at eff0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 0228
	Flags: medium devsel, IRQ 10
	Memory at febfbf00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f4000000 (64-bit, prefetchable) [size=64M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at df00 [size=128]
	[virtual] Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Unknown device 0228
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
	Subsystem: Dell Unknown device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

----
The next major thing I tried was wa-a-ay down at the
"Adding the current user to the audio group

A very common cause for a user to not have sound is not having his/her username in the /etc/group."

(code in terminal)
sudo nano /etc/group
I made the following changes before exiting and saving:
audio:x:29:pulse,jonathan --> audio:x:29:jonathan

I documented the change, so I can undo it, but I have exhausted the sound guide and make a plea to you all for your help. I haven't read all 100 pages of comments to the guide, only the first 3-4 and the last 3-4 (as of July 7).

Thanks in advance; I'll be checking often for help.

---

### Post by Unterseeboot_234 on 2008-07-09
Without comprehending all the hardware specs and settings you posted... I wanted to tell you what worked for me with this similar issue. Fire up a Terminal

alsamixer

That gives you a 8-bit color graphics program that you use the keyboard to change settings. For instance, my nVidia graphics card has a PCM sound chip. I want that chip for my audio instead of my onboard sound chip the IEC958. I make sure PCM has a high volume setting and the headphones also. I use the keyboard arrow keys to navigate that program's features.

All I can tell you is I can lose my audio by tweaking other software such as Cinelerra's audio options when doing video production. I come back to alsamixer and it works. Hope this is of some use to you.

---

### Post by Thirdman03 on 2008-07-21
Thanks for the Alsamixer thing, but I'm afraid it doesn't work for me. Something's not right. I appreciate the effort, and I completely understand why the long list of specs means nothing to you. It's a shot in the dark as to the information someone might need to help me.

---

### Post by mc4man on 2008-07-21
Have you looked for a solution with the emphasis on make and possibly model of pc (dell laptop?) vs. the audio device? You would think yours (sound device) is fairly common,  ie. it works.

I might try some livecds from 8.04 and 7.10 and see if any worked, if so it would be something to look at. If 7.10 worked maybe install it, update it, and try an immediate upgrade to to 8.04 ?

[http://ubuntuforums.org/search.php?searchid=44925911](http://ubuntuforums.org/search.php?searchid=44925911)

---

### Post by Thirdman03 on 2008-07-31
Thanks for the post. I haven't checked the exact model or anything for compatibility, but since I'm having so much trouble it's most definitely worth it. Again, though, my sound was working perfectly until one day, so I doubt that is the exact problem.

Also, I'll try seeing if a friend can find anything he might think is wrong. Didn't want to rely on him, but sometimes you have to, right? Since people might look at this later, hopefully I'll post up any solutions my friend finds.

Thanks again to all.

---

### Post by Thirdman03 on 2008-08-01
Hope no one's angry at how simple this solution was, it was a problem with the alsamixer, that was only fixed by going to the terminal alsamixer. That means I should have had more faith in Unterseeboot_234. The PCM was at zero, so no wonder nothing would work. Unterseeboot_234, it may not matter but I did go to the Alsamixer. I can only guess why I didn't see the problem, but sometimes a new set of eyes is all you need.

Again, thanks for the people who replied. I know I've done stuff with the Alsamixer before, so I don't know how I could overlook it.

I'll try to find a way to mark the post itself SOLVED and put my thanks out there.

---

