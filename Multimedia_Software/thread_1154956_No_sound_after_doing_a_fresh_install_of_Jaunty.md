---
title: "No sound after doing a fresh install of Jaunty"
date: 2009-05-10
forum: Multimedia Software
---

### Post by Clark76 on 2009-05-10
I was previously running 8.10 and decided to upgrade to 9.04 through the package manager and after doing this I lost all sound.  I did not have a lot down on this install so I thought I would simply back up the few files I did not want to loose and do a fresh install and see if that fixes it.  Sadly enough that did not help.  At the log in screen I am getting the quick drum beat but after that nothing.  I did check the headphones I am using on another computer and they are working fine there.
Running aplay -l gives me this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Running lspci -v gives this:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation C51 Host Bridge
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 0
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 1
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 5
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 4
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation C51 Host Bridge
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 3
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: nVidia Corporation C51 Memory Controller 2
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fd800000-fd8fffff
	Prefetchable memory behind bridge: 00000000fd700000-00000000fd7fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Dell Device 01f4
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Dell Device 01f4
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: fda00000-fdafffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Dell Device 01f4
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01f4
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at fdbfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

04:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
	Subsystem: Conexant Systems, Inc. Device 200f
	Flags: bus master, medium devsel, latency 0, IRQ 5
	Memory at fdbe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 9c00 [size=8]
	Capabilities: <access denied>

```
To my untrained eyes this part looks ok (I could be mistaken though ;))
I have been following the instructions in this thread: [Comprehensive Sound Problem Solutions Guide v0.5e](http://ubuntuforums.org/showthread.php?t=205449) and am a bit stumped on the portion to where I need to get the chip set info in this link: [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) but I am not seeing were this info is located.  I know the tutorial is over 2 years old so I am wondering if there is a new link I need to us for this info or if there are different steps I should follow instead.  Please advise.

Thanks for any help offered:)

---

### Post by Clark76 on 2009-05-13
Any ideas?

---

### Post by ozonehole on 2009-05-13
> **Clark76 said:**
> Any ideas?

Have you run alsamixer? I have found that Jaunty by default mutes sound and turns the volume to zero.

In alsamixer, you push "m" to toggle mute/unmute, and of course the up/down arrow keys to adjust volume.

I have not found an elegant way yet to change this default. I have to do it manually, as any changes I make are not remembered after a reboot.

best regards,
oz

---

### Post by Clark76 on 2009-05-13
Thanks for the reply OZ

Unfortunately I have tried that already (plus I just tried it again) with no success.  Think if I can not get this figured out I might go back to 8.10 since I know that the sound worked with that version.  Hoping to avoid doing that though...

---

### Post by sirgimp on 2009-05-13
They were supposedly some changes made to the sound architecture, improving the Pulse Audio implementation. If you go to the menu *System**Preferences*and select*Sound* you'll get the Sound Preference dialog. Select the *Sounds* tab and set the first four drop down choices to *PluseAudio Sound Server* click close and reboot. I have a Dell 530s desktop and the sound works fine in Jaunty. I used to lose frequently in Hardy Heron and Intrepid Ibex, but now when I change from music to audio in Flash Videos, I don't lose the sound. But now there's a problem with fullscreen videos. 

Hope this helps

---

### Post by psyke83 on 2009-05-13
See my PulseAudio guide.

---

### Post by Clark76 on 2009-05-14
Thanks for the suggestions from both of you.

@sirgimp - I tried your suggestion and it made no difference

@psyke83 - I followed your guide up to the first part as was advised since I was running Jaunty and unfortunately that did not help either.

I would consider it being bad timing that the sound would go out due to a hardware failure right when I upgraded but that fact is that at the log in screen I get the quick default drum noise still.  After log in there is nothing though.  I have checked and nothing is muted and volume it pegged at max.

Any other ideas?

---

### Post by Clark76 on 2009-05-16
Just wanted to thank all those that had responded with their suggestions but since I had been working on this for a little while before starting this thread I am throwing in the towel.  I have backed up all my data and reinstalled 8.10.  Sound works fine for me in 8.10.  Hopefully I will have better luck with the sound in 9.10.

Thanks again

---

