---
title: "Problems installing VLC"
date: 2017-01-25
forum: Multimedia Software
---

### Post by lacastelos on 2017-01-25
Good morning everyone

I use Kubuntu 14.04, the 16.04 for some reason did not have good compatibility with my notebook. Earlier  today I requested an update, upgrade and dist-upgrade on my system and  to my surprise it uninstalled the VLC after the dist-upgrade. When trying to reinstall the VLC happens the following:

```
Root @ luiz-Inspiron-N4050: / home / luiz # apt-get install -f vlc
Reading package lists ... Ready
Building dependency tree
Reading status information ... Ready
Some packages could not be installed. This can mean
You have requested an impossible situation or you are using a
Unstable distribution, that some required packages were not
Created yet or removed from "Incoming".
Information can help solve a situation:

The following packages have mismatched dependencies:
Vlc: Depends: vlc-bin (= 2.2.4-13 ~ 14.04.york0) but not installed
Depends on: vlc-plugin-base (= 2.2.4-13 ~ 14.04.york0) but not installed
Depends on: vlc-plugin-qt (= 2.2.4-13 ~ 14.04.york0) but not installed
Depends on: vlc-plugin-video output (= 2.2.4-13 ~ 14.04.york0) but not installed
Pre-Depends: dpkg (> = 1.17.14)
Recommended: vlc-plugin-notify (= 2.2.4-13 ~ 14.04.york0) but not installed
Recommended: vlc-plugin-samba (= 2.2.4-13 ~ 14.04.york0) but not installed
Recommended: vlc-plugin-skins2 (= 2.2.4-13 ~ 14.04.york0) but not installed
Recommended: vlc-plugin-video-splitter (= 2.2.4-13 ~ 14.04.york0) but not installed
Recommended: vlc-plugin-visualization (= 2.2.4-13 ~ 14.04.york0) but is not installed
E: Impossible to fix problems, you kept (hold) broken packages.
Root @ luiz-Inspiron-N4050: / home / luiz # dpkg --config -a
Root @ luiz-Inspiron-N4050: / home / luiz # install apt-get -f
Reading package lists ... Ready
Building dependency tree
Reading status information ... Ready
0 packages upgraded, 0 new packages installed, 0 to be removed and 0 not upgraded.
Root @ luiz-Inspiron-N4050: / home / luiz #
```

In case the computer is a Dell Inpirion 14 N-4050 / Intel (R) Core  (TM) i3-2350M CPU @ 2.30GHz / 1.8 TiB SATA / Total Physical Memory: 4GB

Can anyone suggest me something to go back with VLC to Kubuntu?

Note: Also does not install by the software center.

Thank you very much and sorry for my bad English.

---

### Post by mörgæs on 2017-01-25
Hi, welcome to the fora.

In stead of going back to old releases it's better to get the new release (16.04.1) running. If you run ```
sudo lshw -sanitize > lshw.txt
``` and post the output in CODE tags people can probably help with that.

---

### Post by lacastelos on 2017-01-25
> **mörgæs said:**
> Hi, welcome to the fora.

In stead of going back to old releases it's better to get the new release (16.04.1) running. If you run ```
sudo lshw -sanitize > lshw.txt
``` and post the output in CODE tags people can probably help with that.

Thank you very much. They follow the information requested.

```
Computer
    Description: Laptop computer
    Product: Inspiron N4050 (To be filled by O.E.M.)
    Manufacturer: Dell Inc.
    Version: Not Specified
    Serial: [REMOVED]
    Width: 64-bit
    Capabilities: smbios-2.6 dmi-2.6 vsyscall32
    Configuration: boot = normal chassis = portable sku = To be filled by O.E.M. Uuid = [REMOVED]
  * -core
       Description: Motherboard
       Product: 0X0DC1
       Manufacturer: Dell Inc.
       Physical ID: 0
       Version: A06
       Serial: [REMOVED]
       Slot: To Be Filled By O.E.M.
     * -cpu
          Description: CPU
          Product: Intel (R) Core (TM) i3-2350M CPU @ 2.30GHz
          Manufacturer: Intel Corp.
          Physical ID: 4
          Bus info: cpu @ 0
          Version: Intel (R) Core (TM) i3-2350M CPU @ 2.30GHz
          Serial: [REMOVED]
          Slot: CPU 1
          Size: 901MHz
          Capacity: 2300MHz
          Width: 64-bit
          Clock: 100MHz
          Capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq Dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt cpufreq
          Configuration: cores = 2 enabledcores = 1 threads = 2
