---
title: "No Sound On Dell Studio SMT-116B Desktop"
date: 2008-12-25
forum: Multimedia Software
---

### Post by umechanism on 2008-12-25
[SOLVED 01-25-2009]  Before posting this thread, I vigorously pursued answers at

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")
and various other places on the web.  To date, I've not had any success so I could really use some expert help here.

Ok.  Here are my specifications:
Hardware:  [_[COLOR="Blue"]Dell Studio SMT-116B[/COLOR]_]("http://personafile.com/Dell-Studio-MT-SMT-116B.html") Desktop purchased 12/20/2008.
Software:  Ubuntu 8.10 - Dual booting with Vista (The Sound Works In Vista)
Soundcard: Realtek ALC888S.

**Coding aplay -l gives:**
michael@michael-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]
Coding lspci -v[/B]

michael@michael-ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe7ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 02ac
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=16]
	I/O ports at a400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: Dell Device 02ac
	Flags: medium devsel, IRQ 11
	Memory at fe7ff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Device 02ac
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
	Subsystem: Dell Device 9018
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Dell Device aa28
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8ec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Device 2810:ac02
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fe9ff800 (32-bit, non-prefetchable) [size=2K]
	Memory at fe9ff400 (32-bit, non-prefetchable) [size=128]
	Memory at fe9ff000 (32-bit, non-prefetchable) [size=128]
	Memory at fe9fec00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at d800 [size=256]
	Memory at feaff000 (64-bit, non-prefetchable) [size=4K]
	Memory at fdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at feac0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
	Subsystem: Conexant Systems, Inc. Device 200f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>

michael@michael-ubuntu:~$ aplay-l
bash: aplay-l: command not found
michael@michael-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
michael@michael-ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe7ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: Dell Device 02ac
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 02ac
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=16]
	I/O ports at a400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: Dell Device 02ac
	Flags: medium devsel, IRQ 11
	Memory at fe7ff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Device 02ac
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
	Subsystem: Dell Device 9018
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Dell Device aa28
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8ec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Device 2810:ac02
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fe9ff800 (32-bit, non-prefetchable) [size=2K]
	Memory at fe9ff400 (32-bit, non-prefetchable) [size=128]
	Memory at fe9ff000 (32-bit, non-prefetchable) [size=128]
	Memory at fe9fec00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at d800 [size=256]
	Memory at feaff000 (64-bit, non-prefetchable) [size=4K]
	Memory at fdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at feac0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
	Subsystem: Conexant Systems, Inc. Device 200f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>

I do not really understand what I am doing well enough to be able to interpet the results.  Is my card supported?  Are my drivers working correctly?  What do I need to do in order to sound on my new desktop?

All help will be greatly appreciated.

Mike

---

### Post by umechanism on 2009-01-03
Anyone?

---

### Post by umechanism on 2009-01-06
I installed the latest Pulseaudio patches/changes that came down through the update manager.  I still have no sound.  

Anyone?

---

### Post by umechanism on 2009-01-09
I've still had no success.  Any help would be greatly appreciated.

Thanks!

---

### Post by umechanism on 2009-01-11
Is there a new kernel I can try?  I'm desperate!

---

### Post by umechanism on 2009-01-18
Bump.

Sorry to bump but I'm down to buying a new sound card if I can not get this fixed.

---

### Post by Mumra on 2009-01-19
Sadly - this is exactly what I did. I have the same problem with a Dell Vostro 420.

---

### Post by umechanism on 2009-01-19
> **Mumra said:**
> Sadly - this is exactly what I did. I have the same problem with a Dell Vostro 420.

Does your PC have the same soundcard?  

What soundcard did you purchase and is it working as expected?

---

### Post by Mumra on 2009-01-19
I picked up a complete POS card from a PC repair shop down the road - it turned out to be an Ensoniq Audio card, and Ubuntu can use it perfectly. It cost me $5.

The built-in audio on the Vostro 420 motherboard looks like exactly the same card as you have, the Intel 82801JI HDA. It looked pretty close to working, but I'm guessing that the audio drivers just aren't available yet, and I don't have time to wait or scratch around installing alphas.

Though, it would be lovely to be wrong.

---

### Post by umechanism on 2009-01-25
**SOLVED!!!**

I followed the directions in this thread regarding Dell Studio machines.  The code provided in this threaded plus the other links I show in my last post (dated Jan. 25, 2009) explains how I resolved it.

I'm listening to music now!

[http://ubuntuforums.org/showthread.php?t=969611](http://ubuntuforums.org/showthread.php?t=969611)

---

