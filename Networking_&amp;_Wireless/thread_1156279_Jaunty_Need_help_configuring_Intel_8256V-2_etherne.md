---
title: "Jaunty: Need help configuring Intel 8256V-2 ethernet card!"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by slick601 on 2009-05-11
I have the below ethernet card, and am unable to connect to my wired network in Ubuntu Jaunty.  The interface will try to connect, and then will timeout.  When I set the IP manually, n-m says it is connected but I cannot ping any other hosts in the network. I tried using wicd as well, which had no more success than n-m.  Finally, the ethernet cable works with my eeePC 901 using Jaunty, connects using DHCP and works just fine.  

The hardware is a Dell Inspiron 530 which I am going to use as a media server. 

root@media-PC:~# lspci | grep net
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)

It is using the e1000e module by default. 

From what I have found on various forums, it appears that the correct module for that hardware is the e1000.  However, when I compile that driver and install it to the kernel using modprobe, then rmmod the e1000e driver, and reload gdm, the module doesn't apply itself to the ethernet hardware.  

I then blacklisted e1000e in /etc/modprobe.d/blacklist.conf and restarted.  

When the system comes back up, e1000e is back on the system when I use lsmod | grep 'e10', and e1000 is gone.  None of my changes take effect.  

So, there are a couple problems:

1. e1000e will not blacklist
2. e1000 replacement module will not take control of the ethernet device.

Anyone have any ideas regarding this problem?  I could really use the help, I keep running in circles.  


Thank you a lot!

Mike


Here is the full hardware spec:

media-pc
    description: Desktop Computer
    product: Inspiron 530
    vendor: Dell Inc.
    version: OEM
    serial: HHVFLG1
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=44454C4C-4800-1056-8046-C8C04F4C4731
  *-core
       description: Motherboard
       product: 0RY007
       vendor: Dell Inc.
       physical id: 0
       version: A01
       serial: ..CN7360491M00YT.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.0.16 (12/12/2008)
          size: 128KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU          450  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          slot: Socket 775
          size: 2200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: M3 78T2863EHS-CF7
             vendor: CE00000000000000
             physical id: 0
             serial: 80790510
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: V916764K24QCFW-G6
             vendor: 4000000000000000
             physical id: 1
             serial: 72E51A69
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: M3 78T2863EHS-CF7
             vendor: CE00000000000000
             physical id: 2
             serial: 80790696
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: V916764K24QCFW-G6
             vendor: 4000000000000000
             physical id: 3
             serial: 70E51A69
             slot: DIMM4
             size: 512MiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:21:9b:2b:00:c7
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST3250310AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 4.AD
                serial: 6RYK0ED7
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9aee0d57
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /home
                   version: 1.0
                   serial: 86e8b984-7b49-446f-b1aa-3859eaccb975
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-05-10 17:05:29 filesystem=ext4 modified=2009-05-11 11:51:28 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2009-05-11 11:09:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 956MiB
                   capacity: 956MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 956MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 7c04dc89-029f-4a8a-a21b-4b39c9728b99
                   size: 203GiB
                   capacity: 203GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-05-10 17:05:36 filesystem=ext4 modified=2009-05-11 11:51:58 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-05-11 11:51:58 state=mounted
           *-cdrom
                description: DVD reader
                product: DVD-ROM TS-H353B
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D700
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-H653F
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: D200
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:70:ce:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.69.22 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:0d:a4:17:78:65
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by chili555 on 2009-05-12
First of all, I notice your wireless has an IP address:> description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:0f:b5:70:ce:97
capabilities: ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]ip=192.168.69.22[/COLOR]Network Manager, which is installed by default, will not allow both a wired and wireless connection. Please turn off the wireless before you try the wired.```
sudo dhclient -r wlan0
sudo ifdown wlan0
```Next, I'd like to see if the e1000 module works any better than e1000e:```
sudo ifconfig eth0 down
sudo rmmod -f e1000e
sudo modprobe e1000
sudo ifconfig eth0 up
```Now can you reliably connect?> n-m says it is connected If this is a media server, you do not need NM and I suggest you remove it and configure */etc/network/interfaces* to connect by ethernet with a static IP automatically on boot.

---

### Post by slick601 on 2009-05-12
I physically removed the wireless USB adapter, good call on two connections.

Then, I used rmmod -f as you suggested, and that appeared to work just fine.   ifconfig eth0 ifdown worked fined, as did modprobe.  However, running ifup produced an error, 

eth0: ERROR while getting interface flags: no such device.

lshw lists the network device as UNCLAIMED.

an output of lsmod | grep e10 shows:

"e1000     156356  0"

It appears that the module is not picking up and binding to the hardware device.  


PS I will uninstall nm after we get everything working, for the moment it is easier for me to leave nm on.

---

### Post by chili555 on 2009-05-12
> It appears that the module is not picking up and binding to the hardware device..ko-rrect! A little linux joke there, please forgive me.

I try to be the first to admit what I don't know. I don't know, nor have I been successful researching, what the mechanism is that binds a specific device to a specific driver. I have one last thing to try. Please:```
sudo gedit /etc/modprobe.d/e1000.conf
```This will be a new file. Add a single line:```
alias eth0 e1000
```Proofread, save and close gedit. Now let's be sure *e1000e* never loads.```
sudo mv /lib/modules/2.6.28-11-generic/kernel/drivers/net/e1000e/e1000e.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/e1000e/e1000e.ko.ignore
```Substitute your location, if it's not *2.6.28-11-generic*. Now I am quite sure e1000e is dead to us, but we won't know if e1000 binds until you reboot and see if you can connect.

---

### Post by slick601 on 2009-05-12
Unfortunately, there has been little success.  

Running lsmod | grep e10 produces only the e1000 driver, which is good.

However, lshw tells a not-so-happy story.  It still lists the network device as UNCLAIMED, which means we have the same issue as before.  

I can only conclude that either the e1000 driver is not the correct one for this device, or that there is some kind of hiccough with the binding between module and device.  

Do you have any other suggestions?  I have tried reinstalling Jauny with a newly-burned disc, the source file of which I checked against the posted hash.  

:confused:

---

### Post by slashmax on 2009-06-24
Hmm... I'm having this same issue. Any luck?

-Max

---

### Post by satbunny on 2009-11-25
Same problem here, I have changed to a WiFi device to just keep going.

---

