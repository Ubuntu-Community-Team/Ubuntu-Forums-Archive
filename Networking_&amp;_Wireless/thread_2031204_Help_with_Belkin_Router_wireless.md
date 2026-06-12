---
title: "Help with Belkin Router wireless"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by GCSTider on 2012-07-21
Can somebody assist with setting up the wireless portion of the Belkin Wireless Router. The wired connection works, but unable to get it to connect using wireless.

---

### Post by GCSTider on 2012-07-21
PLEASE HELP. I'M AT MY WITS END!!!!

More information. The belkin router works fine hard wired. I can see the router in wireless networks. I enter my password and it just continues to blink and asks for password again. Does anybody have any suggestions? Thanks in advance.

---

### Post by steeldriver on 2012-07-21
Your thread title is kind of confusing - do you need help with the router setup, or with configuring the interface on the computer?

If you are confident you have the correct wireless credentials, then it sounds like there may be a problem with drivers and/or firmware - we are going to need more information from you so please open a terminal window and type the following commands:

```
lspci -nn | grep -i net

lshw

nm-tool
```

and post back the results

---

### Post by kurt18947 on 2012-07-21
I'm assuming this is a new router. What is the model?  I doubt they're all the same.   Most routers are administered from a browser.  Your documentation, or information found on Belkin's web site should have the default i.p. address, user name and password  information. You type something like [http://192.168.1.1](http://192.168.1.1) or whatever and you'll get to an login page.  Once you get logged in it may make sense.  It's an excellent idea to change the router name and password so somebody doesn't do it remotely for you and lock you out of your own router while using it for their own purposes.  I also disable remote administration unless you have a good reason to leave it enabled.

---

### Post by GCSTider on 2012-07-21
steeldriver - here are the results.

donna@donna-Latitude-D830:~$ lspci -nn | grep -i net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
donna@donna-Latitude-D830:~$ lshw
WARNING: you should run this program as super-user.
donna-latitude-d830       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2010MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
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
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fa000000-feafffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84M [Quadro NVS 140M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:fa000000-fbffffff ioport:ef00(size=128) memory:fc000000-fc01ffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f20(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:febfc000-febfffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:84000000-841fffff ioport:84200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:f9f00000-f9ffffff ioport:84400000(size=2097152)
           *-network UNCLAIMED
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f9ffc000-f9ffffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:f9c00000-f9efffff ioport:f0000000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:4000(size=4096) memory:f9b00000-f9bfffff ioport:84600000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:a1:1f:7c
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5755m-v3.29 ip=192.168.2.2 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:47 memory:f9bf0000-f9bfffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f80(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f60(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:f9a00000-f9afffff ioport:80000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:f9a00000-f9a00fff ioport:5000(size=256) ioport:5400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:19 memory:f9aff000-f9afffff memory:f9afe800-f9afefff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D200
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=32) memory:febfb800-febfbfff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:febfb700-febfb7ff ioport:10c0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 2c:b0:5d:76:fa:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx32 driverversion=1.56+,08/26/2009, 5.10.79.30 multicast=yes wireless=IEEE 802.11g
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
donna@donna-Latitude-D830:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:1C:23:A1:1F:7C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        2C:B0:5D:76:FA:9B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Logan's WiFi:    Infra, 00:22:3F:9D:57:35, Freq 2437 MHz, Rate 54 Mb/s, Strength 21 WEP
    Half-Blood:      Infra, 00:1C:10:1C:F6:5F, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA
    BRANDY-PC_Network: Infra, 00:26:F3:6B:8A:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    JDHarmonHouse:   Infra, 94:44:52:B0:3F:11, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2

---

### Post by GCSTider on 2012-07-21
System information: Running Ubuntu 10.04 on a Dell Lattitude D830.  The router is a Belkin Surf Wireless Router. Once again, if connected via network cable, everything is good. Can't get it to work wirelessly. Can see the wireless network, but can't log in.

---

### Post by kurt18947 on 2012-07-21
> **GCSTider said:**
> System information: Running Ubuntu 10.04 on a Dell Lattitude D830.  The router is a Belkin Surf Wireless Router. Once again, if connected via network cable, everything is good. Can't get it to work wirelessly. Can see the wireless network, but can't log in.


[http://en-us-support.belkin.com/app/answers/detail/a_id/7310](http://en-us-support.belkin.com/app/answers/detail/a_id/7310)
Pay particular attention to #6.
[ATTACH]221597[/ATTACH]
Looking at Belkin's quick setup guide, it looks like the manual setup is accessed via 192.168.2.1 in a browser address bar.

---

### Post by GCSTider on 2012-07-21
> **kurt18947 said:**
> Most likely there's some sort of default password.  For instance, one router uses WEP out of the box.  The default wireless password is part of the router serial #.  Belkin should document the defaults somewhere.  And yes, I'd recommend changing the defaults as soon as you can get to the administration pages.

I've changed the tried the default password and also changed the password.

---

### Post by kurt18947 on 2012-07-21
> **GCSTider said:**
> I've changed the tried the default password and also changed the password.

Good deal.  I was revising my post while you were posting this.  A handy thing to remember when messing about with routers is there is a reset button which returns the box to factory default.  If you foul things up beyond all recogition, push & hold the reset button then try again :).  This procedure has been tested and approved by yours truly :oops:.

---

