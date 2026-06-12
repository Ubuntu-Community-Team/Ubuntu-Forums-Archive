---
title: "Wireless"
date: 2006-02-16
forum: Networking &amp; Wireless
---

### Post by StageMgr2Stars on 2006-02-16
Thanks to all to who helped a while back with my ndiswrapper problem. The driver was sucessfully installed (or so I think). Where do I go from here. I have Dell Inspiron 2200 with a Dell Wireless 1370 card. I am using Breezy. I am at a stand still and this is the one thing that is so important that I get working. So please help.

when I type in iwconfig I get:

courtneyscott@courtneyscott:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.


When I check the installed drivers I see:

Installed ndis drivers:
bcmwl5 driver present, hardware present

(That was the driver I installed)


Thanks again.

---

### Post by bscbrit on 2006-02-16
Use this link, come back when you get stuck... :-D 

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by Lambert on 2006-02-16
The troubleshooting and help for ndiswrapper is also being moved and expanded from the page bscbrit gave you to. You may want to look here also.



[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)



Basically with no wlan0 output with iwconfig tells that you don't have a working driver.

Just a quick check, is ndiswrapper loaded? check with this command

lsmod | grep ndis

if you just get a new prompt then it's not. 

sudo modprobe ndiswrapper 

will load it.

---

### Post by StageMgr2Stars on 2006-02-16
Okay, that is majorly confusing to me. I dont understand it. I put in the command:

