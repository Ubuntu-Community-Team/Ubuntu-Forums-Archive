---
title: "Wireless issue when switching to Lubuntu"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by mcman56 on 2012-12-26
I'm doing a fresh install of lubuntu on a system that was running ubuntu.  Wireless with WICD was good in ubuntu.  WICD is loaded in lubuntu.  

[LIST]
[*]WICD shows No wireless networks found
[*]System Profiler sees a network adapter and shows a MAC address.
[*]lshw in a terminal shows what looks like the correct name of the adapter and driver but also shows *- network DISABLED.
[*]rfkill list shows no hardware or software block
[*]iwconfig shows - no wireless extensions and wlan0 - Managed Access Point: Not associated, TX power 0 dBm, RTS thr: off, Fragment thr: off
[*]chrome works from a wired connection, download of a screen print program did not complete so I don't have screen prints
[*]ifconfig shows eth0 and lo but no wlan
[*]I reloaded WICD in package manager with no affect.  Lubuntu software center does not seem to work correctly
[/LIST]
I seems off that everything worked in ubuntu but not now

---

### Post by mcman56 on 2012-12-26
On boot up, I noticed a message saying the broadcom driver was not loading.  There is a way to query the system and it says it is a 4320 and the instructions are not clear.  14e4.4320.  Looking back Ubuntu saw it as a different broadcom.

---

### Post by mcman56 on 2012-12-26
Actually a 4306  14e4.4320 (rev2)

---

### Post by Hadaka on 2012-12-26
Hi, try this

```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```

---

### Post by mcman56 on 2012-12-26
The driver now seems to be there but I'm not seeing a wireless network.  (lshw no longer shows network disabled.)  I have used wicd in the past but not network manager.  Should it see all available networks?  Thanks!!



WARNING: you should run this program as super-user.
us-hp-nx9010-dh938u       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 2793MHz
          capacity: 2793MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr cpufreq
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
          product: RS200/RS200M AGP Bridge [IGP 340M]
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64
          resources: irq:0 memory:d4000000-d7ffffff memory:d0007000-d0007fff
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 340M]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:9000(size=4096) memory:d0300000-d03fffff memory:d8000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RS200 [Radeon IGP330M/340M/350M]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:10 memory:d8000000-dfffffff ioport:9000(size=256) memory:d0300000-d030ffff memory:d0320000-d033ffff
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_ali5451 latency=64 maxlatency=24 mingnt=2
             resources: irq:5 ioport:1000(size=256) memory:d0000000-d0000fff
        *-isa
             description: ISA bridge
             product: M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=64
             resources: memory:d0001000-d0001fff ioport:1400(size=256)
        *-network:0
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:10 memory:d0002000-d0003fff
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:11 memory:d0004000-d0004fff ioport:1c00(size=256) ioport:1800(size=256) memory:54000000-57ffffff memory:50000000-53ffffff
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:2000(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:2020(size=32)
        *-usb:2
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: b.2
             bus info: pci@0000:00:0b.2
             version: 51
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:d0005000-d00050ff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:10 memory:d0005800-d0005fff memory:d0008000-d000bfff
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_ali latency=32 maxlatency=4 mingnt=2
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2040(size=16)
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0
             resources: irq:0
        *-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0f:20:24:94:56
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.5 latency=90 maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:10 ioport:2400(size=256) memory:d0006000-d0006fff memory:4c000000-4c00ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4d:19:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=3.2.0-35-generic firmware=295.14 multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
us@us-HP-nx9010-DH938U:~$

---

### Post by Hadaka on 2012-12-26
Hi,try this to activate the b43 driver

```
sudo modprobe b43 
```

enter this command and without booting
see if you show available networks.

thanks

---

### Post by mcman56 on 2012-12-27
it now sees the connection but does not connect.  Thanks!

I did reload the whole system again so there is no wicd.

---

### Post by Hadaka on 2012-12-27
ok, well thats an improvement, lets unload wicd
and see if that helps.

```
sudo apt-get purge wicd && sudo apt-get install network-manager --reinstall
sudo modprobe b43 
```dont boot...unplug the ethernet cable and see if it connects.

Late here,,,just noticed you already unloaded wicd

---

### Post by mcman56 on 2012-12-27
Now it works.  The last issue was my wireless router.  I rebooted it and then connected.  For some reason, this router has issues with non-windows systems including Linux, Apple products (computers, phones) and a Kindle.  A static IP helps but does not always cure.  I may need to try a static IP on this install also.  Thanks for your help on this.

---

### Post by Hadaka on 2012-12-27
Glad it is working. !

---