* -cache: 0
             Description: L1 cache
             Physical ID: 5
             Slot: L1-Cache
             Size: 64KiB
             Capacity: 64KiB
             Capabilities: internal write-back unified
        * -cache: 1
             Description: L2 cache
             Physical ID: 6
             Slot: L2-Cache
             Size: 512KiB
             Capacity: 512KiB
             Capacities: internal varies unified
        * -cache: 2
             Description: L3 cache
             Physical ID: 7
             Slot: L3-Cache
             Size: 3MiB
             Capacity: 3MiB
             Capacities: internal varies unified
     * -memory
          Description: System Memory
          Physical ID: 14
          Slot: System board or motherboard
          Size: 4GiB
        * -bank: 0
             Description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <POT-Creation-Date: 2009-10-08 14:02 + 0200PO-Revision-Date: 2013-04-07 17 : 30 + 0000Last-Translator: Neliton Pereira Jr. <nelitonpjr@gmail.com> Language-Team: Brazilian Portuguese <pt_BR@li.org> MIME-Version: 1.0Content-Type: text / plain; Charset = UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-07-20 12: 06 + 0000X-Generator: Launchpad (build 18147) [empty]
             Product: Not Specified
             Manufacturer: Not Specified
             Physical ID: 0
             Serial: [REMOVED]
             Slot: DIMM_A
        * -bank: 1
             Description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             Product: SH564128FH8NZPHSCG
             Manufacturer: AMD
             Physical ID: 1
             Serial: [REMOVED]
             Slot: DIMM_B
             Size: 4GiB
             Width: 64-bit
             Clock: 1333MHz (0.8ns)
     * -firmware
          Description: BIOS
          Manufacturer: Dell Inc.
          Physical ID: 0
          Version: A06
          Date: 11/14/2011
          Size: 64KiB
          Capacity: 1984KiB
          Capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     * -pci
          Description: Host bridge
          Product: 2nd Generation Core Processor Family DRAM Controller
          Manufacturer: Intel Corporation
          Physical ID: 100
          Bus info: pci @ 0000: 00: 00.0
          Release Date: 09
          Width: 32 bits
          Clock: 33MHz
        *-display
             Description: VGA compatible controller
             Product: 2nd Generation Core Processor Family Integrated Graphics Controller
             Manufacturer: Intel Corporation
             Physical ID: 2
             Bus Information: pci @ 0000: 00: 02.0
             Release Date: 09
             Width: 64-bit
             Clock: 33MHz
             Capabilities: msi pm vga_controller bus_master cap_list rom
             Configuration: driver = i915 latency = 0
             Features: irq: 27 memory: f6800000-f6bfffff memory: e0000000-efffffff I / O port: f000 (size = 64)
