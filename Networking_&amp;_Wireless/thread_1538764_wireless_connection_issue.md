---
title: "wireless connection issue"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by vanspud on 2010-07-25
Hi,

I am having a strange issue with my laptop, I recently dual booted Ubuntu onto my laptop that came with Vista on it.

Now when I'm in Vista, my laptop can connect to the Internet(wireless) no matter were I am in my house. However when I'm in Ubuntu, I have to be sitting next to the router to get on the Internet which is not very convenient as it's not the nicest of rooms to work from.

I was just wondering for advice on were I should even start looking to solve this issue? Is it a piece of hardware in my laptop that Ubuntu is not compatible with and I'd have to get a new piece or is there some commands I can run to get to the bottom of it?

Any help is appreciated.

---

### Post by vanspud on 2010-07-26
Just an update here, I can see the network I need to connect too anywhere I am, but it just fails to connect. How do I find out what drivers I have and how do I know what one's I need?

---

### Post by vanspud on 2010-07-26
I disabled the security on my router and it says signal strenght is 100% even when I leave the room, however it still fails to connect.

I'm on Ubuntu 10.04, Advent laptop....

Any help/ advice out there?

---

### Post by rajan on 2010-07-27
what kind of wireless card do you have on your notebook? have there been others posting about problems with it on an ubuntu platform?

---

### Post by vanspud on 2010-07-28
Thanks for replying Rajan, I'm limping along here like a wounded dog trying o solve it. 

I have googled it a lot and it seems to be a common problem across all different versions of Ubuntu(I'm on 10.04). I can see the network but it just keeps prompting me for the password, I also tried turning of the password on the router and it still didn't work. 

I typed in 'hwinfo' and got the following back...

under 'wlan controller' it says the driver is 'rtl8187
under 'ethernet' it says the driver is 'sis190'

is that information any use or is there better information I can give? Thanks again for reply.

---

### Post by rajan on 2010-07-30
Hey vanspud, it looks like you're in a very confusing situation

i can't imagine why it might work simply because you're closer to the router. I have seen transfers become faster when you get closer to the router, but i don't know why that may be tied to authentication. 

i might have some time tomorrow to investigate the causes of this tomorrow, but i'm definitely no expert on the subject. 

just a little more fishing around, try the following commands and post them on here. hopefully someone will be able to help. 

ifconfig (overview of your network interfaces)
lshw (list hardware)
uname -a (version of ubuntu, updates, etc)
iwconfig (wireless network interface overview)

---

### Post by vanspud on 2010-08-01
(this is what I get back when I'm away from the router, I can see the network but can't connect)

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:03:0d:9d:e6:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:332797 (332.7 KB)  TX bytes:332797 (332.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:de:11:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lshw

description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1884MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1867MHz
          capacity: 1867MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:a0000000-afffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:b0000000-b00fffff memory:c0000000-cfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:b0000000-b001ffff ioport:9000(size=12
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
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:1080(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TMC0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:b0104000-b0104fff
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:b0105000-b0105fff
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
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:b0106000-b0106fff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:03:0d:9d:e6:ff
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis190 driverversion=1.3 latency=0 multicast=yes
             resources: irq:19 memory:b0307000-b030707f ioport:1000(size=12
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
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:10c8(size= ioport:10bc(size=4) ioport:10c0(size= ioport:10b8(size=4) ioport:10a0(size=16)
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
             resources: irq:18 memory:b0100000-b0103fff
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:de:11:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


uname -a

2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          
eth0      no wireless extensions.

---

