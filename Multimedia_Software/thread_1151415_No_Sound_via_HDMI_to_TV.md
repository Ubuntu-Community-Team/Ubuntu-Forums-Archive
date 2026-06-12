---
title: "No Sound via HDMI to TV"
date: 2009-05-06
forum: Multimedia Software
---

### Post by zoodsmak on 2009-05-06
I was running Intrepid Ibex without sound and just upgraded to Jaunty with no sound either. Now I'm trying to figure it all out. TOTAL NOOB.

First I tried the sticky post at the top of the page but half way through a link was broken on the page. It appears that the OS is seeing my hardware. Here is the out put I have in the shell:

kevin@kevin-media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



kevin@kevin-media:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fe800000-fe9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: Elitegroup Computer Systems Device 4390
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 2300
	I/O ports at c000 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=16]
	Memory at fe5ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe5fe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe5fd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe5ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe5fc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe5fb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe5fa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Device 4390
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Elitegroup Computer Systems Device 2816
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe5f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe5f9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

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

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
	Subsystem: Elitegroup Computer Systems Device 1b61
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at fe7f0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe600000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe7e8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
	Subsystem: Hauppauge computer works Inc. Device 7911
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Elitegroup Computer Systems Device 8111
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Memory at fdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


Just don't know where to go from here. Thanks for any help!

---

### Post by atundel on 2009-05-08
Have you tried on Administration/Sound to switch it manually and using Totem?

Click on the Autodetect tab and try!
[IMG]http://www.johannes-eva.net/images/2008%2012%20-%20Skype%20in%20Ubuntu%20Intrepid%20Ibex/2008%2012%20-%20Skype%20audio%20settings%20in%20Ubuntu%20Intrepid%20Ibex%202.png[/IMG]

---

### Post by shabazzk on 2009-05-08
I am having the same problem with HDA ATi SB (Alsa mixer), the thing is, it was working before I did a clean install. I just can't pin-point what I did to get it working:confused:. Have tried 5 or more guide in these forums. Nothing seems to work, it like it just decides to start working one day. I would like to figure out how to get this working every time, no matter how many time I reinstall.

---

### Post by zoodsmak on 2009-05-08
I've tried the Switching it manually but still no sound. Is there a way to verify if the hardware is supported?

---

### Post by atundel on 2009-05-09
Did you guys try open the volume control/preferences and ticking the HDMI commuter's box (in my case IEC958)? Btw not all vidoe player's audio work for me, VLC does not, but Totem works perfectly on my TV.

---

