---
title: "Unable to Connect to Wireless Networks - Atheros AR928X"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by Anghrist on 2013-03-06
I'm having real trouble with my laptop (Toshiba Satellite Pro P300-1FP) connecting to wireless networks since installing Ubuntu 12.10. I can view networks but can't connect to any - I enter the security key and it takes an age to process before telling me that it hasn't worked. This is with Ubuntu's default network manager and Wicd.

I've tried everything I can think of (admitedly not a great deal, I'm still very inexperienced with Ubuntu) and have trawled these forums for several days trying every possible solution in every thread I could find that even closely resembled my problem. I'm very keen to get the wireless working on this laptop - I really don't want to have to go back to Windows ...

I'm not sure what information will be needed to correct this problem, but here's what I have just now:

Wireless Adaptor: Atheros AR928X

```
sudo lshw
```

```
    description: Notebook
    product: Satellite Pro P300 ()
    vendor: TOSHIBA
    version: PSPC9E-005005EN
    serial: 29078575W
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=00F4C130-0E93-E411-8BED-00238B792595
  *-core
       description: Motherboard
       product: Satellite Pro P300
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: 29078575W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.50
          date: 11/28/2008
          size: 109KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 2166MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 4MiB
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
          physical id: c
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f8000000-f83fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8400000-f84fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f8904000-f89043ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f8700000-f8703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:c0000000-c02fffff ioport:c0300000(size=2097152)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:2b:63:29:18
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.5.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:c0000000-c000ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:c0500000-c07fffff ioport:c0800000(size=3145728)
           *-network
                description: Ethernet interface
                product: 88E8072 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 16
                serial: 00:23:8b:79:25:95
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=10.10.0.90 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:43 memory:c0500000-c0503fff ioport:3000(size=256) memory:c0800000-c081ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:c0b00000-c0cfffff ioport:c0d00000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8904400-f89047ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f8600000-f86fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:0a:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32
                resources: irq:16 memory:f8600000-f8600fff memory:f8602000-f86027ff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.2
                bus info: pci@0000:0a:01.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:16 memory:f8602800-f86028ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.3
                bus info: pci@0000:0a:01.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=32
                resources: memory:f8601000-f8601fff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:18f8(size=8) ioport:180c(size=4) ioport:18f0(size=8) ioport:1808(size=4) ioport:18e0(size=16) ioport:1810(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0f00000-c0f000ff ioport:1c00(size=32)
        *-ide:1
             description: IDE interface
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1c50(size=8) ioport:1c44(size=4) ioport:1c48(size=8) ioport:1c40(size=4) ioport:1c30(size=16) ioport:1c20(size=16)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK1652GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: LV01
             serial: Z8IJFJQJS
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000080a2
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 5f1dd860-2769-4105-8656-c9c80e23afac
                size: 145GiB
                capacity: 145GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-03-06 09:31:58 filesystem=ext4 lastmountpoint=/ modified=2013-03-06 10:21:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-03-06 10:21:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3960MiB
                capacity: 3960MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3960MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RW  DVRTD08A
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.54
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: outbound


```

Any help at all would be greatly appreciated!

---

### Post by praseodym on 2013-03-06
Please show the outputs of:
```

iwconfig
cat /etc/resolv.conf
rfkill list
iwlist chan
sudo iwlist scan
grep ath9k /etc/modprobe.d/*
dmesg | grep ath9k
```

---

### Post by Anghrist on 2013-03-07
Thanks for your reply - I've pasted the information below. Currently my laptop is plugged into the wired network at my workplace to allow internet access.

[B]iwconfig
[/B]```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.


```

[B]cat /etc/resolv.conf
[/B]```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.100.100.87
nameserver 192.100.100.88
nameserver 192.100.100.89
search erskine.local
```

**rfkill list**
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

[B]iwlist chan
[/B]```
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
lo        no frequency information.

eth0      no frequency information.


```

[B]sudo iwlist scan
[/B]```
wlan0     Scan completed :
          Cell 01 - Address: 00:0D:0B:6B:AE:18
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Wolverine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000037bded9184
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 0009576F6C766572696E65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD06001018010200
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

[B]grep ath9k /etc/modprobe.d/*
[/B]
Seems to do nothing ...

**dmesg | grep ath9k**
```
[   18.137404] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   18.658110] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.668504] Registered led device: ath9k-phy0


```

Please let me know if there's anything else I've missed.

Thank you!

---

### Post by praseodym on 2013-03-07
Try to deactivate the hardware encryption of th driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Additionally, I recommend using pure WPA2-AES encryption instead of WPA only

---

### Post by Anghrist on 2013-03-07
Thanks for the suggestions, but this didn't seem to work :(

Edit: Is this what's expected?

```
hollie@hollie-lt:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for hollie: 
options ath9k nohwcrypt=1
hollie@hollie-lt:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/net/wireless/cfg80211.ko
hollie@hollie-lt:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.5.0-25-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1


```

---

### Post by praseodym on 2013-03-08
Did you change the encryption mode?

---

### Post by Anghrist on 2013-03-08
Do you mean the network encryption? The network with WPA encryption was an access point at work - I also cannot connect to my home router (which uses WPA2).

---

### Post by Anghrist on 2013-03-09
*Shameless bump*

Any other thoughts? I'm completely stumped ... Is it worth mentioning that I tried installing Ubuntu 12.04 as well as the latest release of Joli OS (1.2.1?) and neither of them worked either? I can confirm that the adapter worked a week ago before I put Ubuntu on the laptop, so it's (probably) not a failure of the wifi card.

---

### Post by Anghrist on 2013-03-12
Sorry to bump this again - anyone have any thoughts on this? It's really frustrating, and I've tried so many things (and reinstalled Ubuntu so may times). Am I better off trying a different distro? I tried ndiswrapper but that didn't seem to work either (though that could have been an error on my part).

---

### Post by TK999 on 2013-03-12
First, bring up a terminal (Ctrl+Alt+T is the usual hotkey). Then type
```

