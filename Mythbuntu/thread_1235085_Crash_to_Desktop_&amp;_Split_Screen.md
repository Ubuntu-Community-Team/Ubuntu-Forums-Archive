---
title: "Crash to Desktop &amp; Split Screen"
date: 2009-08-08
forum: Mythbuntu
---

### Post by CrimsonRider on 2009-08-08
Hi, 

I've been trying to build a MythTV box, based on the Dutch Ziggo cable network. It worked on a previous box, but that one had a hard disk crash. I replaced the drive, reinstalled with 9.04 and now am running in to some problems. Maybe they are related.

First off, when I watch TV, the screen is split horizontally, resulting in the same image twice on the screen, but squashed. I have good quality picture and sound, but instead of displaying it completly on the screen, it splits the screen in half and displays it twice. 

Secondly, when I exit the TV mode, it crashes to desktop, always.

Due to things I read on the forum, I suspect this is an issue with the Ati driver. I use the HDMI onboard output of my motherboard wich has an Ati IGFX.

Couldn't work it out so far with the current posts, so I tought I'd ask here. Thanx in advance for any help.

Here are the specs;

```

rider@Myth:~$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.21.0+fixes19961-0ubuntu8
  Candidate: 0.21.0+fixes19961-0ubuntu8
  Version table:
 *** 0.21.0+fixes19961-0ubuntu8 0
        500 http://archive.ubuntu.com jaunty/multiverse Packages
        100 /var/lib/dpkg/status

```

```

uname -a
Linux Myth 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux

```


And the installed hardware, I cut some unneeded parts out of this list

```

rider@Myth:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
        Subsystem: ASUSTeK Computer Inc. Device 82f1
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fbb00000-fbcfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: fbd00000-fbdfffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fbafe000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fbafd000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fbaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbafc000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbafb000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: 66MHz, medium devsel
        Capabilities: <access denied>
        Kernel driver in use: piix4_smbus
        Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: ASUSTeK Computer Inc. Device 82fe
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fbaf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
        Memory behind bridge: fbf00000-fbffffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 82ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbaf9000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>
        Kernel driver in use: k8temp
        Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
        Subsystem: ASUSTeK Computer Inc. Device 82f1
        Flags: bus master, fast devsel, latency 0, IRQ 2299
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at d000 [size=256]
        Memory at fbcf0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fbb00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ASUSTeK Computer Inc. Device 82f1
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fbce8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

04:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: Technotrend Systemtechnik GmbH Device 101a
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fbfffc00 (32-bit, non-prefetchable) [size=512]
        Kernel driver in use: budget_ci dvb
        Kernel modules: budget-ci

```

---

