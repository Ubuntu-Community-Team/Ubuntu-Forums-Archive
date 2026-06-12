---
title: "No internet access on Acer 5745G"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by siddhantjawa on 2012-08-02
I'm a newbie on Ubuntu... I have recently installed Ubuntu 10.04 in dual boot mode. Neither my wireless nor Ethernet is working at all. It works only in windows 7..

Here is configuration of my system

lspci:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)

01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)

03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01)

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



lshw -class network:
WARNING: you should run this program as super-user.
  
*-network UNCLAIMED     
      
description: Ethernet controller
       
product: AR8151 v1.0 Gigabit Ethernet
      
vendor: Atheros Communications
       
physical id: 0
       
bus info: pci@0000:02:00.0
     
  version: c0
      
 width: 64 bits
      
 clock: 33MHz
      
 capabilities: bus_master cap_list
      
 configuration: latency=0
      
 resources: memory:d4800000-d483ffff ioport:2000(size=128)
  

*-network DISABLED
       
description: Wireless interface
    
   product: AR9287 Wireless Network Adapter
   
    vendor: Atheros Communications Inc.
     
  physical id: 0
     
  bus info: pci@0000:03:00.0
    
   logical name: wlan0
      
 version: 01
     
  serial: c4:46:19:29:0a:03
   
    width: 64 bits
     
  clock: 33MHz
      
 capabilities: bus_master cap_list ethernet physical wireless
      
 configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
      
 resources: irq:17 memory:d3800000-d380ffff


rfkill list:

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by AlanR8 on 2012-08-02
Have a go at this.

Plug your machine into router with a cable. This should give you internet access.

Next go to System Settings Additional Drivers and search for new drivers. Your machine should go out on the web, find the driver and install it.

Enjoy

---

### Post by gordintoronto on 2012-08-02
Use 12.04. When the OS is older than the computer, there are often drivers not included.

---

### Post by Dragechakra on 2012-11-03
> **AlanR8 said:**
> Have a go at this.

Plug your machine into router with a cable. This should give you internet access.

Next go to System Settings Additional Drivers and search for new drivers. Your machine should go out on the web, find the driver and install it.

Enjoy

I have a same problem and can't find any drivers.
In system settings, the only place i can find "additional drivers" is in software sources and, there is no search-options. Only an empty list.

Michael

Edit: I run ubuntu 12.04.

---