* -communication
             Description: Communication controller
             Product: 6 Series / C200 Series Family MEI Controller Chipset # 1
             Manufacturer: Intel Corporation
             Physical ID: 16
             Bus info: pci @ 0000: 00: 16.0
             Version: 04
             Width: 64-bit
             Clock: 33MHz
             Capabilities: pm msi bus_master cap_list
             Configuration: driver = mei_me latency = 0
             Resources: irq: 28 memory: f7e0a000-f7e0a00f
        * -usb: 0
             Description: USB controller
             Product: 6 Series / C200 Series Family USB Enhanced Host Controller # 2 Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1a
             Bus Information: pci @ 0000: 00: 1a.0
             Version: 05
             Width: 32 bits
             Clock: 33MHz
             Capabilities: pm debug ehci bus_master cap_list
             Configuration: driver = ehci-pci latency = 0
             Features: irq: 16 memory: f7e08000-f7e083ff
        * -Multimedia
             Description: Audio device
             Product: 6 Series / C200 Series Family High Definition Audio Controller Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1b
             Bus info: pci @ 0000: 00: 1b.0
             Version: 05
             Width: 64-bit
             Clock: 33MHz
             Capacities: pm msi pciexpress bus_master cap_list
             Configuration: driver = snd_hda_intel latency = 0
             Resources: irq: 29 memory: f7e00000-f7e03fff
        * -pci: 0
             Description: PCI bridge
             Product: 6 Series / C200 Series Family PCI Express Root Port 1 Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1c
             Bus Information: pci @ 0000: 00: 1c.0
             Version: b5
             Width: 32 bits
             Clock: 33MHz
             Capacities: pciexpress msi pm normal_decode bus_master cap_list
             Configuration: driver = pcieport
             Resources: irq: 16
        * -pci: 1
             Description: PCI bridge
             Product: 6 Series / C200 Series Chipset Family PCI Express Root Port 2
             Manufacturer: Intel Corporation
             Physical ID: 1c.1
             Bus info: pci @ 0000: 00: 1c.1
             Version: b5
             Width: 32 bits
             Clock: 33MHz
             Capacities: pciexpress msi pm normal_decode bus_master cap_list
             Configuration: driver = pcieport
             Features: irq: 17 I / O port: e000 (size = 4096) I / O port: f1100000 (size = 1048576)
           * -network
                Description: Ethernet interface
                Product: RTL8101 / 2 / 6E PCI Express Fast / Gigabit Ethernet controller
                Manufacturer: Realtek Semiconductor Co., Ltd.
                Physical ID: 0
                Bus info: pci @ 0000: 05: 00.0
                Logical name: eth0
                Version: 05
                Serial: [REMOVED]
                Size: 10Mbit / s
                Capacity: 100Mbit / s
                Width: 64-bit
                Clock: 33MHz
                Capacities: msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                Configuration: autonegotiation = on broadcast = yes driver = r8169 driverversion = 2.3LK-NAPI duplex = half firmware = rtl_nic / rtl8105e-1.fw latency = 0 link = no multicast = yes port = MII speed = 10Mbit / s
                Features: irq: 25 I / O port: e000 (size = 256) memory: f1104000-f1104fff memory: f1100000-f1103fff
        * -pci: 2
             Description: PCI bridge
             Product: 6 Series / C200 Series Family PCI Express Root Port 4 Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1c.3
             Bus info: pci @ 0000: 00: 1c.3
             Version: b5
             Width: 32 bits
             Clock: 33MHz
             Capacities: pciexpress msi pm normal_decode bus_master cap_list
             Configuration: driver = pcieport
             Resources: irq: 19 memory: f7d00000-f7dfffff
           * -network
                Description: Wireless Interface
                Product: AR9285 Wireless Network Adapter (PCI-Express)
                Manufacturer: Qualcomm Atheros
                Physical ID: 0
                Bus info: pci @ 0000: 09: 00.0
                Logical name: wlan0
                Version: 01
                Serial: [REMOVED]
                Width: 64-bit
                Clock: 33MHz
                Capacities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                Configuration: broadcast = yes driver = ath9k driverversion = 4.2.0-42-generic firmware = N / A ip = [REMOVED] latency = 0 link = yes multicast = yes wireless = IEEE 802.11bgn
                Resources: irq: 19 memory: f7d00000-f7d0ffff
