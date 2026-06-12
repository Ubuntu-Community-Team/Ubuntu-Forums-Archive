---
title: "M-Audio soundcard issues"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Pethegreat on 2008-01-05
I have an M-Audio Audiophile 192 sound card. Currently I am unable to get any sound from the card. I have set the card up with the sound preferences. I have tried both sets of audio outputs. This is odd because Ubuntu 7.10 detected my sound card, yet it won't give me any audio.

---

### Post by balaknair on 2008-01-05
Hi
It would be easier for the more experienced users here(I'm not one of them;)) to understand your problem and come up with possible solutions if you could add a little more info
for sound card issues the following details will probably be helpful
open a terminal(in menu applications>utilities>terminal) and type the following commands and copy paste the output here
```
aplay -l
```
```
lspci -v
```

This will give the others a better idea about the hardware you are using, and what the issues with it probably are.

---

### Post by Yellow Pasque on 2008-01-05
Use OSSv4 for this card, as they're the drivers M-Audio points you to on their site. See the link in my sig. I'm using the M-Audio Revo 5.1 and it works great.

---

### Post by balaknair on 2008-01-05
And speaking from personal experience, it could also be that your sound is muted
you might want to try adjusting volume using alsamixer in terminal

According to the ALSA-project.org site the module you need is snd-ice1724
I just trolled the forums to see if others had issues with it and found this
[http://ubuntuforums.org/showthread.php?t=64239](http://ubuntuforums.org/showthread.php?t=64239)
not exactly your specific problem but it's a thought
You might want to try that before trying anything more drastic

---

### Post by Pethegreat on 2008-01-05
Ok i got the output for the aplay-l command
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audiophile192 [M Audio Audiophile192], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audiophile192 [M Audio Audiophile192], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I already see a possible problem. My audiophile is listed as 2 different devices. 

and for lspci -v 
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at fc00 [size=64]
        I/O ports at 1c00 [size=64]
        I/O ports at f400 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: fdf00000-fdffffff
        Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 2608
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
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

01:04.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. Unknown device 3632
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at cc00 [size=32]
        I/O ports at c800 [size=128]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e) (prog-if 00 [VGA])
        Subsystem: PC Partner Limited Unknown device 0840
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fddf0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=256]
        [virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
        Subsystem: PC Partner Limited Unknown device 0841
        Flags: bus master, fast devsel, latency 0
        Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 8168
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 9c00 [size=256]
        Memory at fdaff000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at fd900000 [disabled] [size=128K]
        Capabilities: <access denied>

```

I ran alsamixer. It shows my card as HDA Nvidia. If I can switch that through the terminal then I think my problem will be fixed.

---

### Post by Yellow Pasque on 2008-01-05
Well, if you're not using the integrated sound, disable it in the BIOS. Problem solved.

There's also a way to pick the default device in ALSA, but I don't remember how :\

---

### Post by Pethegreat on 2008-01-05
I don't have that option in BIOS. 

> There's also a way to pick the default device in ALSA, but I don't remember how :\
I would not have a problem if I could do that.

Edit: WTF? I locked up my computer, rebooted, and now the sound works. All I did was run
```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
```

Well it works. Solved...for now

---

### Post by Pethegreat on 2008-01-05
I rebooted, and now i don't have sound.

WTF?

---