sudo iw wlan0 scan | grep SSID

```
If your network is listed, proceed:
```

sudo wpa_passphrase "mywireless_ssid" "secretpassphrase"
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf &

```
If this succeeds, then enter:
```

sudo dhclient wlan0

```

---

### Post by Anghrist on 2013-03-14
Thanks for the suggestion - I've been bringing the laptop into work with me every day for the past week except today =/  

I will try this tonight so fingers crossed!

---

### Post by Anghrist on 2013-03-15
> **TK999 said:**
> First, bring up a terminal (Ctrl+Alt+T is the usual hotkey). Then type
```

sudo iw wlan0 scan | grep SSID

```
If your network is listed, proceed:
```

sudo wpa_passphrase "mywireless_ssid" "secretpassphrase"
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf &

```
If this succeeds, then enter:
```

sudo dhclient wlan0

```

This didn't seem to work ...

```

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf &

``` 

This stage didn't work at all, returning the error:

```
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
```

---

### Post by wildmanne39 on 2013-03-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Anghrist on 2013-03-18
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

Hey, I've attached the file as requested - I hope it makes more sense to you than it does to me =)

---

### Post by praseodym on 2013-03-18
Hi,

deactivate the "madwifi" driver in additional drivers and reboot.

---

### Post by Anghrist on 2013-03-19
The madwifi driver is something I installed the other day thinking it might sort this problem - it hasn't, but it also isn't showing up under 'Additional Drivers' under Software Sources. How else would I remove this? I already know that even with the driver removed/disabled the wifi doesn't connect - is there anything else that might have caused this issue? I've wracked my brain trying to think of something, but I'm completelhy out of ideas.

Thanks for you help and input.

---

### Post by praseodym on 2013-03-19
Please show:

```
locate ath_pci.ko | grep lib
```
Did you install it via software center?

---

### Post by Anghrist on 2013-03-20
> **praseodym said:**
> Please show:

```
locate ath_pci.ko | grep lib
```
Did you install it via software center?

I'm afraid this didn't do anything at all ... is that normal? As for the madwifi driver, I actually followed instructions online for installing it - I didn't take a note of where (stupid; it was either here or perhaps on AskUbuntu). I was considering wiping my laptop and starting fresh anyway - perhaps with 64-bit Ubuntu. I'm getting worried about all the silly little 'tweaks' I've done on here that might now be interfering with the actual solution.

---

### Post by Anghrist on 2013-03-26
Hello!

After pulling all of my hair out, I finally got around to reinstalling Ubuntu 12.10 (x64). So far all I've done is create /etc/modprobe.d/ath9k.conf with the contents "options ath9k nohwcrypt=1". Other than that this is a clean installation, fully updated. Everything looks a little like this:

**sudo lshw -class network**

```
 *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:63:29:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: 88E8072 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:23:8b:79:25:95
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=10.10.0.73 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:c0500000-c0503fff ioport:3000(size=256) memory:c0800000-c081ffff


```

[B]iwconfig
[/B]
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

[B]cat /etc/resolv.conf

[/B]```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search erskine.local


```

[B]rfkill list

[/B]```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

[B]iwlist chan

[/B]```
eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


```

[B]sudo iwlist scan

[/B]```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:0B:6B:AE:18
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Wolverine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007da7a08ae2
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0009576F6C766572696E65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD06001018010300
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```

[B]grep ath9k /etc/modprobe.d/*

[/B]```
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1


```

[B]dmesg | grep ath9k

[/B]```
[   19.310216] ath9k 0000:02:00.0: >enabling device (0000 -> 0002)
[   19.823506] ieee80211 phy0: >Selected rate control algorithm 'ath9k_rate_control'
[   19.837874] Registered led device: ath9k-phy0


```

For these results I am connected via ethernet to my work's network. The wireless network 'Wolverine' is an access point in my office which uses WPA encryption. I am unable to connect to this, or any other network (including my home network, which uses WPA-2 - I think). I currently don't have wicd or the madwifi drivers installed - just a clean OS with the above changes.

Any thoughts for why this isn't working? I should also mention I have now tried openSUSE 12.2, Linux Mint 14.1 and Joli OS 1.2.1 all with this same problem, as well as Ubuntu 12.04. My preference is to get this working on Ubuntu, installing those other distros was really only for testing purposes (I don't want my Ubuntu installation thinking I'm cheating on it :P).

Any help would be greatly appreciated!

---

### Post by Anghrist on 2013-03-27
I'm not sure if I should close this thread and begin a new one, because I think (perhaps) I might have discovered why this isn't working.

As you can see above, Ubuntu detects an Atheros AR928x card, and loads the ath9k driver. In my desperation, I tried swapping the wireless card in this laptop with another one I have. When disconnecting the card in my Ubuntu laptop, I discovered that it is in fact an Atheros AR5B91-X. Is there anyway to make Ubuntu detect the correct model of card? I tried using:

```
sudo modprobe ath5k
``` 

to load the correct driver (I'm assuming that's the correct driver for an AR5B91) but that hasn't worked. Are there any thoughts on this? I'm not really sure where to go from here.

---

### Post by wildmanne39 on 2013-03-27
Hi, please post the outcome of:
```
modinfo ath9k
```
Thanks

---