* -pci: 3
             Description: PCI bridge
             Product: 6 Series / C200 Series Family PCI Express Root Port 8 Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1c.7
             Bus info: pci @ 0000: 00: 1c.7
             Version: b5
             Width: 32 bits
             Clock: 33MHz
             Capacities: pciexpress msi pm normal_decode bus_master cap_list
             Configuration: driver = pcieport
             Features: irq: 24 I / O port: c000 (size = 8192) memory: f6c00000-f7cfffff I / O port: f0000000 (size = 17825792)
        * -usb: 1
             Description: USB controller
             Product: 6 Series / C200 Series Family USB Enhanced Host Controller # 1 Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1d
             Bus info: pci @ 0000: 00: 1d.0
             Version: 05
             Width: 32 bits
             Clock: 33MHz
             Capabilities: pm debug ehci bus_master cap_list
             Configuration: driver = ehci-pci latency = 0
             Features: irq: 23 memory: f7e07000-f7e073ff
        * -isa
             Description: ISA bridge
             Product: HM67 Express Chipset Family LPC Controller
             Manufacturer: Intel Corporation
             Physical ID: 1f
             Bus Information: pci @ 0000: 00: 1f.0
             Version: 05
             Width: 32 bits
             Clock: 33MHz
             Capabilities: isa bus_master cap_list
             Configuration: driver = lpc_ich latency = 0
             Resources: irq: 0
        * -storage
             Description: SATA controller
             Product: 6 Series / C200 Series Chipset Family 6 port SATA AHCI Controller
             Manufacturer: Intel Corporation
             Physical ID: 1f.2
             Bus info: pci @ 0000: 00: 1f.2
             Version: 05
             Width: 32 bits
             Clock: 66MHz
             Capacities: storage msi pm ahci_1.0 bus_master cap_list
             Configuration: driver = ahci latency = 0
             I / O port: f080 (size = 8) I / O port: f080 (size = 8) I / O port: f090 = 4) I / O port: f060 (size = 32) memory: f7e06000-f7e067ff
        * -serial AVAILABLE
             Description: SMBus
             Product: 6 Series / C200 Series Family SMBus Controller Chipset
             Manufacturer: Intel Corporation
             Physical ID: 1f.3
             Bus info: pci @ 0000: 00: 1f.3
             Version: 05
             Width: 64-bit
             Clock: 33MHz
             Configuration: latency = 0
             Features: memory: f7e05000-f7e050ff I / O port: f040 (size = 32)
     * -scsi: 0
          Physical ID: 1
          Logical name: scsi0
          Capacities: emulated
        * -disk
             Description: ATA Disk
             Product: ST2000LM007-1R81
             Manufacturer: Seagate
             Physical ID: 0.0.0
             Bus info: scsi @ 0: 0.0.0
             Logical name: / dev / sda
             Version: SBK2
             Serial: [REMOVED]
             Size: 1863GiB (2TB)
             Capacities: partitioned partitioned: two
             Setting: ansiversion = 5 sectorsize = 4096 signature = 9ca102d9
