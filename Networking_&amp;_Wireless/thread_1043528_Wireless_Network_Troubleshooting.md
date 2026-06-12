---
title: "Wireless Network Troubleshooting"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by gloken on 2009-01-18
Hi, I had wireless working on my laptop, and it seems to have stopped working.
I've been arguing with it and am somewhat concerned that I've made the situation even worse.

How does one begin troubleshooting wireless problems?

Linksys, WPC11 v4

******@****-laptop:~$ lshw**
WARNING: you should run this program as super-user.
****-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 503MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.13.6
          size: 1200MHz
          capacity: 1200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-system:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-system:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:96:98:2f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
           *-pcmcia:0
                description: CardBus bridge
                product: OZ711M1/MC1 4-in-1 MemoryCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: OZ711M1/MC1 4-in-1 MemoryCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
           *-system UNCLAIMED
                description: System peripheral
                product: OZ711Mx 4-in-1 MemoryCardBus Accelerator
                vendor: O2 Micro, Inc.
                physical id: 5.2
                bus info: pci@0000:01:05.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:01:06.0
                logical name: eth0
                version: 10
                serial: 00:40:45:21:1d:36
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
     *-network
          description: Wireless interface
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wlan0
          version: 20
          serial: 00:0f:66:4b:96:3e
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+net8180 driverversion=1.53+Realtek,10/07/2004,5.173.10 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:12:6c:94:54:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


******@****-laptop:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:05.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
01:05.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
01:05.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

---

### Post by blothian on 2009-01-18
try a system recovery or find a driver.
hope this helps
ben

---

### Post by gloken on 2009-01-24
> **blothian said:**
> try a system recovery or find a driver.
hope this helps
ben

I did a clean install, installed wifi and ndiswrapper to install the windows drivers and the card still does not work.  

Any help troubleshooting the card would be much appreciated.

Quick update: sudo iwlist scan does show me several wireless networks in the area, so I seem to be connecting to the card. The GUI network manager isn't finding any wireless though and I can't connect to the internet.

---

### Post by Loosewheel on 2009-01-24
> **gloken said:**
> I did a clean install, installed wifi and ndiswrapper to install the windows drivers and the card still does not work.  

Any help troubleshooting the card would be much appreciated.

Quick update: sudo iwlist scan does show me several wireless networks in the area, so I seem to be connecting to the card. The GUI network manager isn't finding any wireless though and I can't connect to the internet.

Hi gloken, here's a link to Ubuntu documentation, Wireless troubleshooting:
[https://help.ubuntu.com/8.10/internet/C/troubleshooting.html](https://help.ubuntu.com/8.10/internet/C/troubleshooting.html)

You have to configure the connection with NetworkManager the first time, or it will not set it up. Maybe right click the 'nm-applett', (by the clock), and select 'Edit connections'.

---

### Post by kevdog on 2009-01-24
I wrote a thread about this type of activity once (See signature!)

---

### Post by Josh_Lapointe on 2009-01-24
Hey,

I had the same issue with mine, all i did was:
Get the latest updates for all the new modules, and then from there went into System and go for Hardware Drivers, and just enable the drivers that are required for your wireless. (I had a Broadcom 4328 that i thought I'd never find drivers for.) Try that, if that doesn't work. Repost. Also, try Ndiswrapper.

---

### Post by gloken on 2009-01-26
Hi again, thanks for all the help. I'll just sum up my results in case someone has a similar problem.


I stumbled upon my answer in here:

[URL="http://ubuntuforums.org/showthread.php?t=318539  sudo gedit /etc/network/interfaces"]
HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.[/URL]

I disabled the gnome-network-manager and went to the command line. I had to edit */etc/network/interfaces *and add:

auto wlan0
iface wlan0 inet dhcp 

It looks pretty obvious there, but it seems to work now. Thanks for all the tips and links, they were enormously helpful.

---

