---
title: "can someone help me?"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by tklist on 2011-04-16
I use ubuntu 10.04.I connect Internet with a static IP and MAC address.For some reasons,I need to modify MAC address and with a new IP.So,I use gedit command to modify /etc/network/interfaces like this.

auto eth0
iface eth0 inet static
hwaddress ether xx:xx:xx:xx:xx:xx
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x

But I cannot ping through gateway and Internet.
I restart network but it happened that fail to bring up eth0.
Why this happened?Can someone explain  it?
Much thanks.

---

### Post by josephmills on 2011-04-16
> **tklist said:**
> I use ubuntu 10.04.I connect Internet with a static IP and MAC address.For some reasons,I need to modify MAC address and with a new IP.So,I use gedit command to modify /etc/network/interfaces like this.

auto eth0
iface eth0 inet static
hwaddress ether xx:xx:xx:xx:xx:xx
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x

But I cannot ping through gateway and Internet.
I restart network but it happened that fail to bring up eth0.
Why this happened?Can someone explain  it?
Much thanks.

the next tine you have to change  you mac address you can do ```
macchanger -r (card name )
``` if you are rockin a static ip then it should never have to change ip's (you pay for that) So after you  logged into your router did you contact your isp to let them know what happened? As I know with my isp with a static ip they wont even let you in-to your router and they do all the "work" for you. So the first thing that I would do is call my isp and complain about this if you are signed up for a static account then there is 24hour/365day support usually. but in  the mean time could you show us a ```
ifconfig 
``` (take out the important info ) and a ```
lshw
```thanks

---

### Post by tklist on 2011-04-18
> **josephmills said:**
> the next tine you have to change  you mac address you can do ```
macchanger -r (card name )
``` if you are rockin a static ip then it should never have to change ip's (you pay for that) So after you  logged into your router did you contact your isp to let them know what happened? As I know with my isp with a static ip they wont even let you in-to your router and they do all the "work" for you. So the first thing that I would do is call my isp and complain about this if you are signed up for a static account then there is 24hour/365day support usually. but in  the mean time could you show us a ```
ifconfig 
``` (take out the important info ) and a ```
lshw
```thanks

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:24:21:05:0f:90  
          inet addr:49.140.72.7  Bcast:49.140.72.255  Mask:255.255.255.0
          inet6 addr: fec0::9:224:21ff:fe05:f90/64 Scope:Site
          inet6 addr: 2002:318c:4898:9:224:21ff:fe05:f90/64 Scope:Global
          inet6 addr: 2001:da8:b000:6605:224:21ff:fe05:f90/64 Scope:Global
          inet6 addr: fe80::224:21ff:fe05:f90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39630 (39.6 KB)  TX bytes:5040 (5.0 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
It seems right,MAC address and IP are right.
I donot hava macchanger command.

---

### Post by tklist on 2011-04-18
> **josephmills said:**
> the next tine you have to change  you mac address you can do ```
macchanger -r (card name )
``` if you are rockin a static ip then it should never have to change ip's (you pay for that) So after you  logged into your router did you contact your isp to let them know what happened? As I know with my isp with a static ip they wont even let you in-to your router and they do all the "work" for you. So the first thing that I would do is call my isp and complain about this if you are signed up for a static account then there is 24hour/365day support usually. but in  the mean time could you show us a ```
ifconfig 
``` (take out the important info ) and a ```
lshw
```thanks

lshw:

myx-laptop                
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2009MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
 capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:27 memory:d0000000-dfffffff(prefetchable) ioport:d800(size=256) memory:fdef0000-fdefffff memory:fdec0000-fdedffff(prefetchable)
           *-multimedia
                description: Audio device
                product: RV620 Audio device [Radeon HD 34xx Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:fdeec000-fdeeffff
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fff0(size=16)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:fddff000-fddfffff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:fddfe000-fddfefff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:fddfd000-fddfdfff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:24:21:05:0f:90
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis190 driverversion=1.3 ip=49.140.72.7 latency=0 multicast=yes
             resources: irq:19 memory:fddfcc00-fddfcc7f ioport:cc00(size=128)
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=64
             resources: irq:17 ioport:c800(size=8) ioport:c400(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b800(size=16) ioport:b400(size=128)
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:fdf00000-fdffffff
           *-network DISABLED
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:43:62:08:d9
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fdff0000-fdffffff
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:fe000000-febfffff ioport:fa000000(size=50331648)
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:fddf4000-fddf7fff
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage



much thanks

---

