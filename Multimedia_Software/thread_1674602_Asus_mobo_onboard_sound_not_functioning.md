---
title: "Asus mobo onboard sound not functioning?"
date: 2011-01-24
forum: Multimedia Software
---

### Post by myromance123 on 2011-01-24
Hi there. Hopefully I believe I'm putting this in the right spot. A rather annoying problem I have at the moment is that my on-board sound device is not working. Neither in Ubuntu 10.10 or Windows XP Home for that matter.

[LIST]
[*]Motherboard: **ASUS M4A88T-V EVO/USB3**
[*]OS: Ubuntu 10.10 64Bit/Windows Xp Home 32Bit
[/LIST]

I've only bought this mobo yesterday. I set it up and used the Asus given CD on XP and all installed fine. There was however no sound ( no volume bar, no audio device installed) and in Device Manager there are 2 yellow not installed PCI Devices.

I thought it might just be XP, so I installed Ubuntu afterwards. There is still no sound in Ubuntu either.

I believe the on-board sound is an ALC892 Realtek High Definition Sound Device. Neither front ports or back ports work with audio.

What troubles me is that I think the problem has something to do with the  Ati Southbridge (If what I gathered from the Internet is correct so far).

How can I go about getting the sound to work in Ubuntu? I want to determine that there isn't a hardware fault, but if all else fails I will return it to get a new model (Its just such a hassle as the shop is far away).

I used my headphones to test the sound and my speakers. Both headphones and speakers have been tested via my laptop to ensure they function and yes they do work. I also ensured that sound in Ubuntu was not muted, confirmed it is not muted. I have also ensured that I'm using the correctly colored green sound port, and I have also tested all the others as well. No luck.

From a terminal:
```
aplay -l
```
gives me:
```
aplay: device_list:235: no soundcards found...
```

```
lspci -v
```
gives me:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: ASUSTeK Computer Inc. Device 843e
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe900000-fe9fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at b000 [size=8]
    I/O ports at a000 [size=4]
    I/O ports at 9000 [size=8]
    I/O ports at 8000 [size=4]
    I/O ports at 7000 [size=16]
    Memory at fe8ffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fe8fd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe8ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe8fb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe8ff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 841b
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8389
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe8fa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850] (prog-if 00 [VGA controller])
    Subsystem: ATI Technologies Inc Device 0502
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe9e0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at c000 [size=256]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: ATI Technologies Inc HD48x0 audio
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8432
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at d800 [size=256]
    Memory at fdfff000 (64-bit, prefetchable) [size=4K]
    Memory at fdff8000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30)
    Subsystem: ASUSTeK Computer Inc. Device 8413
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at feafe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

```

Btw, which one is the Audio Device?
**#01:00.1 Audio device: ATI Technologies Inc HD48x0 audio**
OR
**#00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)**

Any help would be greatly appreciated!


Further system specs are as follows:
[LIST]
[*]Processor: AMD Phenom II x4 965 BE
[*]RAM: 4GB DDR3 Corsair VS 1333
[*]G.C: ATI RadeonHD 4850 512MB
[/LIST]

This mobo is listed under:** AMD 880G/SB710**
Further specifications regarding this mobo here: [[COLOR="Blue"]link[/COLOR]]("http://www.asus.com/product.aspx?P_ID=LeLwETEg17MhPQcq&templete=2")

---

### Post by Yellow Pasque on 2011-01-24
This is your audio device:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 841b
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```
The other one is the HDMI audio chip on the video card.

Since lspci sees your card and indicates the appropriate kernel module is loaded, the next step is to figure out why ALSA doesn't recognize the card. Look through dmesg for any errors/warnings related to audio, ALSA, snd-hda-intel, etc.

---

### Post by myromance123 on 2011-01-25
Thanks Temüjin for replying,

 How would I use dmesg? Just type it in the terminal? I've never used dmesg before.

Also I've confirmed the hardware is not faulty, since I got it running in XP but that was a real hassle. Problem there was due to SP3.

---

### Post by myromance123 on 2011-01-25
Alright, after running dmesg I get the following ( I took what looked right ):

```
[    9.383694] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.652185] hda_codec: ALC892: BIOS auto-probing.
[    9.658568] Too many connections
[    9.659916] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.659964]   alloc irq_desc for 44 on node 0
[    9.659965]   alloc kstat_irqs on node 0
[    9.659973] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
[    9.659991] HDA Intel 0000:01:00.1: setting latency timer to 64
[   11.082316] type=1400 audit(1295991305.355:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=856 comm="apparmor_parser"
[   11.082491] type=1400 audit(1295991305.355:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=856 comm="apparmor_parser"
[   11.082591] type=1400 audit(1295991305.355:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=856 comm="apparmor_parser"
[   11.153781] type=1400 audit(1295991305.425:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=860 comm="apparmor_parser"
[   11.726137] ppdev: user-space parallel port driver
[   14.384402] r8169 0000:02:00.0: eth0: link up
[   14.384407] r8169 0000:02:00.0: eth0: link up
[   18.258591]   alloc irq_desc for 45 on node 0
[   18.258594]   alloc kstat_irqs on node 0
[   18.258602] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
[   18.259032] [fglrx] Firegl kernel thread PID: 1218
[   18.259203] [fglrx] IRQ 45 Enabled
[   18.558264] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   19.597930] [fglrx] Gart USWC size:1240 M.
[   19.597933] [fglrx] Gart cacheable size:491 M.
[   19.597936] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   19.597938] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   19.597939] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   24.412549] eth0: no IPv6 routers present
[   29.050209] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   29.575200] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

I did notice "Too many connections" displayed on screen since the beginning of my Ubuntu install.

Not sure how to use this information. I'll keep studying it.

---

### Post by myromance123 on 2011-01-25
I must say, extremely weird! But it appears that after having installed the sound drivers in XP, Ubuntu now knows what they are ...

From terminal:
```
aplay -l
```
gives me:
```
ismail@ismail-System-Product-Name:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I still had no sound however, so I then opened up Sound Preferences.
Changing between:
[LIST]
[*]Internal Audio Analog Stereo
[*]HD48x0 audio Digital Stereo (HDMI)
[/LIST]

did nothing to change that.
BUT, I went back to Internal Audio Analog Stereo (HDMI) and then clicked on the drop down menu from Connector. I changed between Analog Output to Analog Headphones. No sound (music was playing in the background). I then changed back to Analog Output and... voile! Sound!

 I swear I don't understand what made it work... I didn't install any new libraries or do anything Alsa related. I am thankful though that it works now :)

SOLVED.

---

