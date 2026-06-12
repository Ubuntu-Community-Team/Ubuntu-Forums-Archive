---
title: "trouble setting up new wireless desktop connection"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by mejbr2003 on 2011-01-30
Hi, thanks ahead of time for any and all help
semi-newbie here.
 
I'm dual booting the latest ubuntu and xp on my desktop computer. I've moved and now have to connect via wireless. 
I have a linksys wireless-g pci adapter. I was able to get it set up fine on the xp ide, but cant get ubuntu set up.
I've tried to follow the steps in the wireless troubleshooting offered in "help". 
it seems like the I needed to obtain the windows wireless driver and install it in ubuntu. so I did that
but
then the instructions told me to download a package that would receive te driver.
If i can't set up my connection, how am I supposed to download anything.
Here is my lshw -c network outcome. I'm not sure it's relevant.

i'm now stuck as to what to do next...
Help please.
thanks again1

---

### Post by ronnielsen1 on 2011-01-30
Post the output of lspci -v

---

### Post by mejbr2003 on 2011-01-31
Here's lspci -v
I haven't made any progress since last night...still stuck
thanks for any and all help

josh@mylivingHAL:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
	Flags: bus master, fast devsel, latency 0
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fa900000-fc9fffff
	Prefetchable memory behind bridge: e2500000-f26fffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ec00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fca00000-feafffff
	Prefetchable memory behind bridge: f2700000-f27fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: Gateway 2000 Device 5288
	Flags: medium devsel, IRQ 3
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e400 [size=256]
	I/O ports at e080 [size=64]
	Memory at febff800 (32-bit, non-prefetchable) [size=512]
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 8731
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at f2680000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at fc9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-96, nvidiafb, rivafb, nouveau

02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0058
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

02:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: ATI Technologies Inc Device 00f8
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Linksys Device 0014
	Flags: bus master, fast devsel, latency 32, IRQ 18
	Memory at feafc000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
	Subsystem: Gateway 2000 Device 5288
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d880 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

josh@mylivingHAL:~$

---

### Post by ronnielsen1 on 2011-01-31
Try this:
> **Ubuntu/Debian**

 In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you: 

 [Toggle line numbers]("http://linuxwireless.org/en/users/Drivers/b43#")    1 sudo apt-get install b43-fwcutter



You will be asked to automatically fetch and install the firmware into the right location. 
Update:  Ubuntu has a page detailing on how one goes about installing broadcom  wireless drivers on their community documentation. 
If  you have internet access on the device that has a b43 supported  broadcom wireless chipset and would like to use b43, follow this link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access) . 
If  you do not have internet access on the device that has a b43 supported  broadcom wireless chipset and would like to use b43, follow this link  instead: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access) . 
Note that you can only follow one of the two guides, not both. 

[http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian)

---

### Post by ronnielsen1 on 2011-02-02
Any luck getting this working?

---

