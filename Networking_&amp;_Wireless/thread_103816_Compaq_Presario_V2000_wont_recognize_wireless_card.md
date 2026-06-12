---
title: "Compaq Presario V2000 wont recognize wireless card"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by jmarti152000 on 2005-12-14
I hope someone can help me?


**Problem:**

I can not get my wireless card to be recognized. I have tried several times and several ways to get it up and running over the past couple of days.  I have spent hours googleing  and searching the support pages here to no avail. 

**My laptop:**
Compaq Presario  V2000 
AMD Sempron Processor

**Wireless Card:**
Netgear MA521 (Made in Taiwan)

Cards power light is on when i plug it in.
I have also tried a Dlink 650

**What I have tried:**

**Ndiswrapper:**
 I can get the driver to load with ndiswrapper that I built from source by following this tutorial [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) .  Install of ndiswrapper goes smoothly. But no luck in detecting card

Results from:
# ndiswrapper -l 
net8180         driver present

#sudo /sbin/iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


The hardware does not seem to be present.

I am new to Ubuntu -  I have used Suse and Redhat in the past so I am somewhat familiar with Linux. 

Thanks any help would be appreciated.

---

### Post by ztirffritz on 2006-01-15
I have a V2000 with a Turion64.  I'm having a similar problem.  The wireless card does not work.  Anyone find a good solution for this yet?

---

### Post by Lambert on 2006-01-15
Run these commands in terminal and post output here

```
sudo lshw
```

```
sudo cardctl ident
```

---

### Post by ztirffritz on 2006-01-16
OK, before I go too far, I should probably ask, "should I be trying to install the 32 bit or the 64 bit version of Ubuntu?"  I have a Compaq Presario V2410 w/ Turion64.  The "64" leads me to believe that I should be installing the 64 bit version, but it stalls during the install at a part at a message about the keyboard of all things.  It is very strange.  I've managed to get the Ubuntu 32 bit version to install, and the 32 bit version of SuSe to install but the wireless card doesn't work for either.  The wireless card is a Broadcom 4813 (I think this is the model number).

---

### Post by efox on 2006-01-17
i have the same laptop with the 64bit cpu...i installed ubuntu amd64...and thats where im havin the SAME problems as you...

on my desktop it works..but my cpu is 32bit on my desktop..and no problems...and im using ethernet and not wifi

anyone have any suggestions ?

---

### Post by ztirffritz on 2006-01-28
I actually managed to get the 64 bit version to install on my laptop by disabling some of the features for the graphics card.  Apparently, the problem was not with the keyboard, but rather with the next item after the keyboard.  The keyboard was the last think that actually succeeded during the install.  Keep searching on this forum and you'll find the thread.  I think that it was either in the laptop section, or the installation issues section.  I still haven't gotten the wireless card installed successfully.  I managed to get a Netgear PCMCIA card to work briefly, but then I broke it while I was trying to get the built-in card to work.  I read somewhere that the Broadcom Wireless card actually has to be activated by something in the Windows OS, so I set up my computer as a dual-boot system to try that, but it hasn't worked either.

---

### Post by eljaco on 2006-01-30
Hey, I have a Dell Inspiron 8500 and can't get my Dell TrueMobile 1300 (Broadcom wireless card) to work. The printouts I got from ```
sudo lshw
``` regarding the wireless card is:
> irq:11
           *-network:1 UNCLAIMED
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:faff6000-faff7fff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master

And ```
sudo cardctl ident

