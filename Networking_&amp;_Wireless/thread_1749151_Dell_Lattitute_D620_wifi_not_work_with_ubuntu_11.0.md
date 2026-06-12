---
title: "Dell Lattitute D620 wifi not work with ubuntu 11.04"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by marcoslai on 2011-05-04
I just bought a used laptop - Dell Lattitute D620,installed 32bit Ubuntu 11.04 gnome,found my wifi is not working. 
'Additional Driver' show that restricted driver is activated & in use,but I switch my wifi hardware button to 'on',the light didn't on,and there's only 'Auto eth0' sho in network manager,NO wireless option.........
How to fix it?
Found a sticker at the bottom of laptop showing my wifi chip is Broadcom brcm94311mcg.
Output of lspci :

marcoslai@marcoslai-Latitude-D620:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by mlabowicz on 2011-05-04
+1, wifi doesn't work on my d620 either. Worked fine on 10.04 and 10.10. I guess I'll be downgrading...

---

### Post by josephmills on 2011-05-04
could we all see a 
```

sudo lshw | grep 14e4 

```
thanks

---

### Post by mlabowicz on 2011-05-05
PCI (sysfs) shows up for a few seconds and then I'm dropped back to the shell prompt. No other output...

---

### Post by marcoslai on 2011-05-05
> **josephmills said:**
> could we all see a 
```

sudo lshw | grep 14e4 

```
thanks

Hi fren,thanks for offering help,anyway,I've changed to Debian Squeeze amd64 last night,and did something follow a tutorial,my wifi work now.

---

### Post by mlabowicz on 2011-05-05
I'm still interested in helping to find a solution. Please let me know if you need any logs, etc from me.

---

### Post by josephmills on 2011-05-05
> **mlabowicz said:**
> I'm still interested in helping to find a solution. Please let me know if you need any logs, etc from me.

sorry about that my bad it was a typo try 
```
lspci -vnn | grep 14e4 
```
once again sorry

---

### Post by ZosoPage on 2011-05-07
having the same issue, the command above shows no output, but here is the whole shabang...


mychal-latitude-d620      
    description: Portable Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5100-1036-8050-B8C04F514231
  *-core
       description: Motherboard
       product: 0JK187
       vendor: Winbond Electronics
       physical id: 0
       serial: .8Q6PQB1.CN129616813716.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A10
          date: 05/16/2008
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2600  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Microprocessor
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: OCZ2MV6672G
             vendor: 7F7F7F7FB0000000
             physical id: 0
             serial: 00000000
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: OCZ2MV6672G
             vendor: 7F7F7F7FB0000000
             physical id: 1
             serial: 00000000
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:ed000000-efefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72M [Quadro NVS 110M/GeForce Go 7300]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff memory:ef000000-ef01ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:efffc000-efffffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:e0000000-e01fffff ioport:e0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:ecf00000-ecffffff ioport:e0400000(size=2097152)
           *-network UNCLAIMED
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:ecffc000-ecffffff
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:4000(size=4096) memory:ece00000-ecefffff ioport:e0600000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:45:76:8c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=half firmware=5752-v3.19 ip=192.168.1.185 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:45 memory:ecef0000-ecefffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:ffa80000-ffa803ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HM251JI
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2SS0
                serial: S19CJD0S262847
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000de14e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 63ee7707-200d-4679-90c0-ceddfb821e02
                   size: 229GiB
                   capacity: 229GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-05-01 15:46:03 filesystem=ext4 lastmountpoint=/ modified=2011-05-01 15:57:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2011-05-07 06:49:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3325MiB
                   capacity: 3325MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3325MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632D
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)
  *-battery
       product: DELL PD
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 66000mWh
       configuration: voltage=11.1V
mychal@mychal-Latitude-D620:~$ sudo lshw | grep l4e4
mychal@mychal-Latitude-D620:~$

---

### Post by mlabowicz on 2011-05-09
Here is the output on my laptop:

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by josephmills on 2011-05-09
```
lsmod | grep b43 
``` and ```
dmesg | grep b43  
```

---

### Post by mlabowicz on 2011-05-09
Nothing was returned for either of these commands...

---

### Post by nm_geo on 2011-05-09
> **mlabowicz said:**
> Nothing was returned for either of these commands...

Have you tired to install the STA driver? By the way I have the same 
laptop and two working versions of Natty 11.04 since Alpha testing. I was able to run the STA driver at first but now I use the b43 driver for my versions.  Here is my PCI-ID info.

lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

Please note the PCI-ID is more important than the BCM43xx number.

Here is a link that just might help you

 [http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)

Thread #5 is the main part I don't want to type it again   q:o)

---

### Post by divergex on 2011-09-24
Sorry for the late reply, but my Dell D620 wireless works great after installing these two packages:

b43-fwcutter
firmware-b43-installer

They can be installed from the Software Center or through the command line:

sudo apt-get install b43-fwcutter firmware-b43-installer

A reboot is not necessary - after the install is complete you should have working wifi and the wifi light should light up as well.

---

### Post by denied on 2011-09-25
Wow divergex, Great job on this one!! Worked perfectly! Now my mom can enjoy wireless internet =) Thanks a lot for this one!!

---

### Post by mörgæs on 2011-09-25
Thanks. 

Divergex, it would be nice if you could post this modification in 
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by Spaard on 2011-10-30
The Wifi in my Latitude D620 is not working with 11.10 worked before. I tried the sudo apt-get install b43-fwcutter firmware-b43-installer and still not working. Can any one assist?

---

### Post by razorxpress on 2011-12-02
I think Additional Hardware installs conflicting drivers. So you must install the correct one and uninstall the one that conflicts.

```
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot -n
```

After reboot if you have not disabled wireless switch (left side slider) and Enable Wireless from network icon, the green wifi icon should light up and start scanning wireless networks.

Thanks to [this post]("http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/")

Cheers!!

---

### Post by Neoxes on 2012-02-25
i tried everything i could find and still no luck with my Dell D620

---

### Post by chili555 on 2012-02-25
> **Neoxes said:**
> i tried everything i could find and still no luck with my Dell D620Let's start with basics. Please run and post:```
lsmod | grep -e b4 -e wl
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by Fodderuntu on 2012-03-12
> **razorxpress said:**
> I think Additional Hardware installs conflicting drivers. So you must install the correct one and uninstall the one that conflicts.

```
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot -n
```After reboot if you have not disabled wireless switch (left side slider) and Enable Wireless from network icon, the green wifi icon should light up and start scanning wireless networks.

Thanks to [this post]("http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/")

Cheers!!

This worked perfectly for me on ubuntu 12.04! Thank you! Must do all 3 steps

---

### Post by Ycc on 2012-11-10
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot -n

Worked for me! 
Thank you!

Edit, I forgot; 

sudo apt-get install b43-fwcutter

:)

---