* -volume: 0
                Description: EXT4 volume
                Manufacturer: Linux
                Physical ID: 1
                Bus info: scsi @ 0: 0.0.0,1
                Logical name: / dev / sda1
                Logical name: /
                Version: 1.0
                Serial: [REMOVED]
                Size: 136GiB
                Capacity: 136GiB
                Capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                Configuration: created = 2016-12-18 16:16:12 filesystem = ext4 lastmountpoint = / modified = 2017-01-24 16:49:08 mount.fstype = ext4 mount.options = rw, relatime, errors = remount-ro , Data = ordered mounted = 2017-01-24 16:49:08 state = mounted
           *-volume 1
                Description: EXT4 volume
                Manufacturer: Linux
                Physical ID: 2
                Bus info: scsi @ 0: 0.0.0,2
                Logical name: / dev / sda2
                Version: 1.0
                Serial: [REMOVED]
                Size: 136GiB
                Capacity: 136GiB
                Capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                Configuration: created = 2016-12-18 17:30:17 filesystem = ext4 lastmountpoint = / modified = 2017-01-18 08:15:51 mounted = 2017-01-18 08:15:54 state = clean
           * -volume: 2
                Description: EXT4 volume
                Manufacturer: Linux
                Physical ID: 3
                Bus info: scsi @ 0: 0.0.0,3
                Logical name: / dev / sda3
                Logical name: / home
                Version: 1.0
                Serial: [REMOVED]
                Size: 1582GiB
                Capacity: 1582GiB
                Capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                Configuration: created = 2016-12-18 16:16:15 filesystem = ext4 lastmountpoint = / home modified = 2017-01-25 09:10:24 mount.fstype = ext4 mount.options = rw, relatime, data = ordered mounted = 2017-01-25 09:10:24 state = mounted
           * -volume: 3
                Extended partition
                Physical ID: 4
                Bus info: scsi @ 0: 0.0.0,4
                Logical name: / dev / sda4
                Size: 7772MiB
                Capacity: 7772MiB
                Capabilities: primary extended partitioned partitioned: extended
              * -logicalvolume
                   Description: Linux swap / Solaris partition
                   Physical ID: 5
                   Logical name: / dev / sda5
                   Capacity: 7772MiB
                   Capabilities: nofs
     * -scsi: 1
          Physical ID: 2
          Logical name: scsi4
          Capacities: emulated
        * -cdrom
             Description: DVD-RAM writer
             Product: DVD + -RW SN-208BB
             Manufacturer: TSSTcorp
             Physical ID: 0.0.0
             Bus info: scsi @ 4: 0.0.0
             Logical name: / dev / cdrom
             Logical name: / dev / sr0
             Version: D300
             Capacities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             Configuration: ansiversion = 5 status = nodisc
  * -battery
       Description: Lithium Ion Battery
       Product: DELL 7XFJJ05
       Manufacturer: Samsung PP
       Physical ID: 1
       Serial: [REMOVED]
       Slot: Sys. Battery Bay
       Capacity: 48840mWh
       Setting: voltage = 11.1V
