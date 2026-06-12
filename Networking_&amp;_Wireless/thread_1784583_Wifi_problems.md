---
title: "Wifi problems"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by caspianaus on 2011-06-17
Dear all,

I'm not new to Ubuntu, and usually I've always been able to find solutions within the forums. Unfortunately this time I'm hitting a brick wall, and can't find the solution.  so I hope you guys can help me out. 
I'm having troubles with my wifi. The wifi is simply not recognized, and not even appearing in the network connections...
I had a similar problem with the last release and was able to fix it by using a simple sudo command (but can't remember which one, unfortunately), but since upgrading to the latest release, I just can't find a way to fix it. 
This is my first post in the forum, so I know many information is missing for a diagnosis, and I hope you can help me to provide them, and eventually solve my problem. In advance thank you for your help.

---

### Post by bkratz on 2011-06-17
> **caspianaus said:**
> Dear all,

I'm not new to Ubuntu, and usually I've always been able to find solutions within the forums. Unfortunately this time I'm hitting a brick wall, and can't find the solution.  so I hope you guys can help me out. 
I'm having troubles with my wifi. The wifi is simply not recognized, and not even appearing in the network connections...
I had a similar problem with the last release and was able to fix it by using a simple sudo command (but can't remember which one, unfortunately), but since upgrading to the latest release, I just can't find a way to fix it. 
This is my first post in the forum, so I know many information is missing for a diagnosis, and I hope you can help me to provide them, and eventually solve my problem. In advance thank you for your help.

This is the type of information necessary to help someone help you.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by caspianaus on 2011-06-17
Laptop HP Pavilion dv2000
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
 
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:9f:52:18  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe9f:5218/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:291695914 (291.6 MB)  TX bytes:17692937 (17.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73000 (73.0 KB)  TX bytes:73000 (73.0 KB)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
i915                  450944  3 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
drm                   180037  4 i915,drm_kms_helper
wl                   2642531  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17878  0 
sm_common              16737  1 r852
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   49822  2 r852,sm_common
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
lib80211               14570  1 wl
soundcore              12600  1 snd
serio_raw              12990  0 
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
ahci                   21591  2 
e100                   40108  0 
libahci                25548  1 ahci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

dmesg

[ 6934.192119] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 6934.208115] PM: Entering mem sleep
[ 6934.208174] Suspending console(s) (use no_console_suspend to debug)
[ 6934.208889] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 6934.241372] i8042 aux 00:0a: wake-up capability disabled by ACPI
[ 6934.243422] i8042 kbd 00:09: wake-up capability enabled by ACPI
[ 6934.243909] e100 0000:08:08.0: PME# enabled
[ 6934.243939] e100 0000:08:08.0: wake-up capability enabled by ACPI
[ 6934.243989] pci 0000:05:00.0: PCI INT A disabled
[ 6934.244180] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 6934.244196] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 6934.244208] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 6934.244220] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 6934.244232] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 6934.244283] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 6934.244595] ACPI handle has no context!
[ 6934.244605] sdhci-pci 0000:08:09.1: PCI INT B disabled
[ 6934.244612] ACPI handle has no context!
[ 6934.244687] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 6934.244829] i915 0000:00:02.0: PCI INT A disabled
[ 6934.248064] ACPI handle has no context!
[ 6934.311152] sd 2:0:0:0: [sda] Stopping disk
[ 6935.264990] PM: suspend of drv:sd dev:2:0:0:0 complete after 1056.108 msecs
[ 6935.265015] PM: suspend of drv:scsi dev:target2:0:0 complete after 1056.047 msecs
[ 6935.265032] PM: suspend of drv:scsi dev:host2 complete after 1055.983 msecs
[ 6935.280033] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 1036.012 msecs
[ 6935.280055] PM: suspend of drv: dev:pci0000:00 complete after 1035.354 msecs
[ 6935.280071] PM: suspend of devices complete after 1071.439 msecs
[ 6935.280074] PM: suspend devices took 1.072 seconds
[ 6935.312447] PM: late suspend of devices complete after 32.367 msecs
[ 6935.312594] ACPI: Preparing to enter system sleep state S3
[ 6935.360061] PM: Saving platform NVS memory
[ 6935.364127] Disabling non-boot CPUs ...
[ 6935.468035] CPU 1 is now offline
[ 6935.468507] Extended CMOS year: 2000
[ 6935.468507] Back to C!
[ 6935.468507] PM: Restoring platform NVS memory
[ 6935.468507] Extended CMOS year: 2000
[ 6935.468507] Enabling non-boot CPUs ...
[ 6935.468507] Booting Node 0 Processor 1 APIC 0x1
[ 6935.365545] Initializing CPU#1
[ 6935.560020] Switched to NOHz mode on CPU #1
[ 6935.560093] CPU1 is up
[ 6935.560669] ACPI: Waking up from system sleep state S3
[ 6935.668566] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6935.668605] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 6935.668652] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6935.668660] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 6935.668697] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010b)
[ 6935.668712] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xd1f1d001)
[ 6935.668719] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xd3f0d200)
[ 6935.668725] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[ 6935.668732] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x30200)
[ 6935.668742] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6935.668750] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6935.668809] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x4030b)
[ 6935.668823] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0x20312021)
[ 6935.668830] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0x20102000)
[ 6935.668837] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
[ 6935.668848] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6935.668856] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6935.668913] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x4040a)
[ 6935.668928] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x20512041)
[ 6935.668935] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xd400d400)
[ 6935.668941] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
[ 6935.668948] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0x50500)
[ 6935.668958] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6935.668966] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6935.669034] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6935.669072] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6935.669109] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6935.669146] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6935.669193] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 6935.669231] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6935.669237] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xd410d410)
[ 6935.669244] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x22803030)
[ 6935.669258] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100107)
[ 6935.669329] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 6935.669374] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 6935.669401] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 6935.669503] pci 0000:05:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6935.669532] pci 0000:05:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd4000000)
[ 6935.669540] pci 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6935.669550] pci 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[ 6935.669632] firewire_ohci 0000:08:09.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010a)
[ 6935.669656] firewire_ohci 0000:08:09.0: restoring config space at offset 0x4 (was 0xd2100000, writing 0xd4101000)
[ 6935.669663] firewire_ohci 0000:08:09.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 6935.669672] firewire_ohci 0000:08:09.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 6935.669693] firewire_ohci 0000:08:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
[ 6935.669696] firewire_ohci 0000:08:09.0: MMC cards are now supported by standard SDHCI controller
[ 6935.669712] sdhci-pci 0000:08:09.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 6935.669736] sdhci-pci 0000:08:09.1: restoring config space at offset 0x4 (was 0x0, writing 0xd4101800)
[ 6935.669743] sdhci-pci 0000:08:09.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 6935.669752] sdhci-pci 0000:08:09.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 6935.669778] pci 0000:08:09.2: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 6935.669802] pci 0000:08:09.2: restoring config space at offset 0x4 (was 0x0, writing 0xd4102000)
[ 6935.669811] pci 0000:08:09.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
[ 6935.669838] r852 0000:08:09.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 6935.669861] r852 0000:08:09.3: restoring config space at offset 0x4 (was 0x0, writing 0xd4102400)
[ 6935.669871] r852 0000:08:09.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
[ 6935.670525] PM: early resume of devices complete after 2.126 msecs
[ 6935.670631] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6935.670636] i915 0000:00:02.0: setting latency timer to 64
[ 6935.670696] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 6935.670711] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 6935.670825] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 6935.670921] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 6935.670938] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 6935.672088] usb usb2: root hub lost power or was reset
[ 6935.673909] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 6935.673917] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 6935.673945] usb usb3: root hub lost power or was reset
[ 6935.673962] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[ 6935.673970] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 6935.673999] usb usb4: root hub lost power or was reset
[ 6935.674015] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[ 6935.674022] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 6935.674051] usb usb5: root hub lost power or was reset
[ 6935.674069] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 6935.674077] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 6935.674143] pci 0000:00:1e.0: setting latency timer to 64
[ 6935.674161] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6935.674168] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 6935.674793] ata2: port disabled. ignoring.
[ 6935.674876] ahci 0000:00:1f.2: setting latency timer to 64
[ 6935.674979] pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 6935.674989] pci 0000:05:00.0: setting latency timer to 64
[ 6935.675026] e100 0000:08:08.0: wake-up capability disabled by ACPI
[ 6935.675033] e100 0000:08:08.0: PME# disabled
[ 6935.675123] sdhci-pci 0000:08:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 6935.675128] sdhci-pci 0000:08:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 6935.676644] sd 2:0:0:0: [sda] Starting disk
[ 6935.736227] firewire_core: skipped bus generations, destroying all nodes
[ 6935.796084] PM: resume of drv:usb dev:usb5 complete after 119.589 msecs
[ 6935.796115] PM: resume of drv:hub dev:5-0:1.0 complete after 119.594 msecs
[ 6935.796120] PM: resume of drv:usb dev:usb4 complete after 119.727 msecs
[ 6935.796129] PM: resume of drv: dev:ep_00 complete after 119.559 msecs
[ 6935.796134] PM: resume of drv:hub dev:4-0:1.0 complete after 119.713 msecs
[ 6935.796137] PM: resume of drv: dev:ep_81 complete after 119.592 msecs
[ 6935.796144] PM: resume of drv: dev:ep_00 complete after 119.677 msecs
[ 6935.796161] PM: resume of drv: dev:ep_81 complete after 119.717 msecs
[ 6935.796177] PM: resume of drv:usb dev:usb3 complete after 119.935 msecs
[ 6935.796191] PM: resume of drv:hub dev:3-0:1.0 complete after 119.878 msecs
[ 6935.796196] PM: resume of drv:usb dev:usb2 complete after 119.978 msecs
[ 6935.796200] PM: resume of drv: dev:ep_00 complete after 119.835 msecs
[ 6935.796208] PM: resume of drv: dev:ep_81 complete after 119.870 msecs
[ 6935.796212] PM: resume of drv:hub dev:2-0:1.0 complete after 119.984 msecs
[ 6935.796225] PM: resume of drv: dev:ep_00 complete after 119.989 msecs
[ 6935.796229] PM: resume of drv: dev:ep_81 complete after 119.995 msecs
[ 6935.866440] i8042 kbd 00:09: wake-up capability disabled by ACPI
[ 6935.992095] ata5: SATA link down (SStatus 0 SControl 300)
[ 6936.024477] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 6936.024482] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 6936.056352] ata1.00: configured for MWDMA2
[ 6936.237592] firewire_core: rediscovered device fw0
[ 6937.504093] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6937.509728] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 6937.515464] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 6937.515470] ata3.00: configured for UDMA/100
[ 6937.533155] PM: resume of drv:sd dev:2:0:0:0 complete after 1856.513 msecs
[ 6937.533185] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 1856.476 msecs
[ 6937.533195] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 1665.790 msecs
[ 6937.539846] PM: resume of devices complete after 1869.264 msecs
[ 6937.540156] PM: resume devices took 1.872 seconds
[ 6937.540201] PM: Finishing wakeup.
[ 6937.540203] Restarting tasks ... done.
[ 6937.545910] video LNXVIDEO:01: Restoring backlight state
[ 6938.080298] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 6938.373182] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6938.376195] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[ 6938.376505] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6941.500800] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 6948.920082] eth0: no IPv6 routers present
[54439.897593] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[54445.030239] PM: Syncing filesystems ... done.
[54445.032043] PM: Preparing system for mem sleep
[54445.368205] Freezing user space processes ... (elapsed 0.09 seconds) done.
[54445.464124] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[54445.480126] PM: Entering mem sleep
[54445.480188] Suspending console(s) (use no_console_suspend to debug)
[54445.480909] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[54445.513531] i8042 aux 00:0a: wake-up capability disabled by ACPI
[54445.515656] i8042 kbd 00:09: wake-up capability enabled by ACPI
[54445.516168] e100 0000:08:08.0: PME# enabled
[54445.516200] e100 0000:08:08.0: wake-up capability enabled by ACPI
[54445.516253] pci 0000:05:00.0: PCI INT A disabled
[54445.516437] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[54445.516453] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[54445.516465] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[54445.516478] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[54445.516491] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[54445.516543] HDA Intel 0000:00:1b.0: PCI INT A disabled
[54445.516831] ACPI handle has no context!
[54445.516840] sdhci-pci 0000:08:09.1: PCI INT B disabled
[54445.516848] ACPI handle has no context!
[54445.516923] ata_piix 0000:00:1f.1: PCI INT A disabled
[54445.517104] i915 0000:00:02.0: PCI INT A disabled
[54445.524056] ACPI handle has no context!
[54445.863167] sd 2:0:0:0: [sda] Stopping disk
[54446.795992] PM: suspend of drv:sd dev:2:0:0:0 complete after 1315.090 msecs
[54446.796014] PM: suspend of drv:scsi dev:target2:0:0 complete after 1315.023 msecs
[54446.796037] PM: suspend of drv:scsi dev:host2 complete after 1314.969 msecs
[54446.812020] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 1295.749 msecs
[54446.812043] PM: suspend of drv: dev:pci0000:00 complete after 1295.105 msecs
[54446.812058] PM: suspend of devices complete after 1331.386 msecs
[54446.812062] PM: suspend devices took 1.332 seconds
[54446.844449] PM: late suspend of devices complete after 32.380 msecs
[54446.844596] ACPI: Preparing to enter system sleep state S3
[54446.892060] PM: Saving platform NVS memory
[54446.896708] Disabling non-boot CPUs ...
[54447.000056] CPU 1 is now offline
[54447.000536] Extended CMOS year: 2000
[54447.000536] Back to C!
[54447.000536] PM: Restoring platform NVS memory
[54447.000536] Extended CMOS year: 2000
[54447.000536] Enabling non-boot CPUs ...
[54447.000536] Booting Node 0 Processor 1 APIC 0x1
[54446.898171] Initializing CPU#1
[54447.092021] Switched to NOHz mode on CPU #1
[54447.092093] CPU1 is up
[54447.092687] ACPI: Waking up from system sleep state S3
[54447.200569] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[54447.200608] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[54447.200654] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[54447.200663] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[54447.200701] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010b)
[54447.200715] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xd1f1d001)
[54447.200722] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xd3f0d200)
[54447.200729] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x20002020)
[54447.200735] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x30200)
[54447.200745] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[54447.200753] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[54447.200813] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x4030b)
[54447.200827] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0x20312021)
[54447.200834] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0x20102000)
[54447.200841] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x20004040)
[54447.200852] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[54447.200861] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[54447.200918] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x4040a)
[54447.200932] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x20512041)
[54447.200939] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xd400d400)
[54447.200946] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x20005050)
[54447.200952] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0x50500)
[54447.200962] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[54447.200970] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[54447.201038] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[54447.201076] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[54447.201113] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[54447.201150] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[54447.201197] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[54447.201235] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[54447.201241] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xd410d410)
[54447.201248] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x22803030)
[54447.201262] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100107)
[54447.201334] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[54447.201379] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[54447.201406] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[54447.201508] pci 0000:05:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[54447.201538] pci 0000:05:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd4000000)
[54447.201545] pci 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[54447.201556] pci 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[54447.201639] firewire_ohci 0000:08:09.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010a)
[54447.201662] firewire_ohci 0000:08:09.0: restoring config space at offset 0x4 (was 0xd2100000, writing 0xd4101000)
[54447.201669] firewire_ohci 0000:08:09.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[54447.201678] firewire_ohci 0000:08:09.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[54447.201700] firewire_ohci 0000:08:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
[54447.201703] firewire_ohci 0000:08:09.0: MMC cards are now supported by standard SDHCI controller
[54447.201719] sdhci-pci 0000:08:09.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[54447.201742] sdhci-pci 0000:08:09.1: restoring config space at offset 0x4 (was 0x0, writing 0xd4101800)
[54447.201749] sdhci-pci 0000:08:09.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[54447.201757] sdhci-pci 0000:08:09.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[54447.201784] pci 0000:08:09.2: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[54447.201807] pci 0000:08:09.2: restoring config space at offset 0x4 (was 0x0, writing 0xd4102000)
[54447.201818] pci 0000:08:09.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
[54447.201844] r852 0000:08:09.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[54447.201869] r852 0000:08:09.3: restoring config space at offset 0x4 (was 0x0, writing 0xd4102400)
[54447.201879] r852 0000:08:09.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
[54447.202533] PM: early resume of devices complete after 2.132 msecs
[54447.202636] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[54447.202642] i915 0000:00:02.0: setting latency timer to 64
[54447.202783] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[54447.202798] HDA Intel 0000:00:1b.0: setting latency timer to 64
[54447.202912] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[54447.203016] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[54447.203031] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[54447.204003] usb usb2: root hub lost power or was reset
[54447.205120] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[54447.205892] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[54447.205921] usb usb3: root hub lost power or was reset
[54447.205938] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[54447.205945] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[54447.205973] usb usb4: root hub lost power or was reset
[54447.205989] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[54447.205997] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[54447.206026] usb usb5: root hub lost power or was reset
[54447.206044] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[54447.206052] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[54447.206118] pci 0000:00:1e.0: setting latency timer to 64
[54447.206137] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[54447.206143] ata_piix 0000:00:1f.1: setting latency timer to 64
[54447.206176] ahci 0000:00:1f.2: setting latency timer to 64
[54447.206236] pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[54447.206246] pci 0000:05:00.0: setting latency timer to 64
[54447.206288] e100 0000:08:08.0: wake-up capability disabled by ACPI
[54447.206296] e100 0000:08:08.0: PME# disabled
[54447.206900] ata2: port disabled. ignoring.
[54447.206993] sdhci-pci 0000:08:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[54447.206998] sdhci-pci 0000:08:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[54447.208520] sd 2:0:0:0: [sda] Starting disk
[54447.268241] firewire_core: skipped bus generations, destroying all nodes
[54447.304210] PM: resume of drv:i915 dev:0000:00:02.0 complete after 101.585 msecs
[54447.328119] PM: resume of drv:usb dev:usb2 complete after 120.023 msecs
[54447.328153] PM: resume of drv:usb dev:usb3 complete after 120.032 msecs
[54447.328158] PM: resume of drv:hub dev:2-0:1.0 complete after 120.049 msecs
[54447.328172] PM: resume of drv: dev:ep_00 complete after 120.057 msecs
[54447.328179] PM: resume of drv: dev:ep_81 complete after 120.069 msecs
[54447.328183] PM: resume of drv:usb dev:usb4 complete after 119.914 msecs
[54447.328233] PM: resume of drv:usb dev:usb5 complete after 119.863 msecs
[54447.328245] PM: resume of drv:hub dev:3-0:1.0 complete after 120.052 msecs
[54447.328254] PM: resume of drv:hub dev:4-0:1.0 complete after 119.958 msecs
[54447.328263] PM: resume of drv: dev:ep_00 complete after 119.916 msecs
[54447.328270] PM: resume of drv:hub dev:5-0:1.0 complete after 119.871 msecs
[54447.328279] PM: resume of drv: dev:ep_00 complete after 119.831 msecs
[54447.328285] PM: resume of drv: dev:ep_00 complete after 120.007 msecs
[54447.328288] PM: resume of drv: dev:ep_81 complete after 120.067 msecs
[54447.328297] PM: resume of drv: dev:ep_81 complete after 119.975 msecs
[54447.328303] PM: resume of drv: dev:ep_81 complete after 119.880 msecs
[54447.391739] i8042 kbd 00:09: wake-up capability disabled by ACPI
[54447.524095] ata5: SATA link down (SStatus 0 SControl 300)
[54447.552477] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[54447.552482] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[54447.584351] ata1.00: configured for MWDMA2
[54447.768673] firewire_core: rediscovered device fw0
[54449.036091] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[54449.041730] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[54449.047469] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[54449.047476] ata3.00: configured for UDMA/100
[54449.073502] PM: resume of drv:sd dev:2:0:0:0 complete after 1864.983 msecs
[54449.073532] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 1864.945 msecs
[54449.073541] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 1680.754 msecs
[54449.080264] PM: resume of devices complete after 1877.673 msecs
[54449.080547] PM: resume devices took 1.880 seconds
[54449.080591] PM: Finishing wakeup.
[54449.080593] Restarting tasks ... done.
[54449.087471] video LNXVIDEO:01: Restoring backlight state
[54449.520605] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[54450.249164] ADDRCONF(NETDEV_UP): eth0: link is not ready
[54450.252196] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[54450.252561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[54460.592059] eth0: no IPv6 routers present
[54463.491934] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[54464.539586] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[54754.982185] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[58271.241168] audit_printk_skb: 15 callbacks suppressed
[58271.241174] type=1400 audit(1308274240.154:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=11551 comm="apparmor_parser"
[58271.243475] type=1400 audit(1308274240.154:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=11551 comm="apparmor_parser"
[58277.718135] type=1400 audit(1308274246.631:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=11587 comm="apparmor_parser"
[58277.720791] type=1400 audit(1308274246.635:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=11587 comm="apparmor_parser"
[60938.125474] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[61359.054154] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[61656.992377] e100 0000:08:08.0: eth0: NIC Link is Down
[61658.992199] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[61660.992376] e100 0000:08:08.0: eth0: NIC Link is Down
[61662.992245] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[61676.992408] e100 0000:08:08.0: eth0: NIC Link is Down
[61678.992248] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[61686.992412] e100 0000:08:08.0: eth0: NIC Link is Down
[61688.992255] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex

sudo lshw -C network
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4000000-d4003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:9f:52:18
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d4100000-d4100fff ioport:3000(size=64)

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lsb_release -d
Description:	Ubuntu 11.04

uname -mr
2.6.38-8-generic i686

sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

---

### Post by wildmanne39 on 2011-06-17
Hi, here is a link to get your wireless working.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)
You may just be able to click on additional drivers while connected to a wired interent connection and install the driver.

---

### Post by nm_geo on 2011-06-17
> **wildmanne39 said:**
> Hi, here is a link to get your wireless working.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)
You may just be able to click on additional drivers while connected to a wired interent connection and install the driver.

Excellent now there are two NM on here Lovington here wildmanne39.

Not to try to take over this thread either, but I have the same wireless card and mine will not run with the STA driver.  

Right now I am testing Oneiric and I still have the same driver working well here.

```
*-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c1:24:e5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:efcf0000-efcfffff
  *-network *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:c5:67:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0-1-generic firmware=478.104 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg


```I can help you with getting those with the CLI or Synaptic you pick?

---

### Post by wildmanne39 on 2011-06-17
> **nm_geo said:**
> Excellent now there are two NM on here Lovington here wildmanne39.

Not to try to take over this thread either, but I have the same wireless card and mine will not run with the STA driver.  

Right now I am testing Oneiric and I still have the same driver working well here.

```
*-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c1:24:e5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:efcf0000-efcfffff
  *-network *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:c5:67:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0-1-generic firmware=478.104 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg


```I can help you with getting those with the CLI or Synaptic you pick?
Hi, I lived in Hobbs for 2 years.

---

### Post by caspianaus on 2011-06-17
Thanks, tried indeed the driver with no success. What's the simplest? Synaptic?

---

### Post by nm_geo on 2011-06-17
> **caspianaus said:**
> Thanks, tried indeed the driver with no success. What's the simplest? Synaptic?
Yes but we may need to fix a few things.. Did you activate the STA driver?

---

### Post by caspianaus on 2011-06-17
yes i activated the driver

---

### Post by nm_geo on 2011-06-17
Try this open Synaptic.

Do a search on bcm

Remove drivers and packages that are active. Mainly bcmwl-kernel-source
and anything that has sta in the description.

Ok now we will install two:

firmware-b43-installer
b43-fwcutter

We may need to check the blacklist too in terminal:
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'

``` Copy and paste that code in terminal
Post results

---

### Post by caspianaus on 2011-06-18
ok, removed the drivers as indicated, installed the 2, result from code:


# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

---

### Post by nm_geo on 2011-06-18
> **caspianaus said:**
> ok, removed the drivers as indicated, installed the 2, result from code:


# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
Good B43 and ssb are not blacklisted.

```
sudo lshw -C network

```

---

### Post by caspianaus on 2011-06-18
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4000000-d4003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:9f:52:18
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d4100000-d4100fff ioport:3000(size=64)

---

### Post by nm_geo on 2011-06-18
Hmmm.. Ok you installed the b43-fwcutter and firmware in Synaptic right?

```
rfkill list all
```

You might need to reboot too.

---

### Post by caspianaus on 2011-06-18
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

Rebooting now

---

### Post by nm_geo on 2011-06-18
Do a 

```
lsmod
```

and post result please

---

### Post by caspianaus on 2011-06-18
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
arc4                   12473  2 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
b43                   296610  0 
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 b43
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 b43,mac80211
mtd                    26720  2 sm_common,nand
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
ahci                   21591  2 
e100                   40108  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci
ssb                    45942  1 b43


btw, after the reboot, wireless networks appear in the list, but indicating wireless disabled (checked the "enable wireless" of course, but still "wireless disabled")

---

### Post by nm_geo on 2011-06-18
We are getting there ..
Do the 

```
sudo lshw -C network
``````

rfkill list all
```and this log line copy and paste

```
dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl'
```

---

### Post by nm_geo on 2011-06-18
Try this too

```
sudo rfkill unblock all
```Should have tried that before the others

Then 

rfkill list all

---

### Post by caspianaus on 2011-06-18
lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
arc4                   12473  2 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
b43                   296610  0 
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 b43
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 b43,mac80211
mtd                    26720  2 sm_common,nand
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
ahci                   21591  2 
e100                   40108  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci
ssb                    45942  1 b43
mark@mark-HP-Pavilion-dv2000-RE178AV:~$ sudo lshw -C network
[sudo] password for mark: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:d4000000-d4003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:9f:52:18
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d4100000-d4100fff ioport:3000(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:41:0f:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no


dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl'
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv2000 (RE178AV)/30B2, BIOS F.39 08/27/2007
[    0.000000] found SMP MP-table at [c00f67e0] f67e0
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.177915] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.194689] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.194689] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.744232] ACPI: No dock devices found.
[    0.744236] HEST: Table not found.
[    0.757146] usbcore: registered new interface driver usbfs
[    0.757146] usbcore: registered new interface driver hub
[    0.757146] usbcore: registered new device driver usb
[    0.757146] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.764072] Switching to clocksource hpet
[    0.767871] Switched to NOHz mode on CPU #0
[    0.767973] Switched to NOHz mode on CPU #1
[    0.778367] pnp: PnP ACPI: found 11 devices
[    0.816715] pci 0000:08:08.0: Firmware left e100 interrupts enabled; disabling
[    0.836628] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.860018] ACPI: Lid Switch [LID0]
[    0.893612] ERST: Table is not found!
[    1.247867] isapnp: No Plug & Play device found
[    1.272031] i2c-core: driver [adp5520] using legacy suspend method
[    1.272034] i2c-core: driver [adp5520] using legacy resume method
[    1.274347] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.292197] hub 1-0:1.0: USB hub found
[    1.292715] hub 2-0:1.0: USB hub found
[    1.293145] hub 3-0:1.0: USB hub found
[    1.296253] hub 4-0:1.0: USB hub found
[    1.296677] hub 5-0:1.0: USB hub found
[    1.298410] device-mapper: multipath: version 1.2.0 loaded
[    1.298414] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.301708] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.699475] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.699492] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[    1.716083] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.716096] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.716108] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.716118] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.724922] sdhci-pci 0000:08:09.1: SDHCI controller found [1180:0822] (rev 19)
[    1.726003] mmc0: no vmmc regulator found
[    1.756170] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    1.773021] e100 0000:08:08.0: eth0: addr 0xd4100000, irq 20, MAC addr 00:16:d3:9f:52:18
[   23.009163] lp: driver loaded but no devices found
[   23.338260] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   23.447821] leds_ss4200: no LED devices found
[   23.493130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.496167] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   23.508208] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.145054] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   24.325551] Registered led device: b43-phy0::tx
[   24.325589] Registered led device: b43-phy0::rx
[   24.325621] Registered led device: b43-phy0::radio
[   24.325646] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   24.605232] Console: switching to colour frame buffer device 160x50
[   33.904013] eth0: no IPv6 routers present

---

### Post by caspianaus on 2011-06-18
rfkill unblock all did the trick!


rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by nm_geo on 2011-06-18
okay reboot and then marked solved

We need to make sure there is nothing in conflict

---

### Post by caspianaus on 2011-06-18
Thanks a lot, problem solved! Don't know what's wrong with the driver, worked perfect in the previous releases. 
Thanks you very much, enjoying wifi again! You've been very helpfulm hope it will help some others.
All the best, mate
;-)

---

### Post by caspianaus on 2011-06-18
no, didn't know their are to wifi card. strange

---

### Post by nm_geo on 2011-06-18
> **caspianaus said:**
> no, didn't know their are to wifi card. strange

NP just wondering..
Please marked solved so others can see and benefit .. Be well

---

### Post by caspianaus on 2011-06-18
rebooted, no conflicts, everything working fine. Marking solved. Thanks again.

---

