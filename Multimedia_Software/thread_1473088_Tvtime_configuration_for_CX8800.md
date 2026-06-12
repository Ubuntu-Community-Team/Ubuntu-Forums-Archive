---
title: "Tvtime configuration for CX8800"
date: 2010-05-04
forum: Multimedia Software
---

### Post by abhilash82 on 2010-05-04
Can someone help me out in setting up tvtime for Conexant Cx8800 based TV tuner cards in Ubuntu 10.04?

I tried all the combinations by modifying the tvtime.xml configuration file but I still get only a Blue screen and no audio.

I also tried with xawtv and the result was same. I have given below the output of xawtv -hwscan.

```
abhilash@ubuntu:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-21-generic)
looking for available devices
port 88-88
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Camera
    flags:  capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : PixelView PlayTV Ultra Pro (Ste
    flags:  capture tuner
```

Also the output of lspci.```


abhilash@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
	Flags: bus master, fast devsel, latency 0
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fa900000-fe9fffff
	Prefetchable memory behind bridge: 40000000-400fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Device 4246
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at d800 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Intel Corporation Device 4246
	Flags: medium devsel, IRQ 3
	I/O ports at c400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Intel Corporation Device e001
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at feb7f800 (32-bit, non-prefetchable) [size=512]
	Memory at feb7f400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at b800 [size=256]
	Memory at fe9ffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 40000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

[B]01:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: PROLINK Microsystems Corp Device 4976
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

01:01.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: PROLINK Microsystems Corp Device 4976
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa[/B]
```

---

### Post by WinterRain on 2010-05-04
Did you read [this]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)") page?

---

