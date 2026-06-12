---
title: "No wired connection - Ubuntu 10.04.1"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by jokes_finder on 2010-10-03
Hello,

Well, I have Ubuntu 10.04 LTS on my desktop.. Everything is going well

I have just bought a new Laptop - Toshiba Satellite L650-10M
I downloaded the [windows installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") and have ubuntu set-up on the laptop

The problem is: I can NOT access the Internet... It says that no networks are found!!
I think I need to install the driver

I'm ready to post the needed outputs.

Sorry for my bad English

Thanks in advance...

Note: I have searched topics like this one but can't find an answer

---

### Post by dineshs on 2010-10-03
> I'm ready to post the needed outputs.
```
sudo lshw -C network
``````
iwconfig
```

---

### Post by jwerwie on 2010-10-03
System -> Administration -> Hardware Drivers

---

### Post by jokes_finder on 2010-10-04
Sorry for being late..

@dineshs:
Here are the outputs:

for the sudo lshw -C network command:```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d5000000-d503ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4000000-d4003fff
```and for the iwconfig command:
```
lo        no wireless extensions.

pan0      no wireless extensions.

```for the ifconfig -a command:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32288 (32.2 KB)  TX bytes:32288 (32.2 KB)

pan0      Link encap:Ethernet  HWaddr e6:ea:71:f2:6a:ec  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```for the lspci command:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```\for the sudo ifup eth0 command:
```
Ignoring unknown interface eth0=eth0.
```
@jwerwie: 

A window appeared which says "NO proprietary drivers are in use on this system"

---

### Post by dineshs on 2010-10-05
> product: AR8152 v1.1 Fast Ethernet
Pl try this link
[http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

---

### Post by jokes_finder on 2010-10-05
Thanks a lot
Everything is going well

---

