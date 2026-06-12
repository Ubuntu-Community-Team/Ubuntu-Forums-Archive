---
title: "Sounds on"
date: 2010-06-20
forum: Multimedia Software
---

### Post by iedgar10 on 2010-06-20
Hello,


I have a foxconn m61pmv with onboard 5.1 sound. I'm trying to get 5.1 sounds to work. Regular 2.1 works (only my front speakers make sounds) BUT ONLY SOMETIMES. Sometimes Ubuntu will load and there'll be two volume adjusting icons, although only one is actually working, and there would be no sound.
Yes, i have gone through the comprehensive guide and things did not work for me. Any help would be appreciated. 

RESULTS FOR RELEVANT COMMANDS: 


**[SIZE=2]aplay -l[/SIZE]**

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708BCE Analog [VT1708BCE Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708BCE Digital [VT1708BCE Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[SIZE=2]
**lspci -v**[/SIZE]
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at fc00 [size=64]
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fd800000-fd8fffff
    Prefetchable memory behind bridge: fdf00000-fdffffff
    Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
    Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 28
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ec00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d800 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c400 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
    Subsystem: Foxconn International, Inc. Device 0efe
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau

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
    Kernel driver in use: k8temp
    Kernel modules: k8temp

---

### Post by iedgar10 on 2010-06-20
ANYBODY? It appears as though spending more money on Microsoft is an amazing idea- nobody ever replies to forums when i ask for help... lol *Sigh*

bump.

---

### Post by iedgar10 on 2010-06-21
72 views = 0 replies 
*tear* lol

Using 10.04, by the way.

---

### Post by lkjoel on 2010-06-21
Ok, click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

Let me know if it works!

---

### Post by iedgar10 on 2010-06-21
> **lkjoel said:**
> Ok, click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

Let me know if it works!

Thanks! I followed the procedure and I get sound using 2.1 audio. I'm going to test it and see if it'll keep working unlike ALSA that just randomly stopped sometimes. 

One more question: you wouldn't happen to know how to get onboard 5.1 working, would you? 
With windows, the mobo can with a driver CD that also installed an audio controller that just changed what each of the back audio ports were used for. For example, i have blue, green and pink ports on the back. The blue is mic, green is speaker/headphones, and pink was input (i think), but on the software for windows i could change the blue to become front, green to rear, and pink to center/ c sub. Is there any way to do that on here? Or is there a separate piece of software that will allow me to do this?

---

### Post by lkjoel on 2010-06-21
Blue is mic??
Usually blue is output/line in.
Pink is usually mic. Did you check it correctly?

Also for OSS, you need to (at every restart) run
```
sudo soundoff && sudo sync && sudo soundon
```

---

### Post by iedgar10 on 2010-06-21
> **lkjoel said:**
> Blue is mic??
Usually blue is output/line in.
Pink is usually mic. Did you check it correctly?

Also for OSS, you need to (at every restart) run
```
sudo soundoff && sudo sync && sudo soundon
```

Not quite, in the windows software you can make blue be anything, actually. I know that natively it is mic or output (you say mic, i believe you) . BUT you can change it to be either front, back or CSub. Then you can change the other jacks accordingly to get 5.1 using the onboard jacks. Is there anyway to do that on Ubuntu?

---

### Post by lkjoel on 2010-06-21
I don't think I understand you clearly.
I thought you were talking about the plugs in your soundcard.

---

### Post by iedgar10 on 2010-06-22
> **lkjoel said:**
> I don't think I understand you clearly.
I thought you were talking about the plugs in your soundcard.

gahh i'm a terrible explainer lol I will try again....
The motherboard has 5.1 sound onboard. HOWEVER, to get 5.1 you must use software provided by Foxconn (the mobo's manufacturer) in order to change what each of the rear output jacks are for. ORIGNALLY (without the mic they're speakers, mic, input) BUT if you use the software you can change them to be front, rear, Csub. Is there any way to get this on Ubuntu?

---

### Post by lkjoel on 2010-06-22
Hmm, never heard of them.
That reminds me of something else...
Does the soundcard work? Try replacing it.
That was the problem with my computer.

---

### Post by iedgar10 on 2010-06-26
It's on board sound. I know it works because I dualboot with Vista and it works great on Vista.

---

### Post by lkjoel on 2010-06-28
Did you try wine? It emulates windows.
Try:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```

---

### Post by iedgar10 on 2010-06-29
I don't think Wine is appropriate for what i'm trying to do, is it? 
I have understood that windows will emulate software but it won't make permanent hardware changes, will it?

---

### Post by lkjoel on 2010-06-30
Just emulate the software that you have for your sound board.
WINE is quite low-level, and it can be used as drivers.
Though most of the time, it needs to access Z: for your system. (Not the WINE system)

---

