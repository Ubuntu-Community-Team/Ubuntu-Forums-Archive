---
title: "Nvidia card instead nvidia integrated card"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by ajibarra on 2006-11-12
Hi, i have a nvidia pci-xpress card and i use it but i have a nvidia integrated card and i think that it is the problem. Later i installed the
 Nvidia BETA driver i got blackscreen. I read how use Nvidia card instead Intel integrated card but it is not my case because i cannot put the modules on the blacklist because both cards are nvidia. I want to know if somebody have my problem and if somebody has a solution. 

Thanks,

Alejandro Ibarra

---

### Post by tseliot on 2006-11-12
The beta driver doesn't work for everyone.

You should uninstall it. **Then** you should try Method 1 of my guide.

Moreover I need these details in order to help you:
1) Post the content of your /etc/X11/xorg.conf
1) post the output of this command:
```
lspci -v
```

---

### Post by ajibarra on 2006-11-12
Hi, thank you for response.
#lspci -v
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: efe00000-efefffff
        Prefetchable memory behind bridge: 00000000efb00000-00000000efb00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: efa00000-efafffff
        Prefetchable memory behind bridge: 00000000ef900000-00000000ef900000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: ea000000-ecffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 58
        Memory at ee000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at ed000000 (64-bit, non-prefetchable) [disabled] [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at effff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at efffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f400 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at e000 [size=16]
        Memory at efffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at cc00 [size=16]
        Memory at efffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: efd00000-efdfffff
        Prefetchable memory behind bridge: efc00000-efcfffff
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at c800 [size=256]
        I/O ports at c400 [size=256]
        Memory at efffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at efffa000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c000 [size=8]
        Capabilities: [44] Power Management version 2

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

03:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at ea000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at eb000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ec000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting

04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0caf
        Flags: bus master, medium devsel, latency 32, IRQ 50
        Memory at efdff000 (32-bit, non-prefetchable) [size=2K]
        Memory at efdf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

04:07.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Netgear FA311 / FA312 (FA311 with WoL HW)
        Flags: bus master, medium devsel, latency 32, IRQ 58
        I/O ports at bc00 [size=256]
        Memory at efdfe000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at efc00000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 2

04:09.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: Atheros Communications, Inc. TP-Link TL-WN510G Wireless CardBus Adapter
        Flags: bus master, medium devsel, latency 168, IRQ 66
        Memory at efde0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

```
$cat xorg.conf
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "xkbLayout"     "latam"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Option "RenderAccel" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


```
Other problen that i have is when i reboot my computer and load X i dont have correctly configured video card, i have that open "System Preferences" (KDE) and change Graphic Card because its say "nv generic", i set the graphic card "Nvidia GeForce 6". It is not the driver NV i use "nvidia", it is the graphic card and i dont know how to change that.

Thank you,

Alejandro Ibarra

---

### Post by tseliot on 2006-11-12
> **ajibarra said:**
> Hi, thank you for response.
Make the Section Device of your /etc/X11/xorg.conf look like this:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
	BusID       "PCI:3:0:0"
EndSection
```
In this way you will use your Geforce 6200.

Then log out and press CTRL+ALT+Backspace and log in again.

> **ajibarra said:**
> Other problen that i have is when i reboot my computer and load X i dont have correctly configured video card, i have that open "System Preferences" (KDE) and change Graphic Card because its say "nv generic", i set the graphic card "Nvidia GeForce 6". It is not the driver NV i use "nvidia", it is the graphic card and i dont know how to change that.
You shouldn't care about what System Preferences says. "nv generic" is just a label, nothing else (and therefore doesn't influence the way in which your card works).

---

### Post by ajibarra on 2006-11-12
Ok, now i am using Nvidia 6200 but i read that the blackscreen problem with nvidia drivers beta is because the integrated card is not disable at all..

Here is the post:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated")

Thanks you for all,

Alejandro Ibarra

---

