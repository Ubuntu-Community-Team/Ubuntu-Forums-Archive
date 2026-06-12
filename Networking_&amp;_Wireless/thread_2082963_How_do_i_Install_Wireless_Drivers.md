---
title: "How do i Install Wireless Drivers?"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by PirateKarma on 2012-11-11
Hey guys, so i'm not very good with computers. I've been using Ubuntu 12.04 and I love it! The only problem is compared to Windows 7, Ubuntu doesn't seem to work well with my Wireless Card. The Signal is always weaker than the amount of Signal I get when in Windows 7. I'm sitting right next to the modem right now, and its still not as strong as it could be. Someone told me, I should install drivers, but Idk how to do this, or what company drivers i even have. Please help! >.<

---

### Post by Abhinav Kumar on 2012-11-11
> **PirateKarma said:**
> Hey guys, so i'm not very good with computers. I've been using Ubuntu 12.04 and I love it! The only problem is compared to Windows 7, Ubuntu doesn't seem to work well with my Wireless Card. The Signal is always weaker than the amount of Signal I get when in Windows 7. I'm sitting right next to the modem right now, and its still not as strong as it could be. Someone told me, I should install drivers, but Idk how to do this, or what company drivers i even have. Please help! >.<
Hi PirateKarma,

Can you please post the output of 
```
sudo lshw -C network
```
and ```
lspci
```

:)
Regards,
Abhinav

---

### Post by PirateKarma on 2012-11-11
Thank you for replying! :) 

Here is the output for sudo lshw -C network


```
  *-network               
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: cc:af:78:80:1e:55
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-32-generic firmware=0.34 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:b5400000-b540ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 2c:27:d7:e4:ff:cf
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:b1404000-b1404fff memory:b1400000-b1403fff

```

And this is the output for lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by Abhinav Kumar on 2012-11-11
Hi,
```

Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe

```
This shows that you need to have aRalink driver installed on your system.
Ralink drivers are relatively new.
A similar SOLVED post is available at
[http://ubuntuforums.org/showthread.php?t=1850267](http://ubuntuforums.org/showthread.php?t=1850267) 

:)
Regards,
Abhinav

---

### Post by PirateKarma on 2012-11-11
Do I also install the Ralink driver 3562. from that post? Or do I need a different driver?

---

### Post by Abhinav Kumar on 2012-11-11
> **PirateKarma said:**
> Do I also install the Ralink driver 3562. from that post? Or do I need a different driver?
No you don't need to install driver 3562
you have to install driver 5390

:)
Regards,
Abhinav

---

### Post by PirateKarma on 2012-11-11
okay thank you!!! :))))

---

