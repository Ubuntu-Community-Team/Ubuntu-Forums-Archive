---
title: "No sound at all in heron; using headphones in audigy se card"
date: 2008-05-12
forum: Multimedia Software
---

### Post by kurtttz on 2008-05-12
I have got amd64 ubuntu 8.04.  My PC has an Audigy SE card, and headphones plugged into the sound card, and it works fine under vista (at least the sound works fine, the rest of vista is less good....)  

I can't play sound from the front-of-the-box-soundcard headphone hole, as that has a loose connection and doesn't work, even in windows.  

Ubuntu seems to have found the audigy sound card:

adam@adam-desktop:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
adam@adam-desktop:~$ 

But I can't hear a thing; I've tried playing mp3s and youtube, and even the testing buttons on sound configuration, and get nothing.  Master volume on top menu is set to 100%.  

Any help gratefully appreciated.

---

### Post by nubbe on 2008-05-13
Have u tried this:
Type alsamixer in terminal.
Then go with arrow keys almost all the way to the right, There is
Audigy Analog/Digital Output Jack

Then press 'm' to toggle mute.
It should be "off" to work

---

### Post by kurtttz on 2008-05-14
hi Jack, 

Thanks for reply.  I tried what you said.  I do not see Audigy in AlsaMixer.  I have the following bars:
IEC958 [Off]
IEC958 C
IEC958 F
IEC958 R
IEC958 U
Analog C
Analog F
Analog R
Analog S
CAPTURE

Also, I do hear that little african drum sound on start up of ubuntu.  Then nothing else.  Any more ideas?

cheers,
dougal.

---

### Post by nubbe on 2008-05-16
Not really, but if u got start-up sound, then it probably isn't this problem.
Try to play with the volume on the graphical volume control. check the channels in settings and play with them.

---

### Post by kurtttz on 2008-06-08
hi, I made some progress. The headphones plugged into the sound card play that drum beat on startup if you type in the wrong password.  But not the african sound for the correct password, nor any other sound once running.  

The sound socket at the front plays nothing because of hardware fault (it doesn't work under vista either).  But the spare sound socket at the back, not the soundcard one, the normal one, works ok.  So I have sound now in ubuntu, but i expect it is using on board sound card rather than the audigy card.  I haven't got any s/w yet installed on ubuntu where I could tell the difference in sound quality.  

I ran 2 more diagnostic commands, see below.  For 'lspci -v' the sound card is the second last device.  Should I be concerned that it says "Audigy LS" rather than "Audigy SE" or that it considers it an "Unknown device" ?

Thanks for help.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at cc00 [size=64]
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at fec80000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at dddff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at dddfec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dde00000-ddefffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at dddf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 508
	Memory at dddfd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c480 [size=8]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=16]
	Memory at dddfc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=8]
	I/O ports at b080 [size=4]
	I/O ports at b000 [size=16]
	Memory at dddf3000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ddf00000-dfffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at ddeff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at dc00 [size=128]
	Capabilities: <access denied>

01:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at d880 [size=32]
	Capabilities: <access denied>

01:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

01:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at ddeff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Unknown device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at d480 [size=32]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: CardExpert Technology Unknown device 0401
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ec00 [size=128]
	Expansion ROM at ddfe0000 [disabled] [size=128K]
	Capabilities: <access denied>


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Pjotr123 on 2008-06-08
It becomes easier if you use Alsamixergui:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 2 )

---

