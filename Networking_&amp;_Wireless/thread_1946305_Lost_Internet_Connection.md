---
title: "Lost Internet Connection"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by Timmons on 2012-03-24
Hello,

My computer today just lost the connection.  I don't recall even doing anything but it won't access the internet.  I can access it on the network share but accessing any website doesn't work.  

I tried changing the file in /etc/network/interfaces after reading through some other simliar problems but nothing seems to fix it.  Can anyone help?

---

### Post by Timmons on 2012-03-24
Bump.  I have tried so many things to get this to work and really need some help here.  eth0 doesn't show up in network manager where before it was.  Very frustrated.

---

### Post by HeroKing on 2012-03-24
i've got the same problem. i can detect my router, but can't connect. and ethernet cable doesn't work either

---

### Post by Bucky Ball on 2012-03-24
What release are you using?

---

### Post by HeroKing on 2012-03-24
10.10

---

### Post by Timmons on 2012-03-25
I am using 11.10.   I was able to get it working although I'm not sure how long or which was the resolution.  I looked at the forum on the drivers and downgraded to 8168 from 8169 and then also stopped network manager and didn't start it again.  Now it's able to access the internet.  I'm pretty sure it wasn't the driver but just stopped network manager and that I might have to do that every time I log in.

---

### Post by garvinrick4 on 2012-03-25
You all must tell the users what card and driver you are using or at least a network card.
Here are some different ways to access what cards you have: Just post cards and drivers
in a new thread for each of you. You will get help some good users around here.
```
lspci -nn | grep 0280
```
```
lspci -k
```
```
sudo lshw -C network
```

---

### Post by Timmons on 2012-03-25
Hello,

Here is the information from doing those commands.  Right now I still have an internet connection but am fully expected it to go kaput upon reboot.



00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
    Subsystem: Intel Corporation 82945G/GZ Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
    Subsystem: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge
    Kernel driver in use: leds_ss4200
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
    Subsystem: Intel Corporation N10/ICH7 Family SATA IDE Controller
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Intel Corporation N10/ICH 7 Family SMBus Controller
    Kernel modules: i2c-i801
01:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
    Subsystem: Intel Corporation Device 0000
    Kernel driver in use: e1000e
    Kernel modules: e1000e
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
    Subsystem: Intel Corporation Device 3132
    Kernel driver in use: sata_sil24
    Kernel modules: sata_sil24


PCI (sysfs)  
SCSI                      
  *-network        
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:15:17:31:b0:d8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=3.1-1 ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:ff6e0000-ff6fffff ioport:bc00(size=32)

---

### Post by garvinrick4 on 2012-03-25
Below is your ethernet connection and driver. All seems fine with it. You might have
to just make sure the "Network Manager" icon in upper right like radio waves. Make sure
says enabled when reboot. Do not add any more drivers you use e1000e which comes
in the Linux kernel. [COLOR=Red]yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=3.1-1[/COLOR]


01:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
    Subsystem: Intel Corporation Device 0000
    [COLOR=Red]Kernel driver in use: e1000e[/COLOR]
    Kernel modules: e1000e

---

