---
title: "Plain english PLEASE!"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by rocksavs on 2011-10-19
I upgraded to 11.10 and now I cant connect to my wireless network. I go in and create new network and its there even looks like Its connected, however, I try to connect and it says something along the lines of "unable to connect to server". I go to the connect to hidden network find the one I created again it looks as if its connected I click oon Firefox and again get the "unable to connect to network". When I first installed "Ubuntu" just a few weeks ago, I had to switch the firewall and then everything was great! For some reason now, I cant do that. This update took place this past Thursday. On Monday I was able to connect SOMEHOW, and once I shut down I havent been able to again.
 
Asking me to show input or output or any put I dont know how to do that. I just need someone to explain to me in plain english what I have to do and not give me some code to input. Until this upgrade I was loving Ubuntu.
 
HELP PLEASE!!!!!

---

### Post by pdc on 2011-10-19
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

give as much information as possible

the networking forum runs on information !       :P

---

### Post by rocksavs on 2011-10-19
That is as much info as possible!

---

### Post by jonobr on 2011-10-19
Come on squire, Respectfully, your not even trying here.
There is no magic bullet that fixes this.

The link the above poster send you is a lot of info granted, but in order to help you (which a lot of people in this forum try to do)you need to help yourself.

On your desktop 
go to applications accessories and at type 

```
lshw  
```

then 

```
ifconfig -a
```


then 

```
cat /etc/network/interface
```

then 

```
cat /etc/resolv.conf
```

Copy all that and post at least that much.
You would have to do the same with any OS.
eg - in Windows , type cmd, ipconfig /all
ipconfig /release

While your at it, I would also recommend changing the title of this thread to something meaningful and searchable.
People look through posts to see if there is an issue similar to theirs,

recommend you put in "Wireless adapter (insert make here) not working after upgrade to 11.10"

---

### Post by collisionystm on 2011-10-19
> **rocksavs said:**
> I upgraded to 11.10 and now I cant connect to my wireless network. I go in and create new network and its there even looks like Its connected, however, I try to connect and it says something along the lines of "unable to connect to server". I go to the connect to hidden network find the one I created again it looks as if its connected I click oon Firefox and again get the "unable to connect to network". When I first installed "Ubuntu" just a few weeks ago, I had to switch the firewall and then everything was great! For some reason now, I cant do that. This update took place this past Thursday. On Monday I was able to connect SOMEHOW, and once I shut down I havent been able to again.
 
Asking me to show input or output or any put I dont know how to do that. I just need someone to explain to me in plain english what I have to do and not give me some code to input. Until this upgrade I was loving Ubuntu.
 
HELP PLEASE!!!!!


In other words your wireless card just can't see your network. You are manually creating a network for it in network manager, and trying the ' connect to hidden ' because that is the only option that you were left with on that menu. Correct?

Open the terminal, lets see what kind of card we are working with.

type 

lspci

post the output, please.

Thanks!

---

### Post by inobe on 2011-10-19
go in network settings, remove any previous connections, restart, find network, enter in credentials.

---

### Post by rocksavs on 2011-10-19
Ok. Sorry about the crabbiness. Now for some reason I am able to log on. When I got on about 5 minutes before it wouldnt let me. I looked at the forum from another source came back to this computer and it had found a bunch of wireless networks. Any ideas as to why now? Any ideas on how to keep it that way? Any and all input would be great!

Again sorry about the crabbiness!

---

### Post by collisionystm on 2011-10-19
Probably just a delay? It would really help to know what make and model card you have

---

### Post by rocksavs on 2011-10-19
Im sorry again but how do I see what model card I have?

---

### Post by collisionystm on 2011-10-19
Open terminal

TyPe lspci

Copy and paste the output

---

### Post by rocksavs on 2011-10-19
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3824MiB
     *-cpu
          product: Intel(R) Pentium(R) CPU        P6000  @ 1.87GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.5.2
          serial: 0002-0652-0000-0000-0000-0000
          size: 933MHz
          capacity: 933MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm popcnt lahf_lm arat cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             width: 64 bits
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 12
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:f0806800-f080680f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f0807000-f08073ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:42 memory:f0600000-f0603fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:c0400000-c05fffff ioport:c0600000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:f0500000-f05fffff ioport:c0200000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 70:f1:a1:a1:0b:39
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic-pae firmware=N/A ip=192.168.15.47 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0500000-f0503fff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:f0400000-f04fffff ioport:c0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: c1
                serial: b8:ac:6f:70:7d:2f
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
                resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0807400-f08077ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:1840(size=8) ioport:1814(size=4) ioport:1818(size=8) ioport:1810(size=4) ioport:1820(size=32) memory:f0806000-f08067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f0807800-f08078ff ioport:1860(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:f0605000-f0605fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
I hope this helps

---

### Post by collisionystm on 2011-10-20
Broadcom bcm4313

---

### Post by rocksavs on 2011-10-20
So what does that mean?

---

### Post by inobe on 2011-10-20
> **rocksavs said:**
> So what does that mean?

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+broadcom+bcm4313+driver&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+broadcom+bcm4313+driver&ie=utf-8&oe=utf-8)

or

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+broadcom+bcm4313+driver&ie=utf-8&oe=utf-8#sclient=psy-ab&hl=en&client=ubuntu&channel=fs&source=hp&q=ubuntu+broadcom+bcm4313&pbx=1&oq=ubuntu+broadcom+bcm4313&aq=f&aqi=p-p1g-b3&aql=1&gs_sm=s&gs_upl=264567l266642l0l268200l7l7l0l0l0l0l205l956l2.4.1l7l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=dc20b2672385f007&biw=1920&bih=905](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+broadcom+bcm4313+driver&ie=utf-8&oe=utf-8#sclient=psy-ab&hl=en&client=ubuntu&channel=fs&source=hp&q=ubuntu+broadcom+bcm4313&pbx=1&oq=ubuntu+broadcom+bcm4313&aq=f&aqi=p-p1g-b3&aql=1&gs_sm=s&gs_upl=264567l266642l0l268200l7l7l0l0l0l0l205l956l2.4.1l7l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=dc20b2672385f007&biw=1920&bih=905)


it can mean a number of things, but what's important is you know what that may be!

googling will help, google is useful when put to use :D

---

### Post by pdc on 2011-10-21
or this 

[http://tinyurl.com/62osrbd](http://tinyurl.com/62osrbd)           :D

---

