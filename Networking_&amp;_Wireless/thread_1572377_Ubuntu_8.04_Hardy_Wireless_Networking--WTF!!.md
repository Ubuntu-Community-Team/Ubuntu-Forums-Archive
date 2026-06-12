---
title: "Ubuntu 8.04 Hardy Wireless Networking--WTF?!!"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by Rockerbabysitter on 2010-09-11
Okay, I've got the same newbie problem as the other newbies regarding wireless networking.  I got it up and running a few months back, but the nimrod I rent from did something with his Verizon router and screwed everything up; we've got Ubuntu 8.04 on a Dell Dimension 4600C.  Now I have to try getting my gf's Netgear WG111v3 back up & running.  I've tried reinstalling all the ndiswrapper packages; the WB111v3 wireless dongle shows up as installed hardware, and I get the connection status bar at the top right, but I cannot connect to any web pages.  So, from the beginning, can somebody please help get this working again?  I realize everyone's machine is unique, and I have included some codes for diagnosis.  Do I need to remove/reinstall any components?  thanks for any help you may provide...

Here's a list of commands; let me know what else you need:

user@user-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:8b:fa:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:8b:fa:84  
          inet addr:169.254.9.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1020327 (996.4 KB)  TX bytes:1020327 (996.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:ee:bc:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213729 (208.7 KB)  TX bytes:257651 (251.6 KB)

user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@user-desktop:~$ ndiswrapper -l
wg111v3 : driver installed
    device (0846:4260) present

user@user-desktop:~$ lsusb
Bus 005 Device 003: ID 0846:4260 NetGear, Inc. 
Bus 005 Device 002: ID 05dc:a764 Lexar Media, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

user@user-desktop:~$ lshw
WARNING: you should run this program as super-user.
user-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: xxxMiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: Conexant
                vendor: Conexant
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:01:01.0
                logical name: eth0
                version: 01
                serial: 00:0b:db:8b:fa:84
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
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
       serial: 00:22:3f:ee:bc:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg111v3 driverversion=1.52+NETGEAR Inc.,05/11/2007,5.1 multicast=yes wireless=IEEE 802.11g
user@user-desktop:~$ 
user@user-desktop:~$

---

### Post by MaindotC on 2010-09-11
Your wireless card isn't connected to an access point and does not have an IP address assigned.  Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) for troubleshooting this issue.  Also, when you post output from a shell please enclose it in [code] tags.

---

### Post by ieee488 on 2010-09-11
You really should consider upgrading to 9.10

There was a sizeable jump in wireless compatibility from 8.04

---

### Post by MaindotC on 2010-09-11
Sometimes you can't upgrade because 9.04 and above does not support some old hardware.  I have a Thinkpad T60 that has a built in ATIx1300.  ATI does not make a driver for this card that will work in 9.04 and above because these distros use a higher version of X window system that does not come in 8.10 and below.  I have to use 8.04.

---

### Post by Rockerbabysitter on 2010-09-11
Yeah... like I said, it's my gf's comp, not mine.  Thanks for the input--we'll give it a shot and see what happens... :D

---

### Post by Rockerbabysitter on 2010-09-11
> **strAlan said:**
> Your wireless card isn't connected to an access point and does not have an IP address assigned.  Please consult the [Ubuntu Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") for troubleshooting this issue.  Also, when you post output from a shell please enclose it in [code] tags.

Well, THAT was a little more confusing & frustrating.  Not easy learning this after being a PC for so long! :o

I went through this guide and still can't get it working.  Can I just remove all networking components and try over?  I'm really not computer-stupid, I just have all kinds of things going on around where I'm staying and it's easy to lose concentration around here.  None of the Troubleshooting seemed to work. I can ping the DNS, but not the router.  I can't seem to assign the IP address manually.  What do I need here?

---

### Post by MaindotC on 2010-09-11
You need to tell us at what point of the troubleshooting you failed.  When you say you can ping the DNS but not the router, do you mean you can ping a DNS server or you can ping a machine by it's FQDN?  Were you able to ping a machine on your network or outside your network?

When you say you can't assign an IP address manually - what is happening when you attempt it?  Are you using NetworkManager or are you using /etc/network/interfaces?

---

