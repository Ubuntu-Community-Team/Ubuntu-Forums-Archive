---
title: "No sound :( Nforce 2, already followed comprehensive sound problem solutions guide"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by charims on 2006-08-25
I have no sound whatsoever, i don't know if I am using the wrong diver or what, maybe someone can help me, but i have gone through the entire "comprehensive sound problem solutions guide" here on the forums, and to no avail. I would really like sound, and, if i can't get it using my onboard sound card, i can install some cheap old soundcard(I have a few) that will do the job too.

Okay, so here is my output from 
```
aplay -l 
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK8 [NVidia CK8], device 0: Intel ICH [NVidia CK8]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK8 [NVidia CK8], device 2: Intel ICH - IEC958 [NVidia CK8 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

It has not changed at all since i started.

I have been attempting to use the snd-intel8x0 driver, but i have also tried snd-ac97-bus and snd-ac97-codec.

I also ended up compiling my own driver for snd-intel8x0 as directed by the "Comprehensive sound problem solutions guide".

To no avail, nothing seems to work :(. I have rememberd to restart each time, to reset the sound system, but it jsut won't work.

Will somone please help?
](*,) :confused:

---

### Post by charims on 2006-08-25
oops forgot to post this. Output of 

```
lspci -v
```


```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel, IRQ 9
        I/O ports at e400 [size=32]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: 66MHz, fast devsel, IRQ 177
        Memory at eb002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at eb003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at eb004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at eb001000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e000 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at eb005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e8000000-e8ffffff

0000:00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3) (prog-if 8a [Master SecP PriP])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 927a
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e9000000-eaffffff
        Prefetchable memory behind bridge: d8000000-dfffffff

0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2018
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 193
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant: Unknown device 2000
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e8000000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at c000 [size=8]
        Capabilities: <available only to root>

```

---

### Post by charims on 2006-08-26
Will someone please help me?

---

### Post by warmwaddle on 2007-11-30
Me too... I have absolutely no idea why I don't have sound.

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by jfank on 2007-12-01
I'm having sorta the same problem with my computer.  I was getting sound without a problem after I installed Kubuntu, but when I installed the VLC video player I lost all sound.  I can't get any sound from the music, movies, or even normal system sounds.  I ran those same codes and this is what I got on mine.

> jfank2006@Justinz-Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




> jfank2006@Justinz-Laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0c, sec-latency=32
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 18b0 [size=8]
        I/O ports at 18a4 [size=4]
        I/O ports at 18a8 [size=8]
        I/O ports at 18a0 [size=4]
        I/O ports at 1890 [size=16]
        Memory at dc444400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d6000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Capabilities: <access denied>

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1050
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at da000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Sony Corporation Unknown device 8212
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

Hopefully this is enough information on the information from the terminal to get some help on.  Thank you for the help...

---

