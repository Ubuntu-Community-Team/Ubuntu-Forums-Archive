---
title: "System lockups in firefox when viewing images - possibly graphics related"
date: 2011-01-07
forum: Multimedia Software
---

### Post by ets2006 on 2011-01-07
Hiya guys, girls, and web search spiders. I've got an interesting one today, and its been bugging me for weeks.
At first, I thought it was just a bug with [arrivabus.co.uk]("http://arrivabus.co.uk"), maybe a corrupted image, but recently I've been experiencing complete system lockups whilst browsing the interwebs. Complete, as in, have to hard power cycle the machine. Its main causes, from what I've found, appear to be images. This one, ([http://i.imgur.com/DfUgJ.jpg](http://i.imgur.com/DfUgJ.jpg)) caused my latest lockup. Apparently its a picture of one of those "african bankers/royalty" who email you.
What's even weirder, is that most of the time, there's nothing in kern.log the moment the lockup happens, laptop just goes completely dead. I said most of the time, because on December 22, I got lucky, and the laptop appeared to have managed to save the logs before locking up. I'll post below.
```
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746764] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746773] IP: [<ffffffffa00f9a0d>] radeon_ttm_bo_destroy+0x3d/0xc0 [radeon]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746809] PGD 6a4f7067 PUD 6a4f6067 PMD 0 
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746814] Oops: 0002 [#1] SMP 
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746817] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746821] CPU 1 
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746823] Modules linked in: michael_mic arc4 b44 ssb mii cryptd aes_x86_64 aes_generic binfmt_misc parport_pc ppdev dm_crypt joydev snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm lib80211_crypt_tkip snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq wl(P) snd_timer snd_seq_device dell_wmi lib80211 snd edac_core dell_laptop dcdbas soundcore psmouse pcspkr serio_raw snd_page_alloc edac_mce_amd k8temp i2c_piix4 shpchp lp parport radeon video ttm drm_kms_helper sdhci_pci sdhci output drm ahci i2c_algo_bit led_class libahci pata_atiixp [last unloaded: mii]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746864] 
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746869] Pid: 1055, comm: Xorg Tainted: P            2.6.35-22-generic #35-Ubuntu 0WY383/Vostro   1000 
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746872] RIP: 0010:[<ffffffffa00f9a0d>]  [<ffffffffa00f9a0d>] radeon_ttm_bo_destroy+0x3d/0xc0 [radeon]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746893] RSP: 0018:ffff88006a6a1ad8  EFLAGS: 00010286
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746896] RAX: ffff880036fc8c00 RBX: ffff880036fc8c00 RCX: 0000000000000000
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746899] RDX: 0000000000000000 RSI: ffffffffa00af350 RDI: ffff880075676e38
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746902] RBP: ffff88006a6a1af8 R08: 0000000000000000 R09: 0000000000000000
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746904] R10: 0000000000000001 R11: 0000000000000000 R12: ffff880036fc8c78
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746907] R13: ffff8800756764f8 R14: 0000000000000001 R15: 0000000002dc6000
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746911] FS:  00007f6d00b18840(0000) GS:ffff880001f00000(0000) knlGS:00000000dfeecb70
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746914] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746917] CR2: 0000000000000008 CR3: 000000006a4e2000 CR4: 00000000000006e0
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746920] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746922] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746926] Process Xorg (pid: 1055, threadinfo ffff88006a6a0000, task ffff880072e696e0)
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746928] Stack:
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746930]  ffff880036fc8cbc ffff880036fc8c78 ffff880036fc8cbc ffff8800756764f8
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746934] <0> ffff88006a6a1b28 ffffffffa00af3f5 ffff880075676868 ffff880036fc8cbc
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746939] <0> ffffffffa00af350 ffff8800756764f8 ffff88006a6a1b48 ffffffff812ba857
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746945] Call Trace:
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746958]  [<ffffffffa00af3f5>] ttm_bo_release_list+0xa5/0x100 [ttm]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746966]  [<ffffffffa00af350>] ? ttm_bo_release_list+0x0/0x100 [ttm]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746972]  [<ffffffff812ba857>] kref_put+0x37/0x70
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746980]  [<ffffffffa00b216c>] ttm_bo_release+0x7c/0xa0 [ttm]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746987]  [<ffffffffa00b20f0>] ? ttm_bo_release+0x0/0xa0 [ttm]
Dec 22 20:32:12 LXS-VOSTRO1 kernel: [210075.746991]  [<ffffffff812ba857>] kref_put+0Dec 22 20:33:10 LXS-VOSTRO1 kernel: imklog 4.2.0, log source = /proc/kmsg started.
```Im using a Dell Vostro 1000, with the ATI Radeon "Xpress" 1550 series,  which, as far as I'm aware, is just a rebadged "Xpress" 200 series.
I'm running 10.10, pretty much a clean install.
Here's my lshw;
```
user@LXS-VOSTRO1:~$ sudo lshw
[sudo] password for user: 
lxs-vostro1               
    description: Portable Computer
    product: Vostro   1000
    vendor: Dell Inc.
    version: Not Specified
    serial: 
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=portable uuid=44454C4C-4700-1034-8039-B7C04F35344A
  *-core
       description: Motherboard
       product: 0WY383
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN4864387Q0478.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: 2.6.3 (12/07/2007)
          size: 105KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: Engineering Sample
          slot: Socket M2/S1G1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0100000-c01fffff ioport:c8000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             resources: ioport:3000(size=4096) memory:c0200000-c02fffff ioport:80400000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 01
                serial: 00:22:5f:5f:aa:b2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.1.10.2 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:c0200000-c0203fff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8438(size=8) ioport:8454(size=4) ioport:8430(size=8) ioport:8450(size=4) ioport:8400(size=16) memory:c0004000-c00043ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HM121HI
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: LZ10
                serial: S14PJD0Q859426
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d66b6
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: df016e3e-c658-4534-8f4f-376cd500308d
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-12-12 13:08:03 filesystem=ext4 lastmountpoint=/ modified=2010-12-12 13:47:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-07 13:04:00 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 4693MiB
                   capacity: 4693MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4693MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:c0005000-c0005fff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:c0006000-c0006fff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:c0007000-c0007fff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:c0008000-c0008fff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:c0009000-c0009fff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:c0004400-c00044ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
           *-cdrom
                description: DVD-RAM writer
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
                version: D400
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:c0000000-c0003fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: memory:c0300000-c03fffff
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 02
                serial: 00:21:70:7b:43:d6
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.1.0.2 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:21 memory:c0300000-c0301fff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:08:01.0
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:20 memory:c0302800-c03028ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:08:01.1
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:c0302c00-c0302cff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-battery
       description: Lithium Ion Battery
       product: Sanyo DELLUD2648
       vendor: Sanyo DELLUD2648
       physical id: 1
       slot: System Battery Bay
       capacity: 53000mWh
       configuration: voltage=11.1V

```If anybody can enlighten me to the cause(s) of these seemingly random system lockups, I'd greatly appreciate it. :)

---

### Post by lovinglinux on 2011-01-07
> **ets2006 said:**
> Hiya guys, girls, and web search spiders.

That was funny. I wonder if the search spiders will reply :)

> **ets2006 said:**
> I'm running 10.10, pretty much a clean install.

Are you running a clean Firefox profile as well?

---

### Post by ets2006 on 2011-01-07
> **lovinglinux said:**
> Are you running a clean Firefox profile as well?

No. I disabled all my plugins though, restarted ff, and got a complete lockup. Strange, because I can wget the image and open it in the gnome image viewer.

---

### Post by lovinglinux on 2011-01-07
> **ets2006 said:**
> No. I disabled all my plugins though, restarted ff, and got a complete lockup. Strange, because I can wget the image and open it in the gnome image viewer.

Try creating a new profile, just for testing.

See [http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

---

### Post by ets2006 on 2011-01-07
Ok, I created a new profile, navigated to the forums, and ctrl+clicked on the image link. System locked up, solid. Hard reboot, and everything appears normal, but nothing in kern.log to indicate anything unusual. Strange. :(

---

### Post by mocha on 2011-01-07
Hard locks under Linux usually indicate some sort of hardware failure.  I've had numerous hardware problems that would cause lockups but were not immediately obvious until I investigated.  Check your motherboard and video card for blown caps, test your memory with memtest, try a different power supply, etc..  There's a lot it could be.  Can you put your hard drive into another computer, boot it, and see if you get hard locks on the same website?  Then you'll know for certain it's your hardware.

---

### Post by lovinglinux on 2011-01-07
> **ets2006 said:**
> Ok, I created a new profile, navigated to the forums, and ctrl+clicked on the image link. System locked up, solid. Hard reboot, and everything appears normal, but nothing in kern.log to indicate anything unusual. Strange. :(

Create a test user in Ubuntu, log with that account and test it.

---

### Post by ets2006 on 2011-01-07
> **mocha said:**
> Hard locks under Linux usually indicate some sort of hardware failure.  I've had numerous hardware problems that would cause lockups but were not immediately obvious until I investigated.  Check your motherboard and video card for blown caps, test your memory with memtest, try a different power supply, etc..  There's a lot it could be.  Can you put your hard drive into another computer, boot it, and see if you get hard locks on the same website?  Then you'll know for certain it's your hardware.
Its a laptop, so I'm not exactly going to strip it down to have a look for bad caps. I know my hdd is on its way out (bad sectors) but its still usable and shouldn't be causing any issues.
I'll do a memtest, but I'm still pretty sure its the drivers for my graphics. Ive also got another laptop, with the same chipset and graphics, so if I can find a spare ide hdd around the house, I'll try to install ubuntu on that and see if that dies too. What was the absolute minimum for an ubuntu install again??

> **lovinglinux said:**
> Create a test user in Ubuntu, log with that account and test it.
Will do, I'll report back.

---

### Post by lovinglinux on 2011-01-07
> **ets2006 said:**
> Will do, I'll report back.

If that renders the same result, then try the LiveCD.

---

### Post by ets2006 on 2011-01-08
> **lovinglinux said:**
> If that renders the same result, then try the LiveCD.

Hmm, looks like I'll be downloading the LiveCD over my <sarcasm>extremely fast</sarcasm> adsl connection. Or maybe, I'll drop in to grans, to use her cable connection - she never uses it and I wouldn't want it to go to waste :P
Interestingly, I found this in kern.log - you can clearly see that the last line was interrupted whilst being written. All timestamps make sense, so it looks like it may be graphics related.
```
Jan  8 09:55:32 LXS-VOSTRO1 kernel: [56319.038044] radeon 0000:01:05.0: object_init failed for (47996928, 0x00000006)
Jan  8 09:55:32 LXS-VOSTRO1 kernel: [56319.038053] [drm:radeon_gem_object_create] *ERROR* Failed to allocate GEM object (47996928, 4, 4096, -12)
Jan  8 09:55:32 LXS-VOSTRO1 kernel: [56319.227635] radeon 0000:01:05.0: object_init failed for (47996928, 0x00000006)
Jan  8 09:55:32 LXS-VOSTRO1 kernel: [56319.227643] [drm:radeon_gem_object_create] *ERROR* Failed to allocate GEM object (47996928, 4, 4096, -12)
Jan  8 09:55:32 LXS-VOSTRO1 kernel: [56319.227792] radeon 0000:01:05.0: object_init failed for (47996928, 0x00000Jan  8 09:56:43 LXS-VOSTRO1 kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

---

### Post by Yellow Pasque on 2011-01-08
Looks like a problem with the video driver. For your card, I highly recommend using the xorg-edgers PPA.

---

### Post by ets2006 on 2011-01-08
> **Temüjin said:**
> Looks like a problem with the video driver. For your card, I highly recommend using the xorg-edgers PPA.
I'll try to get running on the xorg-edgers packages whilst my ISO downloads, and I'll report back.

Progress report
Current progress: none. I've found the PPA, but it seems to be for 10.04, and I cant use the drivers they have on my 10.10 because of dependency problems, apparently. Any ideas on how to get it to work nicely on 10.10 without having to make lots of effort?

---

### Post by Yellow Pasque on 2011-01-08
It has packages for both Lucid and Maverick (and maybe Karmic or Natty). It should work fine if you add the PPA as a software source and update. It won't work if you try to download individual packages. It says that right in the instructions on the page and you did read those, didn't you?

> I cant use the drivers they have on my 10.10 because of dependency problems, apparently
Why do you say this? What is the output of:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by ets2006 on 2011-01-08
> **Temüjin said:**
> It has packages for both Lucid and Maverick (and maybe Karmic or Natty). It should work fine if you add the PPA as a software source and update. It won't work if you try to download individual packages. It says that right in the instructions on the page and you did read those, didn't you?
Yes.

> **Temüjin said:**
> 
Why do you say this?
Because I'm not exactly the best with linux, I probably made a typo.

> **Temüjin said:**
> 
What is the output of:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```Decidedly a lot better than whatever I tried earlier. I'll reboot, and report back.

Update: After installing the drivers, and rebooting, i tried looking at the image again. This time, I saw X flick over to tty1, then the laptop showed the classic signs of a kernel panic... the flashing caps lock and scroll lock keys. kern.log yeilds nothing other than
```
Jan  8 15:57:31 LXS-VOSTRO1 kernel: [  268.550939] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
```

---

### Post by Yellow Pasque on 2011-01-08
Run memtest

---

### Post by ets2006 on 2011-01-08
> **Temüjin said:**
> Run memtest
Done. It passed.

Sooo... any ideas? Or am I stuck with random kernel panics on opening images/webpages?

---

### Post by ets2006 on 2011-01-23
I may have some success. Booting with "radeon.modeset=0" appears to have fixed it, but I haven't had a chance to fully test it. I'll have to see how it goes and report back when its fully tested. :D

---

