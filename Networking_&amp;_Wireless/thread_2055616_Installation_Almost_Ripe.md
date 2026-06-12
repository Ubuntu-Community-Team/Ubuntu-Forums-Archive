---
title: "Installation Almost Ripe"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by necs on 2012-09-09
Check This Out
 necs: apt-get install ndiswrapper-common 
    # apt-get install ndiswrapper-common    Reading package lists... 
Done     Building dependency tree            Reading state information... 
Done     Suggested packages:       ndiswrapper-source
  The following NEW packages will be installed:       ndiswrapper-common    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.    Need to get 21.7kB of archives.    After this operation, 98.3kB of additional disk space will be used.
 Get:1 [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/)  revolution/main    ndiswrapper-common 1.54-2ubuntu1 [21.7kB]    Fetched  21.7kB in 9s (2,300B/s)                Selecting previously deselected  package ndiswrapper-common.
  (Reading database ... 238113 files and directories currently installed.) 
Unpacking ndiswrapper-common (from .../ndiswrapper-  common_1.54-2ubuntu1_all.deb) ...   
Processing triggers for man-db ...   Setting up ndiswrapper-common (1.54-2ubuntu1) ...

 necs:lspci -nn 
  00:00.0 Host bridge [0600]: 
Intel Corporation 440FX - 82441FX PMC    [Natoma] [8086:1237] (rev 02)    00:01.0 ISA bridge [0601]:
 Intel Corporation 82371SB PIIX3 ISA    [Natoma/Triton II] [8086:7000]     00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4  IDE    [8086:7111] (rev 01)    00:02.0 VGA compatible controller [0300]:  
InnoTek Systemberatung GmbH    VirtualBox Graphics Adapter [80ee:beef]    00:03.0 Ethernet controller [0200]: 
Intel Corporation 82540EM Gigabit    Ethernet Controller [8086:100e] (rev 02)    00:04.0 System peripheral [0880]:
 InnoTek Systemberatung GmbH VirtualBox    Guest Service [80ee:cafe]   00:05.0 Multimedia audio controller [0401]: 
Intel Corporation 82801AA    AC'97 Audio Controller [8086:2415] (rev 01)    00:06.0 USB Controller [0c03]:
 Apple Computer Inc. KeyLargo/Intrepid USB    [106b:003f]    00:07.0  Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI    [8086:7113]  (rev 08    00:0d.0 SATA controller [0106]:
 Intel Corporation 82801HBM/HEM    (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)

  necs: lshw -C network
    *-network                         description: 
Ethernet interface          product: 82540EM Gigabit Ethernet Controller          vendor:
 Intel Corporation          physical id: 3          
bus info: pci@0000:00:03.0
 logical name: eth0          
version: 02
 serial: 08:00:27:33:92:38          
size: 1GB/s          capacity: 1GB/s 
         width: 32 bits            clock: 66MHz          capabilities:  pm pcix bus_master cap_list ethernet physical tp     10bt 10bt-fd 100bt  100bt-fd 1000bt-fd autonegotiation          configuration:  autonegotiation=on broadcast=yes driver=e1000     driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.0.2.15     latency=64 link=yes mingnt=255 multicast=yes port=twisted pair  speed=1GB/s           resources: irq:10 memory:f0000000-f001ffff  ioport:d010(size=8)

---

### Post by necs on 2012-09-09
> **necs said:**
> Check This Out
 necs: apt-get install ndiswrapper-common 
    # apt-get install ndiswrapper-common    Reading package lists... 
Done     Building dependency tree            Reading state information... 
Done     Suggested packages:       ndiswrapper-source
  The following NEW packages will be installed:       ndiswrapper-common    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.    Need to get 21.7kB of archives.    After this operation, 98.3kB of additional disk space will be used.
 Get:1 [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/)  revolution/main    ndiswrapper-common 1.54-2ubuntu1 [21.7kB]    Fetched  21.7kB in 9s (2,300B/s)                Selecting previously deselected  package ndiswrapper-common.
  (Reading database ... 238113 files and directories currently installed.) 
Unpacking ndiswrapper-common (from .../ndiswrapper-  common_1.54-2ubuntu1_all.deb) ...   
Processing triggers for man-db ...   Setting up ndiswrapper-common (1.54-2ubuntu1) ...

 necs:lspci -nn 
  00:00.0 Host bridge [0600]: 
Intel Corporation 440FX - 82441FX PMC    [Natoma] [8086:1237] (rev 02)    00:01.0 ISA bridge [0601]:
 Intel Corporation 82371SB PIIX3 ISA    [Natoma/Triton II] [8086:7000]     00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4  IDE    [8086:7111] (rev 01)    00:02.0 VGA compatible controller [0300]:  
InnoTek Systemberatung GmbH    VirtualBox Graphics Adapter [80ee:beef]    00:03.0 Ethernet controller [0200]: 
Intel Corporation 82540EM Gigabit    Ethernet Controller [8086:100e] (rev 02)    00:04.0 System peripheral [0880]:
 InnoTek Systemberatung GmbH VirtualBox    Guest Service [80ee:cafe]   00:05.0 Multimedia audio controller [0401]: 
Intel Corporation 82801AA    AC'97 Audio Controller [8086:2415] (rev 01)    00:06.0 USB Controller [0c03]:
 Apple Computer Inc. KeyLargo/Intrepid USB    [106b:003f]    00:07.0  Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI    [8086:7113]  (rev 08    00:0d.0 SATA controller [0106]:
 Intel Corporation 82801HBM/HEM    (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)

  necs: lshw -C network
    *-network                         description: 
Ethernet interface          product: 82540EM Gigabit Ethernet Controller          vendor:
 Intel Corporation          physical id: 3          
bus info: pci@0000:00:03.0
 logical name: eth0          
version: 02
 serial: 08:00:27:33:92:38          
size: 1GB/s          capacity: 1GB/s 
         width: 32 bits            clock: 66MHz          capabilities:  pm pcix bus_master cap_list ethernet physical tp     10bt 10bt-fd 100bt  100bt-fd 1000bt-fd autonegotiation          configuration:  autonegotiation=on broadcast=yes driver=e1000     driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.0.2.15     latency=64 link=yes mingnt=255 multicast=yes port=twisted pair  speed=1GB/s           resources: irq:10 memory:f0000000-f001ffff  ioport:d010(size=8)

necs: iwconfig

lo       no wireless extenstion
eth0   no wireless extenstion

What else should I do

---

### Post by chili555 on 2012-09-09
Are you running in a virtual machine such as VirtualBox? Wireless networking likely won't work in a virtual machine.> InnoTek Systemberatung GmbH ***VirtualBox*** Guest Service 

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

We see no wireless device in your lspci.

---