```

---

### Post by SeijiSensei on 2017-01-25
Were you previously installing VLC from a PPA repository or the main Ubuntu one?

Are you now running a new 14.04 installation from scratch, or did you try to downgrade from 16.04 somehow.  That's unlikely to turn out well.  If you're on a brand-new installation, I'd add Doug McMahon's PPA for 14.04: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) and use that for things like VLC.  I prefer SMPlayer with the mpv engine myself; they are in Doug's repo as well and are more up-to-date.

I'm quite happy remaining on Kubuntu 14.04 at least until the next LTS release in 2018.  I've run 16.04 in virtual machines for testing but don't see much that compels me to switch.

---

### Post by howefield on 2017-01-25
Probably a consequence of using PPAs to get a more up to date version of VLC than was available via the repositories ?

I'd suggest putting the software lists back to default by using ppa-purge.

Can you list the repositories that you are using, this command will do it..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by lacastelos on 2017-01-25
> **SeijiSensei said:**
> Were you previously installing VLC from a PPA repository or the main Ubuntu one?

Are you now running a new 14.04 installation from scratch, or did you try to downgrade from 16.04 somehow.  That's unlikely to turn out well.  If you're on a brand-new installation, I'd add Doug McMahon's PPA for 14.04: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) and use that for things like VLC.  I prefer SMPlayer with the mpv engine myself; they are in Doug's repo as well and are more up-to-date.

I'm quite happy remaining on Kubuntu 14.04 at least until the next LTS release in 2018.  I've run 16.04 in virtual machines for testing but don't see much that compels me to switch.

Hello. First of all thank you.

1) When I installed VLC I previously did via the command line "apt-get install vlc"

2) When I installed Kubuntu 14.04 I made zero. After that only update, upgrade and dist-upgrade (which until the latter has updated without any problem).

3) I'll take a look at DougMacMahon PPA.

3) As for Kubuntu 16.04, on my computer it presented serious problems (locking a lot, keeping the HD 100% busy all the time).

4) I'll try out SMPlayer for sure.

I tried to install the dependencies one by one but I had problem requesting dpkg (> = 1.17.14) I currently have version 1.17.5 (amd64). Would it be possible to install a more current version in 14.04? How can I do this? Maybe with a newer version of dpkg I can install all the required dependencies.

Again, thank you very much and sorry for my bad English.

---

### Post by lacastelos on 2017-01-25
> **howefield said:**
> Probably a consequence of using PPAs to get a more up to date version of VLC than was available via the repositories ?

I'd suggest putting the software lists back to default by using ppa-purge.

Can you list the repositories that you are using, this command will do it..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Hello.

The repositories are:

root@luiz-Inspiron-N4050:/home/luiz# egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*


```
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty main restricted
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty main restricted
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty universe
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty universe
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-updates universe
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-updates universe
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty multiverse
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty multiverse
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-updates multiverse
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-updates multiverse
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-security main restricted
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-security main restricted
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-security universe
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-security universe
/etc/apt/sources.list:deb [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-security multiverse
/etc/apt/sources.list:deb-src [http://ubuntu-archive.locaweb.com.br/ubuntu/](http://ubuntu-archive.locaweb.com.br/ubuntu/) trusty-security multiverse
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
/etc/apt/sources.list.d/cairo-dock-team-ppa-trusty.list:deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/cairo-dock-team-ppa-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/cairo-dock-team-ppa-trusty.list.save:deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/dhor-myway-trusty.list:deb [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu) trusty main
/etc/apt/sources.list.d/dhor-myway-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu) trusty main
/etc/apt/sources.list.d/dhor-myway-trusty.list.save:deb [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu) trusty main
/etc/apt/sources.list.d/ehbello-fritzing-trusty.list:deb [http://ppa.launchpad.net/ehbello/fritzing/ubuntu](http://ppa.launchpad.net/ehbello/fritzing/ubuntu) trusty main
/etc/apt/sources.list.d/ehbello-fritzing-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/ehbello/fritzing/ubuntu](http://ppa.launchpad.net/ehbello/fritzing/ubuntu) trusty main
/etc/apt/sources.list.d/ehbello-fritzing-trusty.list.save:deb [http://ppa.launchpad.net/ehbello/fritzing/ubuntu](http://ppa.launchpad.net/ehbello/fritzing/ubuntu) trusty main
/etc/apt/sources.list.d/inkscape_dev-stable-trusty.list:deb [http://ppa.launchpad.net/inkscape.dev/stable/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable/ubuntu) trusty main
/etc/apt/sources.list.d/inkscape_dev-stable-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/inkscape.dev/stable/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable/ubuntu) trusty main
/etc/apt/sources.list.d/inkscape_dev-stable-trusty.list.save:deb [http://ppa.launchpad.net/inkscape.dev/stable/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable/ubuntu) trusty main
/etc/apt/sources.list.d/jonathonf-vlc-trusty.list:deb [http://ppa.launchpad.net/jonathonf/vlc/ubuntu](http://ppa.launchpad.net/jonathonf/vlc/ubuntu) trusty main
/etc/apt/sources.list.d/jonathonf-vlc-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/jonathonf/vlc/ubuntu](http://ppa.launchpad.net/jonathonf/vlc/ubuntu) trusty main
/etc/apt/sources.list.d/jonathonf-vlc-trusty.list.save:deb [http://ppa.launchpad.net/jonathonf/vlc/ubuntu](http://ppa.launchpad.net/jonathonf/vlc/ubuntu) trusty main
/etc/apt/sources.list.d/librecad-dev-librecad-daily-trusty.list:deb [http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu](http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu) trusty main
/etc/apt/sources.list.d/librecad-dev-librecad-daily-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu](http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu) trusty main
/etc/apt/sources.list.d/librecad-dev-librecad-daily-trusty.list.save:deb [http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu](http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu) trusty main
/etc/apt/sources.list.d/mc3man-trusty-media-trusty.list:deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
/etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.save:deb [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
/etc/apt/sources.list.d/n-muench-programs-ppa-trusty.list:deb [http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu](http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu) trusty main
/etc/apt/sources.list.d/n-muench-programs-ppa-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu](http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu) trusty main
/etc/apt/sources.list.d/n-muench-programs-ppa-trusty.list.save:deb [http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu](http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu) trusty main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list:deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list.save:deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main
/etc/apt/sources.list.d/philip5-extra-trusty.list:deb [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) trusty main
/etc/apt/sources.list.d/philip5-extra-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) trusty main
/etc/apt/sources.list.d/philip5-extra-trusty.list.save:deb [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) trusty main
/etc/apt/sources.list.d/pmjdebruijn-darktable-release-trusty.list:deb [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) trusty main
/etc/apt/sources.list.d/pmjdebruijn-darktable-release-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) trusty main
/etc/apt/sources.list.d/pmjdebruijn-darktable-release-trusty.list.save:deb [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) trusty main
/etc/apt/sources.list.d/transmissionbt-ppa-trusty.list:deb [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/transmissionbt-ppa-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/transmissionbt-ppa-trusty.list.save:deb [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/videolan-stable-daily-trusty.list:deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) trusty main
/etc/apt/sources.list.d/videolan-stable-daily-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) trusty main
/etc/apt/sources.list.d/videolan-stable-daily-trusty.list.save:deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.save:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
```

---

### Post by lacastelos on 2017-01-25
> **SeijiSensei said:**
> Were you previously installing VLC from a PPA repository or the main Ubuntu one?

Are you now running a new 14.04 installation from scratch, or did you try to downgrade from 16.04 somehow.  That's unlikely to turn out well.  If you're on a brand-new installation, I'd add Doug McMahon's PPA for 14.04: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) and use that for things like VLC.  I prefer SMPlayer with the mpv engine myself; they are in Doug's repo as well and are more up-to-date.

I'm quite happy remaining on Kubuntu 14.04 at least until the next LTS release in 2018.  I've run 16.04 in virtual machines for testing but don't see much that compels me to switch.

Hello again.

Add the repository mentioned. The problem with VLC remains the same. Get install SMPlayer and I'll test it. I will continue to look for a solution to the VLC, after all and always learning something more.

If you have any other tips, welcome. Grateful.

---

### Post by mc4man on 2017-01-25
That york ppa had mis-packaged x265, after being informed of such seems it was redone. But there also seems to be issues with other packages in it, maybe libcairo. I'd get rid of it, it's a potential mess.
To do that install ppa-purge (sudo apt-get install ppa-purge

Then, 
```
sudo ppa-purge ppa:jonathonf/vlc
```

---

### Post by lacastelos on 2017-01-25
> **mc4man said:**
> That york ppa had mis-packaged x265, after being informed of such seems it was redone. But there also seems to be issues with other packages in it, maybe libcairo. I'd get rid of it, it's a potential mess.
To do that install ppa-purge (sudo apt-get install ppa-purge

Then, 
```
sudo ppa-purge ppa:jonathonf/vlc
```

Thank you very much.

It worked perfectly for me.

The VLC has been re-installed and is in operation with your tip. Thank you very much for giving up your time by helping me.

---

### Post by lacastelos on 2017-01-25
Just one more question. How do I mark this post as resolved?

---

### Post by mc4man on 2017-01-25
> **lacastelos said:**
> Just one more question. How do I mark this post as resolved?
At the very top of your thread you should see "Thread Tools " dropdown. In it will be an option to mark as solved.

(- I've a companion ppa to Ubuntu multimedia, if inclined have a _careful read thru_ here - 
[https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6)

it's getting some updates now & in near future, the vlc would be the 2.2.4 that adds vdpau support thru libav11 if that matters.. new vlc will be ready within 15 min. or so

---

### Post by lacastelos on 2017-01-25
> **mc4man said:**
> At the very top of your thread you should see "Thread Tools " dropdown. In it will be an option to mark as solved.

(- I've a companion ppa to Ubuntu multimedia, if inclined have a _careful read thru_ here - 
[https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6)

it's getting some updates now & in near future, the vlc would be the 2.2.4 that adds vdpau support thru libav11 if that matters.. new vlc will be ready within 15 min. or so

Thanks so much.

---