``` prints out the following: > Socket 0:
  no product info available


I doubt it makes a difference, but I am using Kubuntu.

---

### Post by Lambert on 2006-01-30
When you say you can't get it to work what have you tried? 

There is no native driver for broadcom in breezy. You need to use an app called ndiswrapper which in a nutshell makes the windows drivers work in linux. There are two links in my signature about wireless you'll find more information about ndiswrapper in either one of these.

---

### Post by eljaco on 2006-01-30
I tried using the HOWTO for the Hoary distro (see my post at the end of [http://ubuntuforums.org/showthread.php?t=25683&page=31&highlight=.inf]("http://ubuntuforums.org/showthread.php?t=25683&page=31&highlight=.inf") ) for more info.

---

### Post by Lambert on 2006-01-30
Run these two commands and post here

```
cat /proc/version
```
This one I'm not sure is correct but away from ubuntu and can't verify.



```
sudo modinfo ndiswrapper
```

---

### Post by eljaco on 2006-01-30
For the first one:

> ~$ cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

And the other:
> filename:       /lib/modules/2.6.12-9-386/misc/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.8
license:        GPL
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:        usbcore
srcversion:     9B90945C33B2D307DCEF19B
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)


---

### Post by Lambert on 2006-01-30
So one last question 

run this command

```
sudo slocate -u
```

then

```
sudo slocate ndiswrapper
```

post results of second command here.

What I think is happening

ubuntu comes with a ndiswrapper module pre-installed in 

/lib/modules/(kernel v)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

You probably didn't remove this before installing v 1.8 but it's just a guess. post results.

---

### Post by johnnyzap on 2006-03-12
I currently cannot get my DWL-650 rev P, which as I understand uses the Prism 3 chipset, to work.  I used synaptics package manager to install ndis wrapper utils and downloaded the winxp drivers from dlink.  I followed the commands for ndiswrapper, but while it says the netprism driver is present, it does not say the h/w is present.  Despite an effort, I am stuck at this point, sitting 3 feet away from my wireless router plugged in via hardline for the time being.  Here are the results of all of the commands suggested in this topic.  (very long)

matthew@ubuntu:/$ ndiswrapper -l
Installed ndis drivers:
netprism        driver present
matthew@ubuntu:/$ sudo /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

matthew@ubuntu:/$ sudo lshw
ubuntu
    description: Portable Computer
    product: Latitude CPx J650GT
    vendor: Dell Computer Corporation
    serial: 22SB701
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-32BB-1053-8042-B2C04F373031
  *-core
       description: Motherboard
       product: Latitude CPx J650GT
       vendor: Dell Computer Corporation
       physical id: 0
       slot: ESS Maestro 3i
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A16 (03/05/2003)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.8.3
          slot: Microprocessor
          size: 500MHz
          capacity: 750MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KB
             capacity: 256KB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MB
          capacity: 512MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 128MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f4000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f4000000-f7ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff ioport:ec00-ecff iomemory:fcfff000-fcffffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 3
             bus info: pci@00:03.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:10100000-10100fff irq:11
           *-network
                description: DWL-650 Wireless PC Card RevP
                product: ISL37101P-10
                vendor: D-Link
                physical id: 0
                version: A3
                slot: Socket 0
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 3.1
             bus info: pci@00:03.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:10101000-10101fff irq:11
           *-network
                description: CardBus PC Card
                physical id: 0
                version: Fast Ethernet CardBus PC Card
                slot: Socket 1
                resources: irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:860-86f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: SAMSUNG MP0402H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: UC100-19
                   serial: S03WJ30A132586
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma2 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: SAMSUNG CD-ROM SN-124
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: S004
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:dce0-dcff irq:11
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 11.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1983S Maestro-3i PCI Audio Accelerator
             vendor: ESS Technology
             physical id: 8
             bus info: pci@00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Maestro3
             resources: ioport:d800-d8ff iomemory:faffe000-faffffff irq:5
     *-network
          description: Ethernet interface
          product: RTL-8139/8139C/8139C+
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 1
          bus info: pci@06:00.0
          logical name: eth0
          version: 10
          serial: 00:10:60:5f:ea:86
          size: 100MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.5 link=yes multicast=yes port=MII speed=100MB/s
          resources: ioport:4800-48ff iomemory:11000000-110001ff irq:11
  *-battery
       product: 0001J433
       vendor: SANYO
       physical id: 1
       slot: Left Module Bay
       capacity: 66000mWh
       configuration: voltage=14.8V
matthew@ubuntu:/$ sudo cardctl ident
Socket 0:
  product info: "D-Link", "DWL-650 Wireless PC Card RevP", "ISL37101P-10", "A3"
  manfid: 0x000b, 0x7110
  function: 6 (network)
Socket 1:
  product info: "CardBus PC Card", "Fast Ethernet CardBus PC Card"
  manfid: 0x0000, 0x021b
  function: 6 (network)
matthew@ubuntu:/$ cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
matthew@ubuntu:/$ sudo modinfo ndiswrapper
filename:       /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.1
license:        GPL
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:        usbcore
srcversion:     E21E28A177890611AE46391
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
matthew@ubuntu:/$ sudo slocate -u
matthew@ubuntu:/$ sudo slocate ndiswrapper
/etc/ndiswrapper
/etc/ndiswrapper/netprism
/etc/ndiswrapper/netprism/1260:3873:1186:3700.5.conf
/etc/ndiswrapper/netprism/prismnds.sys
/etc/ndiswrapper/netprism/prismusb.sys
/etc/ndiswrapper/netprism/2001:3700.0.conf
/etc/ndiswrapper/netprism/netprism.inf
/etc/ndiswrapper/netprism/1260:3873.0.conf
/var/lib/dpkg/info/ndiswrapper-utils.postinst
/var/lib/dpkg/info/ndiswrapper-utils.list
/var/lib/dpkg/info/ndiswrapper-utils.md5sums
/var/cache/apt/archives/ndiswrapper-utils_1.1-4ubuntu2_i386.deb
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/usr/share/doc/ndiswrapper-utils
/usr/share/doc/ndiswrapper-utils/README.Debian
/usr/share/doc/ndiswrapper-utils/README
/usr/share/doc/ndiswrapper-utils/AUTHORS
/usr/share/doc/ndiswrapper-utils/changelog.gz
/usr/share/doc/ndiswrapper-utils/copyright
/usr/share/doc/ndiswrapper-utils/changelog.Debian.gz
/usr/share/man/man8/ndiswrapper.8.gz
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-buginfo
matthew@ubuntu:/$

The power light on the DWL-650 rev P is on steady, but the transmit light does nothing.  I do have WEP on my router, but I thought it was still a h/w problem at this point.  In the network settings, only modem1 and ETH0 (my lan card) show up.  WLAN0 does not show up.  I also have this loopback connection (lo) which I don't really understand what that is.  

thanks in advance.  -Matt

---