courtneyscott@courtneyscott:~$ sudo lshw
courtneyscott
    description: Portable Computer
    product: Inspiron 2200
    vendor: Dell Inc.
    serial: 5R3HM81
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-5200-1033-8048-B5C04F4D3831
  *-core
       description: Motherboard
       product: 0U6962
       vendor: Dell Inc.
       physical id: 0
       serial: .5R3HM81.CN486435921273.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (09/18/2005)
          size: 64KB
          capacity: 512KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.6
          slot: Microprocessor
          size: 1700MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KB
             capacity: 8KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: Chip DDR Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: System Board Memory
             size: 256MB
             width: 64 bits
             clock: 333MHz (3.003ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             vendor: AD00000000000000
             physical id: 1
             serial: FFFF0442
             slot: DIMM_B
             size: 256MB
             width: 64 bits
             clock: 333MHz (3.003ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:dff00000-dff7ffff ioport:ec38-ec3f iomemory:c0000000-cfffffff iomemory:dfec0000-dfefffff irq:16
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:dff80000-dfffffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf80-bf9f irq:16
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB MOUSE
                   vendor: CHESEN
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf60-bf7f irq:17
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf40-bf5f irq:18
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf20-bf3f irq:19
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ffa80800-ffa80bff irq:16
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
                vendor: Linux 2.6.12-10-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: ImageMate 5 in 1 Reader/Writer
                   vendor: SanDisk
                   physical id: 2
                   bus info: usb@5:2
                   logical name: scsi0
                   version: 93.12
                   serial: 0301690466
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@0.0:0.0
                      logical name: /dev/sda
                      version: 9312
                      capabilities: removable
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:20000000-20000fff irq:16
           *-network:0 UNCLAIMED
                description: Network controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                resources: iomemory:dfdfe000-dfdfffff irq:1
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 03
                serial: 00:12:3f:fb:cb:ab
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A ip=10.197.4.30 link=yes multicast=yes port=MII speed=100MB/s
                resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:ed00-edff ioport:ec40-ec7f iomemory:dfebfe00-dfebffff iomemory:dfebfd00-dfebfdff irq:16
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:ee00-eeff ioport:ec80-ecff irq:17
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:bfa0-bfaf irq:16
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD400VE-75HDT1
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 11.07D11
                   serial: WD-WXE805185736
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off smart=on
              *-cdrom
                   description: DVD reader
                   product: HL-DT-STCD-RW/DVD-ROM GCC-4244N
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: B101
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:10c0-10df irq:10
  *-battery
       product: DELL5A1PAN
       vendor: Panasonic
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 43000mWh
       configuration: voltage=14.8V



I have no idea what I am doing...

---

### Post by StageMgr2Stars on 2006-02-16
[QUOTE=Lambert]The troubleshooting and help for ndiswrapper is also being moved and expanded from the page bscbrit gave you to. You may want to look here also.



[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)



Basically with no wlan0 output with iwconfig tells that you don't have a working driver.

Just a quick check, is ndiswrapper loaded? check with this command

lsmod | grep ndis

if you just get a new prompt then it's not. 

sudo modprobe ndiswrapper 

will load it.[/QUOTE]
Its loaded and still nothin'

---

### Post by Lambert on 2006-02-16
If it's loaded then we need to find another driver to use with ndiswrapper. Which one did you use and what's the make, model number and version of your card?

---

### Post by StageMgr2Stars on 2006-02-16
[QUOTE=Lambert]If it's loaded then we need to find another driver to use with ndiswrapper. Which one did you use and what's the make, model number and version of your card?[/QUOTE]
It is a Dell Wireless 1370 WLAN Mini-PCI Card. Whats even more confusing is that if I go to System - Admin - Windows Wireless Drivers, its appears there. Once I hit configure network, it brings me back to the network page but wlan still isnt listed. Just my ethernet and modem. :-/

---

### Post by Lambert on 2006-02-16
There is a difference between those two windows. In the windows wireless device  window you're looking at, that simply reads the device memory section and recognizes that it is a ndis device. Real simple explanation and I could be off on my terminology.

The network manager is different and needs a working driver so the kerenel can talk to the device and recognize it as a wireless functioning device, again exscuse the poor explanation and simple terminology. 

So hopefull you understand why you see differences between the two.

I didn't see anything on your device so I need a little more to do some research.

From terminal run these commands and post output.

sudo lspci -v | grep -A 4 Eth

sudo lspci -n

I'm looking for the device and manf id which will look like xxxx:xxxx in the lspci -n output.

Though others with Dell truemobile minipc devices, I noticed they are using the bcmwl5a.inf driver and it looks like you're using the bcmwl5.inf driver.

You can try to remove current driver like this..

sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwl5

then remove the files from your hard drive and copy over the bcmwl5a.inf and .sys file on to your hard drive and install that driver

---

### Post by StageMgr2Stars on 2006-02-16
[QUOTE=Lambert]There is a difference between those two windows. In the windows wireless device  window you're looking at, that simply reads the device memory section and recognizes that it is a ndis device. Real simple explanation and I could be off on my terminology.

The network manager is different and needs a working driver so the kerenel can talk to the device and recognize it as a wireless functioning device, again exscuse the poor explanation and simple terminology. 

So hopefull you understand why you see differences between the two.

I didn't see anything on your device so I need a little more to do some research.

From terminal run these commands and post output.

sudo lspci -v | grep -A 4 Eth

sudo lspci -n

I'm looking for the device and manf id which will look like xxxx:xxxx in the lspci -n output.

Though others with Dell truemobile minipc devices, I noticed they are using the bcmwl5a.inf driver and it looks like you're using the bcmwl5.inf driver.

You can try to remove current driver like this..

sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwl5

then remove the files from your hard drive and copy over the bcmwl5a.inf and .sys file on to your hard drive and install that driver[/QUOTE]
courtneyscott@courtneyscott:~$ sudo lspci -v | grep -A 4 Eth
0000:02:08.0 Ethernet controller: Intel Corp.: Unknown device 1068 (rev 03)
        Subsystem: Dell: Unknown device 01a4
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at df40 [size=64]



courtneyscott@courtneyscott:~$ sudo lspci -n
0000:00:00.0 0600: 8086:2590 (rev 03)
0000:00:02.0 0300: 8086:2592 (rev 03)
0000:00:02.1 0380: 8086:2792 (rev 03)
0000:00:1d.0 0c03: 8086:2658 (rev 03)
0000:00:1d.1 0c03: 8086:2659 (rev 03)
0000:00:1d.2 0c03: 8086:265a (rev 03)
0000:00:1d.3 0c03: 8086:265b (rev 03)
0000:00:1d.7 0c03: 8086:265c (rev 03)
0000:00:1e.0 0604: 8086:2448 (rev d3)
0000:00:1e.2 0401: 8086:266e (rev 03)
0000:00:1e.3 0703: 8086:266d (rev 03)
0000:00:1f.0 0601: 8086:2641 (rev 03)
0000:00:1f.1 0101: 8086:266f (rev 03)
0000:00:1f.3 0c05: 8086:266a (rev 03)
0000:02:01.0 0607: 104c:ac56
0000:02:03.0 0280: 14e4:4318 (rev 02)
0000:02:08.0 0200: 8086:1068 (rev 03)



The bcmwl5.inf driver is what I downloaded off the dell site and it said it was specifically for the 1370

---

### Post by StageMgr2Stars on 2006-02-16
could it be something with the bcmwl5.sys b/c I dont see that anywhere on ndiswrapper

---

### Post by Lambert on 2006-02-17
post the output of this directory

```
sudo cat /etc/ndiswrapper/bcmwl5/
```

After very little research, I do believe you need the l5.inf and not the lfa.inf for you device. For some odd reason though driver isn't working.

---

### Post by StageMgr2Stars on 2006-02-17
sorry that took me so long, its been a busy day...

courtneyscott@courtneyscott:~$ sudo cat /etc/ndiswrapper/bcmwl5/
Password:
cat: /etc/ndiswrapper/bcmwl5/: Is a directory

there ya go.

---

### Post by Lambert on 2006-02-17
My bad, wrong command, post output of this one.

```

ls /etc/ndiswrapper/bcmwl5/

```

---

### Post by StageMgr2Stars on 2006-02-17
courtneyscott@courtneyscott:~$ ls /etc/ndiswrapper/bcmwl5/
14E4:4311:1028:0007.5.conf  14E4:4320:1028:0001.5.conf
14E4:4311:1028:0008.5.conf  14E4:4320:1028:0002.5.conf
14E4:4311.5.conf            14E4:4320:1028:0003.5.conf
14E4:4312:1028:0007.5.conf  14E4:4320:1028:0004.5.conf
14E4:4312:1028:0008.5.conf  14E4:4320.5.conf
14E4:4312.5.conf            14E4:4324:1028:0001.5.conf
14E4:4318:1028:0005.5.conf  14E4:4324:1028:0002.5.conf
14E4:4318:1028:0006.5.conf  14E4:4324:1028:0003.5.conf
14E4:4318.5.conf            14E4:4324:1028:0004.5.conf
14E4:4319:1028:0005.5.conf  14E4:4324.5.conf
14E4:4319:1028:0006.5.conf  bcmwl5.inf
14E4:4319.5.conf            bcmwl5.sys
courtneyscott@courtneyscott:~$

---

### Post by Lambert on 2006-02-18
I think you have to many .conf files in that folder and causing a problem, but this is just a guess after doing some searching.

So here is my current suggestion.

move everything out of the folder except the files begininng with  14E4:4318

You can do it from a terminal by doing this.

```

mkdir ~/ndiswrapper_backups
sudo mv /etc/ndiswrapper/bcmwl5/ 14E4:4311* ~/ndiswrapper_backups

```

Adding the * at the end is a wild card  will move all files starting that way. There is a space between the * and ~.

redo the mv command with all the the .conf files.

So the only thing left is bcmwl5.inf bcmwl5.sys and the 14E4:4318 .conf files.

You can also do the move graphicall by running this command

gksudo nautilus

---

### Post by StageMgr2Stars on 2006-02-18
deleted post.

---

### Post by StageMgr2Stars on 2006-02-18
[QUOTE=Lambert]I think you have to many .conf files in that folder and causing a problem, but this is just a guess after doing some searching.

So here is my current suggestion.

move everything out of the folder except the files begininng with  14E4:4318

You can do it from a terminal by doing this.

```

mkdir ~/ndiswrapper_backups
sudo mv /etc/ndiswrapper/bcmwl5/ 14E4:4311* ~/ndiswrapper_backups

```

Adding the * at the end is a wild card  will move all files starting that way. There is a space between the * and ~.

redo the mv command with all the the .conf files.

So the only thing left is bcmwl5.inf bcmwl5.sys and the 14E4:4318 .conf files.

You can also do the move graphicall by running this command

gksudo nautilus[/QUOTE]
okay, I did all of this. Now what? I typed in wlan once I was done and still didn't see anything

---

### Post by Lambert on 2006-02-18
run these commands

sudo modprobe -r ndiswrapper

sudo modprobe ndiswrapper

simply removes then reinserts it. If you don't see the wlan0 interface then I'm stumped at this point. There are those that have a broadcom chipset and never get it set up, and I haven't seen pattern to why or what's happening.

All I can say from here is
1. Try a different driver. Even though you pulled it from dell's site, it's still a windows driver so it means nothing in linux. It's best to find a driver that someone has verified working. You can even use drivers from other manufactures if the chipset matches. your chipset is the 14E4:4318. You can go to the ndiswrapper wiki/list section and find a device with the same chipset and try those drivers as they are verified.
2. Go to the ndiswrapper gurus. They might see or know something we are missing here.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)


I know it's annoying etc.... I was here many months ago. Bought a device natively supported with a linux driver. Best $30 I spent.

One of the problems in linux is hardware support by vendors. Write broadcom/dell and let them know your disgust in their support for linux. Can't help know but can help to improve.

There might be someone who has solved the same problem you're having. You may need to settle in a little while, and keep bumping the thread every couple days for a week or so.

At this point, I'll keep watching and if I notice something else I can recommend I will other wise I wish you luck and patience.

---

### Post by bscbrit on 2006-02-19
I have experienced a similar problem but found it was resolved by using the bcmwl5a driver, rather than the bcmwl5. It is worth a try but, unlike me, remember to remove the bcmwl5 driver from your computer before trying to get the 5a driver loaded.  Lost about 30 minutes before I realised how stupid I was :mrgreen:

I agree with Lambert regarding complaining but, to be honest, I have never received a satisfactory reply as a result.  I understand the economics but some companies are actually quite rude.  It is, apparently, your own fault for using 'an Operating System not designed for real-world applications'....  I pointed out that the company itself used linux on its servers but left it at that point.

---

### Post by StageMgr2Stars on 2006-02-19
[QUOTE=bscbrit]I have experienced a similar problem but found it was resolved by using the bcmwl5a driver, rather than the bcmwl5. It is worth a try but, unlike me, remember to remove the bcmwl5 driver from your computer before trying to get the 5a driver loaded.  Lost about 30 minutes before I realised how stupid I was :mrgreen:

I agree with Lambert regarding complaining but, to be honest, I have never received a satisfactory reply as a result.  I understand the economics but some companies are actually quite rude.  It is, apparently, your own fault for using 'an Operating System not designed for real-world applications'....  I pointed out that the company itself used linux on its servers but left it at that point.[/QUOTE]
Heres the problem, I tried using the 5a i found randomly on the dell website but that driver isnt not for the 1370. When I loaded it, it said "driver present, hardware. no" Atleast with the 5, it said the hardware was present. If you have th 5a that worked for you, can you send it to me?

---

### Post by bscbrit on 2006-02-19
Sure - send me a PM with your email address.

---

### Post by bscbrit on 2006-02-19
Email sent - about 5 minutes ago.  You will have to work that out into your time because I haven't a clue where you are :D   EDIT Oh yes I do, NY. Duh....

And its time for my bed.....

---

### Post by StageMgr2Stars on 2006-02-19
*does the happy linux dance* even tho I didnt get your drivers, I used a bunch of suggestions to find yours and now I have wireless! My driver was bad the whole time! Damn you Dell! but Yay Ubuntu!!

---

### Post by bscbrit on 2006-02-20
Great news - see you around the forum!

---

