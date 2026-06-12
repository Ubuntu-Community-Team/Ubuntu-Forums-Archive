---
title: "*wire* connection not working? finish install?"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by bodhidharma on 2011-07-31
Folks,

I'm running a new Lenovo T420, and oddly enough it doesn't detect the ethernet cable when I plug in.  I think I may not have finished the networking part of the installation (I probably skipped anything it said I could do later), but now I'm in a bad situation!

Does anyone know what I can do?  Here is some relevant info:
```
 lshw -C Network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f2600000-f261ffff memory:f262b000-f262bfff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:c6:ea:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=172.30.170.251 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f2500000-f2501fff

 lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c4f (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 04)


cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

Any suggestions would be great!

---

### Post by chili555 on 2011-07-31
I think your ethernet card works with the module e1000e. Let's load it and see what happens. Please do:```
sudo modprobe e1000e
```Any errors or warnings? Is an ethernet interface created?```
ifconfig
```Thanks.

---

### Post by bodhidharma on 2011-07-31
Thanks for your insight... but no joy, yet.  I did the
modprobe e1000e
which simply came back immediately (i.e., no errors).  e1000e shows in lsmod, so it worked.  But the ifconfig shows nothing new, likewise lshw, etc.

---

### Post by chili555 on 2011-07-31
What does dmesg have to say?```
dmesg | grep e100
```

---

### Post by bodhidharma on 2011-07-31
Hmm, it says

```
dmesg | grep e100
[    0.000000] ACPI: UEFI dafe1000 0003E (v01 LENOVO TP-83    00001270 PTL  00000002)
[    0.000000]   #5 [00008e1000 - 00008e40ed]              BRK ==> [00008e1000 - 00008e40ed]
[ 5860.418411] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[ 5860.418421] e1000e: Copyright (c) 1999-2008 Intel Corporation.

```

I don't know what that means, is it reasonable?

---

### Post by chili555 on 2011-07-31
It is reasonable in that the module loads and causes no error, warnings, etc. It does not, however, go on to create an ethernet interface eth0. Let's dig deeper. Please do:```
dmesg | grep 19.0
```19.0 is part of the bus number:> *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@[COLOR="Red"]0000:00:19.0[/COLOR]
       version: 04
       width: 32 bits
       clock: 33MHzFor reference, my e1000e device does this in dmesg:> [    1.507254] [COLOR="Red"]e1000e[/COLOR]: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.507258] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.507292] e1000e 0000:02:00.0: Disabling ASPM  L1
[    1.507310] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.507336] e1000e 0000:02:00.0: setting latency timer to 64
[    1.507554] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.508050] e1000e 0000:02:00.0: Disabling ASPM L0s 
[    1.629139] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:41:e6:cb:ef
[    1.629144] e1000e 0000:02:00.0: [COLOR="Red"]eth0: Intel(R) PRO/1000 Network Connection[/COLOR]
[    1.629222] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: 005301-003In short, the physical device and the driver meet and get married.

---

### Post by bodhidharma on 2011-07-31
Hmm, here's what I get
```

dmesg | grep e100
[    0.000000] ACPI: UEFI dafe1000 0003E (v01 LENOVO TP-83    00001270 PTL  00000002)
[    0.000000]   #5 [00008e1000 - 00008e40ed]              BRK ==> [00008e1000 - 00008e40ed]
[ 5860.418411] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[ 5860.418421] e1000e: Copyright (c) 1999-2008 Intel Corporation.
ROOT@zinho[~] dmesg | grep 19.0
[    0.547279] pci 0000:00:19.0: reg 10 32bit mmio: [0xf2600000-0xf261ffff]
[    0.547285] pci 0000:00:19.0: reg 14 32bit mmio: [0xf262b000-0xf262bfff]
[    0.547291] pci 0000:00:19.0: reg 18 io port: [0x5080-0x509f]
[    0.547329] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.547333] pci 0000:00:19.0: PME# disabled
[    0.560380] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.019303] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    1.019309] ahci 0000:00:1f.2: setting latency timer to 64
[   19.191078] IBM TrackPoint firmware: 0x0e, buttons: 3/3
```

---

### Post by chili555 on 2011-07-31
I love Lenovos! You'd better send it to me and I'm sure I'll have it fixed in 3-4 years. No? Just kidding. 

Are you quite sure the ethernet is enabled in the computer's BIOS? How are the IRQs set up? Auto Detect? Something simple is not right.

---

### Post by bodhidharma on 2011-07-31
Yeah, I thought something simple was really messed up.  I would take you up on your offer of a quick fix (3-4 years) if I didn't need the damn thing to be working sooner....

Any suggestions about a bunch of silly, basic things to check to try to track this down, and *how* to check them?  I guess to check the BIOS, I go into the BIOS menus during boot.  IRQs?  Other basic things?

I've never had these kinds of problems on fresh installs in the past.  I keep thinking that when I did the install, I clicked something at some point about "configure network later", because I was in a place with only a crappy wireless, and maybe it didn't do some really basic config.  Is there some utility I can run which will re-do the install at that point?

Thanks for all your help, by the way....

---

### Post by chili555 on 2011-07-31
On my older Lenovo, and yours might not be the same, it says, approximately, to press the blue ThinkVantage button to enter the setup utility. That's the BIOS. I'd just check to see that everything in sight is enabled.

Here is a screenshot showing a Thinkpad IRQ setup page. Yours, of course, might be different.

I'm fairly confident it's not an installation issue. e1000e is on your system and loads without complaint. It just doesn't see a compatible ethernet card to marry.

I will see what else I can see in my own BIOS and post back.

---

### Post by chili555 on 2011-07-31
In the Lenovo BIOS simulator I found on line, under Config > Network I found this.

---

