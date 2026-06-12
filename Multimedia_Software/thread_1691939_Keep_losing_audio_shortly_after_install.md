---
title: "Keep losing audio shortly after install"
date: 2011-02-20
forum: Multimedia Software
---

### Post by Jasmotron on 2011-02-20
Ok, so, I've been building systems for some time now, but an relatively new to linux in all its glory. A little info about the PC (which is going to be used as an HTPC):

Epox 9NPA+Ultra with nForce 4 chipset
2gb g.skill value ram
AMD Athlon x2 4800+ (64)
Ubuntu 10.10 32-bit
nVidia 7950gt 512mb
120gb Seagate SATA HD - boot drive
1tb Samsung SATA HD - storage
On-board audio (currently disabled, see below)
DVI to HDMI adapter in to HDMI on 42" Toshiba LCD-TV.


Basically what happens: audio works perfectly while using the "live" session, and also works perfectly after I install the OS. It continues to work for a seemingly random period of time. Within 1-3 reboots, I get no audio.

I disabled the on-board audio in the BIOS thinking it may have been a faulty card (also an old board I haven't used in years), and bought a USB sound card which works great on other systems.

The USB audio also acts similarly to the on-board audio in that I get audio for the first boot or two, then afterwards I do not get audio at all. (Note: I had formatted and reinstalled between disabling the on-board and buying the USB).

Here's some terminal goodness:

```

htpc@htpc-desktop:~$ cat /proc/asound/cards
 1 [default        ]: USB-Audio - USB Sound Device        
                      USB Sound Device         at usb-0000:00:02.0-4, full speed
htpc@htpc-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
htpc@htpc-desktop:~$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: 66MHz, fast devsel, IRQ 5
    I/O ports at fc00 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at e800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d400 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c000 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
    Subsystem: EPoX Computer Co., Ltd. Device 1011
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at bc00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: fdb00000-fdbfffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: fd900000-fd9fffff
    Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: fa000000-fcffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

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

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: EPoX Computer Co., Ltd. Device 900e
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 19
    Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ac00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Device 19f1:2207
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
    I/O ports at 6c00 [size=128]
    [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

```As you can see my audio card is not listed when lspci -v is called, but then again I'm not sure if I'm even looking in the right spot. I went over the "Comprehensive Sound Problem Solutions Guide" found here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) at least ten times with no success. (meaning I've done everything LordRaiden suggested)

I am also unable to get alsamixer to open - it gives me an error similar to:
```
cannot open mixer: No such file or directory
```but from what I can tell nothing is muted. I also do not have an "/etc/asound.conf" file for some reason, although it seems that I should. I've read on other forum posts that creating a simple asound.conf file will enable alsamixer.

I'm thinking it's not hardware related since it's guaranteed to work if I run the live CD or do a fresh install. I'm hoping some of the more linux experienced folks could point me in the right direction?

Edit: lsusb output:
```
htpc@htpc-desktop:~$ lsusb
Bus 002 Device 004: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 1997:0409
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Edit2: 
```
sudo lshw -c sound
```has no output. I assume this is a bad sign?

Edit3: alsa-info script: [http://www.alsa-project.org/db/?f=bd5784cd70a3d0ed294c255a6ea54c06f5cdc020](http://www.alsa-project.org/db/?f=bd5784cd70a3d0ed294c255a6ea54c06f5cdc020)

---

### Post by Jasmotron on 2011-02-20
UPDATE:

I feel like a dumbass. It seems unplugging the USB audio device and plugging it back in has fixed the sound. At least temporarily.

I still don't have access to alsamixer, however. I'm going to mark the issue resolved until I have need of alsamixer.

---

