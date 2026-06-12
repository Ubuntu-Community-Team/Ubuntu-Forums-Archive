---
title: "Intel 3945abg wifi card not recognized (even in lspci)"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by liorz1984 on 2009-04-29
but works perfectly in windows.
in addition, *I Can* access the internet (but the connection is very slow and disconnects frequently), because ubuntu installed the rt73usb driver instead of the needed iwl3945

How can i (for start) make ubuntu identify my card?..

lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
04:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
04:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
04:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

Thanks,
Lior.

---

### Post by Zorael on 2009-04-29
Alarming. Does lshw find it properly?
```
$ lshw -c network
```
And you're completely sure it's an iwl3945 card and not an usb device of some sort that works with rt73usb? I don't see how a 3945 card would work even slightly with another driver, though do educate me if I'm wrong.
```
$ lsusb
```

---

### Post by liorz1984 on 2009-04-29
Ok, So basically I have an LG K2-2A8DE laptop, so I know I have this kind of card from the manufacturer website...

lshw -c network returns:

           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:04:03.0
                logical name: eth0
                version: 10
                serial: 00:16:17:54:5e:de
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

lsusb returns:
Bus 005 Device 003: ID 0db0:6877 Micro Star International 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


super weird... i know.

---

