---
title: "broadcom sta problems please help!!!!!!!!!!!!!!!!!"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by SCOOT1986 on 2010-12-31
hey guys, im still pretty new to linux so bare with me. I recently upgraded to meerkat (10.10) and im having issues with my wireless connection. It will drop connection randomly. 

pci- netgear wn311b-100nas wpa security
broadcom sta prop. driver
wicd is installed

i'm only posting this because i've tried everything i can think of and i've spent HOURS on google and here trying to figure this out.

i will post iwconfig and ifconfig results when i get a chance later 2nite. if you guys have any idea or know how to fix it, it would be very much appreciated

---

### Post by PatchesTheCaveman on 2010-12-31
Hi SCOOT1986!  Running those commands well help us a lot.

Please also run:
```
lspci -v
```

That will help us verify whether the Broadcom STA driver is installed properly.

---

### Post by SCOOT1986 on 2010-12-31
scooter@scooter-EP43-UD3L:~$ sudo iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:"IT250KforBubba"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:84:A8:F3   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=4/5  Signal level=-64 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

scooter@scooter-EP43-UD3L:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:7f:38:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

eth1      Link encap:Ethernet  HWaddr e0:91:f5:84:a1:bd  
          inet6 addr: fe80::e291:f5ff:fe84:a1bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:507 errors:0 dropped:0 overruns:0 frame:1089
          TX packets:594 errors:176 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:362169 (362.1 KB)  TX bytes:109843 (109.8 KB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3152 (3.1 KB)  TX bytes:3152 (3.1 KB)

scooter@scooter-EP43-UD3L:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fb000000-fcffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000efffffff
    Capabilities: [88] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at fe00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at fd00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 7ff00000-800fffff
    Prefetchable memory behind bridge: 0000000080100000-00000000802fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 0000000080300000-00000000804fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdb00000-fdbfffff
    Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at fc00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fb00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at fa00 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Memory behind bridge: fdc00000-fdcfffff
    Capabilities: [50] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard

00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    I/O ports at f800 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: medium devsel, IRQ 11
    Memory at fdffd000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 (prog-if 85 [Master SecO PriO])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f600 [size=8]
    I/O ports at f500 [size=4]
    I/O ports at f400 [size=8]
    I/O ports at f300 [size=4]
    I/O ports at f200 [size=16]
    I/O ports at f100 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device 0699
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ee000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ef00 [size=128]
    [virtual] Expansion ROM at e0000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: nVidia Corporation Device 0699
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
    Subsystem: Giga-byte Technology Device b000
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at df00 [size=8]
    I/O ports at de00 [size=4]
    I/O ports at dd00 [size=8]
    I/O ports at dc00 [size=4]
    I/O ports at db00 [size=16]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at ce00 [size=256]
    Memory at fdeff000 (64-bit, prefetchable) [size=4K]
    Memory at fdee0000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at fde00000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 12-34-56-78-12-34-56-78
    Kernel driver in use: r8169
    Kernel modules: r8169

05:00.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
    Subsystem: Netgear Device 7d00
    Flags: bus master, fast devsel, latency 32, IRQ 20
    Memory at fdcfc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules: wl, ssb

```
in the process of running this through terminal  it's dropped the connection about 6 times and wicd popped up and error stating "bad password" could this all be a conflict with the wireless security??

---

### Post by PatchesTheCaveman on 2010-12-31
I have a BCM4312 using the STA driver that works great with a WPA2 encrypted router so I don't think so.

The output from iwconfig indicates while your wireless signal isn't great, it should be more than adequate.

Have you tried using NetworkManager instead of wicd?
```
sudo apt-get remove wicd
sudo apt-get install network-manager
```

Usually we have people go the other way around, but there's a first time for everything!

---

### Post by SCOOT1986 on 2010-12-31
i also ran lshw -c network TWICE. once when network dropped

scooter@scooter-EP43-UD3L:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 6c:f0:49:7f:38:ef
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:fde00000-fde0ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: e0:91:f5:84:a1:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=32 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fdcfc000-fdcfffff



And once while wireless was working.

scooter@scooter-EP43-UD3L:~$ sudo lshw -c network
[sudo] password for scooter: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 6c:f0:49:7f:38:ef
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:fde00000-fde0ffff
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: e0:91:f5:84:a1:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.107 latency=32 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fdcfc000-fdcfffff


I'm a little confused as to why it would disable itself??

---

### Post by PatchesTheCaveman on 2010-12-31
It could just do that when it's not being used.  Then again, it could indicate a problem.  Run this command and copy/paste the results:
```
dmesg | grep -i wl
```

That will show any errors the STA driver might be experiencing.

I'll check right now and see if I can replicate that lshw behavior on my system.

---

### Post by PatchesTheCaveman on 2010-12-31
I manually disconnected from my wireless network and lshw still did not report my Broadcom device as DISABLED so something funky is definitely going on here.

---

### Post by SCOOT1986 on 2010-12-31
scooter@scooter-EP43-UD3L:~$ sudo dmesg | grep -i wl
[sudo] password for scooter: 
[   11.200695] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.210880] wl 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20

---

### Post by PatchesTheCaveman on 2010-12-31
There are updated drivers from Broadcom that might help your situation.

Visit [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) to download.  Follow the instructions in the README.txt file to install.  Let me know if you run into trouble.

While the README states that you can get them prepackaged from Ubuntu (and you can), Ubuntu's version is outdated.

---

### Post by SCOOT1986 on 2010-12-31
thanks! ive gone through and downloaded the build tools required, and double checked that everything was installed correctly, downloaded the new .gz file. but im not sure how to "build" the module. 

BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:

For 32 bit: 	hybrid-portsrc_x86-32_v5.100.82.38.tar.gz
For 64 bit: 	hybrid-portsrc_x86-64_v5.100.82.38.tar.gz

Example:
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc_x86-32_v5.100.82.38.tar.gz   [COLOR=Blue][SIZE=4]**<------stuck**[/SIZE]
[/COLOR]
2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make

When the build completes, it will produce a wl.ko file in the top level
directory.

If your driver does not build, check to make sure you have installed the
kernel package described in the requirements above.
i've never had to build kernal modules b4. so if you could give me a crash walkthrough "for dummies" lol it would really speed me up.
and again thanx a bunch for the help!!

---

### Post by PatchesTheCaveman on 2010-12-31
Download the correct driver if you already haven't done so.  Extract it somewhere you can get to easily, like your home directory.

Then open a terminal and *cd* to the directory you extracted it to.

From there you can run *make* and follow the remainder of the instructions.

---

### Post by SCOOT1986 on 2011-01-12
thanks patches! that fixed my problem completely, i havent dropped in over a week now

---

### Post by northd_tech on 2011-08-27
> **SCOOT1986 said:**
> sudo lspci -v
```

05:00.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
    Subsystem: Netgear Device 7d00
    Flags: bus master, fast devsel, latency 32, IRQ 20
    Memory at fdcfc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules:** wl, [COLOR=Red]ssb[/COLOR]**

```
Well there's [at least one of] the problem(s)- the proprietary "STA" **wl** module requires "b43" and "[COLOR=Red]**ssb**[/COLOR]" to be blacklisted in [COLOR=Blue]/etc/modprobe.d/blacklist.conf[/COLOR] in order to work properly from what I remember of Broadcom "STA" driver modules.

EDIT:  Here are the Broadcom-specific lines from my "blacklist.conf" for a working "STA" driver using the **wl** module:

```
blacklist ssb
blacklist b44
blacklist b43legacy
blacklist b43
```

---

