---
title: "Samsung N210 Wireless Driver RTL8192E will not compile on 11.10"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by jonnohudski on 2011-11-08
SOrry for reposting this, my first post went in with a prefix of LUBUNTU!


Hello again, REALTEK have sent me their recent Linux driver for their 8192E wireless network card.

I have been trying to compile it all day and have had no luck.

Firstly it was reporting that autoconf.h was missing, so i managed to  link it to what i assume is the correct location  (../generated/autoconf.h).

Secondly, it reported that modversions.h was missing. I couldn't find  any mention of this problem in google, apart from 1 mention that  suggested just touching it. So i did.

Now when I try to make the driver, i get the following

root@terri-N150-N210-N220:/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010# make
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in  "/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192/Makefile".  Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error 2

So, loking at the forums, chilli555 suggests trying 

KBUILD_NOPEDANTIC=1 make all

so did and got the following, which to me seems to be saying that it didn't build anything.

make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'

But, being an optimist, I tried 

KBUILD_NOPEDANTIC=1 make install

which gave the following errors.

make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Entering directory `/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192'
install -p -m 644 r8192e_pci.o  /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/
install: cannot stat `r8192e_pci.o': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/terri/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192'
make: *** [install] Error 2

Now, I am a noob, so, please dont castigate me for my naivity. But can someone help?

My original problem is that my wireless keeps dropping out, and even  when connected reports 1MB connection speed to my BT homehub 2 router.

Any help will be reallly appreciated.

---

### Post by jonnohudski on 2011-11-09
Has anyone got any ideas on this?
 
Everything else seems to work perfectly, but the wireless keeps dropping out and is slow when it does connect.

---

### Post by jonnohudski on 2011-11-09
it now appears that every other boot shows that the "Wireless Networks" "device not ready"
 
And it panics almost every other shutdown too.
 
I followed some instructions to disable ipv6 which has made no difference.
 
Desperately want this to work as my wife uses this netbook for work and i quite like my testicles where they are.

---

### Post by jonnohudski on 2011-11-09
after some kind help from papibe, I can now post the results to lshw

jonno@terri-N150-N210-N220:/home/terri$ sudo lshw
[sudo] password for jonno: 
terri-n150-n210-n220      
    description: Notebook
    version: Not Applicable
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=1 family=1234567890 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled sku=1234567890 uuid=40F4895E-DA1D-B211-8000-F807D2C8C675
  *-core
       description: Motherboard
       product: N150/N210/N220
       vendor: SAMSUNG ELECTRONICS CO., LTD.
       physical id: 0
       version: Not Applicable
       serial: 123490EN400015
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: 05JI.M039.20100109.JIP
          date: 01/09/2010
          size: 103KiB
          capacity: 1984KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int5printscreen int9keyboard int14serial int17printer int10video usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: CPU 1
          size: 1GHz
          capacity: 3300MHz
          width: 64 bits
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm cpufreq
          configuration: cores=1 enabledcores=1 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
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
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 012345678901234567890123456789012345
             vendor: 48spaces
             physical id: 0
             serial: 01234567
             slot: J6G1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f0300000-f037ffff ioport:18d0(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0380000-f03fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:f0400000-f0403fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f0100000-f01fffff ioport:80a00000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8192E/RTL8192SE Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:26:b6:9a:95:7e
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xE ip=192.168.1.69 latency=0 multicast=yes wireless=802.11bgn
                resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:5000(size=4096) memory:80600000-807fffff ioport:80800000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:f0200000-f02fffff ioport:80400000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 00
                serial: 00:24:54:44:7a:bc
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:f0200000-f0203fff ioport:3000(size=256)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:4000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0604000-f06043ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:18e8(size=8) ioport:18dc(size=4) ioport:18e0(size=8) ioport:18d8(size=4) ioport:18c0(size=16) memory:f0604400-f06047ff
           *-disk
                description: ATA Disk
                product: ST9250315AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0001
                serial: 6VC2KQBF
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9d97ba08
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 529bb3a8-71ed-9d47-a37d-41cb9d44d9a4
                   size: 14GiB
                   capacity: 15GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-12-10 18:03:43 filesystem=ntfs label=RECOVERY state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 561e-c623
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-12-10 18:03:47 filesystem=ntfs label=SYSTEM state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: e89492ff-cce5-0841-8e1a-00a37fcdabb7
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-12-10 18:03:48 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 52GiB
                 *-logicalvolume:1
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4490MiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 50GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 2036MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

---

### Post by praseodym on 2011-11-09
Did you ever try the PPA from [Voria]("https://launchpad.net/~voria/+archive/ppa?field.series_filter=oneiric"), there are Oneiric-Packages now:

```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update
sudo apt-get install samsung-wireless samsung-tools
```
and reboot.

---

### Post by jonnohudski on 2011-11-09
well, that seemed incredibly easy. Rebooting now, so I'll post my experiences a little later.
 
Thanks praseodym.

---

### Post by jonnohudski on 2011-11-09
okay, i've rebooted and wireless came straight up, but still have a reported network speed of 1mb. Any ideas how to increase this?

---

### Post by jonnohudski on 2011-11-09
Oh, and now I don't get any internet access (I am foruming from my other laptop!). Which makes me thing that I am not actually connected to WIFI, although it is reporting it.
 
 
HELP!!!!

---

### Post by praseodym on 2011-11-09
Please show:

```
lsmod
rfkill list
iwconfig
dmesg | egrep 'rtl8|r8'
sudo iwlist scan
```
You can c/p the outputs to a textfile and upload it.

---

### Post by jonnohudski on 2011-11-10
Will do as soon as I get home tonight. Thanks.

---

