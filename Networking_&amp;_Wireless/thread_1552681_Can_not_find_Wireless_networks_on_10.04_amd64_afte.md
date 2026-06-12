---
title: "Can not find Wireless networks on 10.04 amd64 after uptates"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by philosopher2003@gmail.com on 2010-08-14
Everything was working great till I updated about 8 days ago!  I have since been un able to find a solution.



PC Modle MSI Wind U230
 

 lspci 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
 00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) 
 00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) 
 00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) 
 00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 
 00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
 00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
 00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
 00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
 00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
 00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
 00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c) 
 00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
 00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
 01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
 01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller 
 02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe 
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
 

 lsusb Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 002: ID 5986:02c1 Acer, Inc  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 lspci -nn | grep 'Wireless Brand' I got no out put here
 But I know it is a RaLink RT3090 Wireless 802.11n 1T/1R PCIe
 

 ifconfig 

 eth0      Link encap:Ethernet  HWaddr 40:61:86:18:ba:68   
           inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::4261:86ff:fe18:ba68/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:5158 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4714 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:5106984 (5.1 MB)  TX bytes:835551 (835.5 KB) 
           Interrupt:28 Base address:0xe000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:37179 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:37179 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:5052957 (5.0 MB)  TX bytes:5052957 (5.0 MB) 
 

 iwconfig lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 pan0      no wireless extensions. 
 

 iwconfig wlan0 wlan0     No such device 
 

 lsmod Module                  Size  Used by 
 binfmt_misc             7960  1  
 ppdev                   6375  0  
 joydev                 11072  0  
 snd_hda_codec_atihdmi     3023  1  
 snd_hda_codec_realtek   279040  1  
 rfcomm                 40393  4  
 fbcon                  39270  71  
 tileblit                2487  1 fbcon 
 font                    8053  1 fbcon 
 bitblit                 5811  1 fbcon 
 softcursor              1565  1 bitblit 
 vga16fb                12757  0  
 vgastate                9857  1 vga16fb 
 snd_hda_intel          25677  2  
 snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep               6924  1 snd_hda_codec 
 snd_pcm_oss            41394  0  
 snd_mixer_oss          16299  1 snd_pcm_oss 
 snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
 sco                     9617  2  
 snd_seq_dummy           1782  0  
 snd_seq_oss            31219  0  
 bridge                 53184  0  
 stp                     2171  1 bridge 
 snd_seq_midi            5829  0  
 snd_rawmidi            23420  1 snd_seq_midi 
 bnep                   11884  2  
 snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
 snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 l2cap                  34806  16 rfcomm,bnep 
 radeon                740390  3  
 uvcvideo               62467  0  
 snd_timer              23649  2 snd_pcm,snd_seq 
 snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 ttm                    60847  1 radeon 
 videodev               40518  1 uvcvideo 
 drm_kms_helper         30742  1 radeon 
 v4l1_compat            15495  2 uvcvideo,videodev 
 v4l2_compat_ioctl32    12020  1 videodev 
 snd                    71106  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 btusb                  12969  2  
 bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb 
 drm                   199204  5 radeon,ttm,drm_kms_helper 
 i2c_algo_bit            6024  1 radeon 
 psmouse                64576  0  
 serio_raw               4918  0  
 i2c_piix4               9639  0  
 soundcore               8052  1 snd 
 snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
 edac_core              45423  0  
 edac_mce_amd            9278  0  
 k8temp                  3912  0  
 shpchp                 33711  0  
 video                  20623  0  
 output                  2503  1 video 
 lp                      9336  0  
 parport                37160  2 ppdev,lp 
 r8169                  39650  0  
 usb_storage            49833  0  
 mii                     5237  1 r8169 
 ahci                   37870  3  
 pata_atiixp             4209  0  
 

 lsmod | grep "wlan_module_name" No output here eather but see above!
 

 dmesg [    0.625495] ACPI Error: No handler for Region [SACS] (ffff88011384b55 [PCI_Config] (20090903/evregion-319) 
 [    0.625503] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295) 
 [    0.625510] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node ffff880113843c00), AE_NOT_EXIST 
 [    0.625545] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node ffff880113843c00), AE_NOT_EXIST 
 [    0.625576] ACPI Error: No handler for Region [SACS] (ffff88011384b55 [PCI_Config] (20090903/evregion-319) 
 [    0.625582] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295) 
 [    0.625589] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node ffff880113843ce0), AE_NOT_EXIST 
 [    0.625622] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node ffff880113843ce0), AE_NOT_EXIST 
 [    0.625665] ACPI Error: No handler for Region [SACS] (ffff88011384b55 [PCI_Config] (20090903/evregion-319) 
 [    0.625671] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295) 
 [    0.625677] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node ffff880113843ec0), AE_NOT_EXIST 
 [    0.625710] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node ffff880113843ec0), AE_NOT_EXIST 
 [    0.625740] ACPI Error: No handler for Region [SACS] (ffff88011384b55 [PCI_Config] (20090903/evregion-319) 
 [    0.625746] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295) 
 [    0.625752] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node ffff880113843fa0), AE_NOT_EXIST 
 [    0.625785] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node ffff880113843fa0), AE_NOT_EXIST 
 [    0.635210] thermal LNXTHERM:01: registered as thermal_zone0 
 [    0.635221] ACPI: Thermal Zone [THRM] (42 C) 
 [    0.637260] Linux agpgart interface v0.103 
 [    0.637310] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
 [    0.638901] brd: module loaded 
 [    0.639517] loop: module loaded 
 [    0.639649] input: Macintosh mouse button emulation as /devices/virtual/input/input4 
 [    0.639935] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    0.640023] pata_acpi 0000:00:14.1: setting latency timer to 64 
 [    0.640519] Fixed MDIO Bus: probed 
 [    0.640571] PPP generic driver version 2.4.2 
 [    0.640636] tun: Universal TUN/TAP device driver, 1.6 
 [    0.640639] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
 [    0.640762] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
 [    0.640854] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
 [    0.640894] ehci_hcd 0000:00:12.2: EHCI Host Controller 
 [    0.640962] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1 
 [    0.641024] ehci_hcd 0000:00:12.2: debug port 1 
 [    0.641058] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff800 
 [    0.664413] Freeing initrd memory: 8140k freed 
 [    0.670036] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00 
 [    0.670190] usb usb1: configuration #1 chosen from 1 choice 
 [    0.670238] hub 1-0:1.0: USB hub found 
 [    0.670254] hub 1-0:1.0: 6 ports detected 
 [    0.670421]   alloc irq_desc for 19 on node 0 
 [    0.670424]   alloc kstat_irqs on node 0 
 [    0.670433] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
 [    0.670465] ehci_hcd 0000:00:13.2: EHCI Host Controller 
 [    0.670525] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2 
 [    0.670577] ehci_hcd 0000:00:13.2: debug port 1 
 [    0.670607] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe7ff400 
 [    0.690028] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00 
 [    0.690141] usb usb2: configuration #1 chosen from 1 choice 
 [    0.690178] hub 2-0:1.0: USB hub found 
 [    0.690188] hub 2-0:1.0: 6 ports detected 
 [    0.690294] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
 [    0.690393] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    0.690420] ohci_hcd 0000:00:12.0: OHCI Host Controller 
 [    0.690481] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3 
 [    0.690529] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000 
 [    0.754161] usb usb3: configuration #1 chosen from 1 choice 
 [    0.754197] hub 3-0:1.0: USB hub found 
 [    0.754215] hub 3-0:1.0: 3 ports detected 
 [    0.754360] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    0.754387] ohci_hcd 0000:00:12.1: OHCI Host Controller 
 [    0.754446] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4 
 [    0.754480] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000 
 [    0.814152] usb usb4: configuration #1 chosen from 1 choice 
 [    0.814189] hub 4-0:1.0: USB hub found 
 [    0.814206] hub 4-0:1.0: 3 ports detected 
 [    0.814356] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
 [    0.814383] ohci_hcd 0000:00:13.0: OHCI Host Controller 
 [    0.814443] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5 
 [    0.814489] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000 
 [    0.874173] usb usb5: configuration #1 chosen from 1 choice 
 [    0.874210] hub 5-0:1.0: USB hub found 
 [    0.874227] hub 5-0:1.0: 3 ports detected 
 [    0.874374] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
 [    0.874406] ohci_hcd 0000:00:13.1: OHCI Host Controller 
 [    0.874477] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6 
 [    0.874512] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7fb000 
 [    0.934164] usb usb6: configuration #1 chosen from 1 choice 
 [    0.934202] hub 6-0:1.0: USB hub found 
 [    0.934220] hub 6-0:1.0: 3 ports detected 
 [    0.934313] uhci_hcd: USB Universal Host Controller Interface driver 
 [    0.934416] PNP: PS/2 Controller [PNP0303S2K,PNP0f03S2M] at 0x60,0x64 irq 1,12 
 [    0.960926] ACPI: Battery Slot [BAT1] (battery present) 
 [    0.960986] serio: i8042 KBD port at 0x60,0x64 irq 1 
 [    0.960995] serio: i8042 AUX port at 0x60,0x64 irq 12 
 [    0.961170] mice: PS/2 mouse device common for all mice 
 [    0.962384] rtc_cmos 00:03: RTC can wake from S4 
 [    0.962447] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
 [    0.962482] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs 
 [    0.962664] device-mapper: uevent: version 1.0.3 
 [    0.962838] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL] 
 [    0.962988] device-mapper: multipath: version 1.1.0 loaded 
 [    0.962992] device-mapper: multipath round-robin: version 1.0.0 loaded 
 [    0.963307] cpuidle: using governor ladder 
 [    0.963310] cpuidle: using governor menu 
 [    0.963802] TCP cubic registered 
 [    0.963979] NET: Registered protocol family 10 
 [    0.964664] lo: Disabled Privacy Extensions 
 [    0.965044] NET: Registered protocol family 17 
 [    0.965108] powernow-k8: Found 1 AMD Athlon(tm) Neo X2 Dual Core Processor L335 processors (2 cpu cores) (version 2.20.00) 
 [    0.965124] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found. 
 [    0.965126] [Firmware Bug]: powernow-k8: Try again with latest BIOS. 
 [    0.965271] PM: Resume from disk failed. 
 [    0.965297] registered taskstats version 1 
 [    0.965762]   Magic number: 6:138:698 
 [    0.965874] rtc_cmos 00:03: setting system clock to 2010-08-13 19:41:19 UTC (1281728479) 
 [    0.965878] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
 [    0.965880] EDD information not available. 
 [    0.965957] Freeing unused kernel memory: 880k freed 
 [    0.966491] Write protecting the kernel read-only data: 7696k 
 [    0.983630] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5 
 [    0.996212] udev: starting version 151 
 [    1.100087] usb 1-6: new high speed USB device using ehci_hcd and address 3 
 [    1.148709] scsi0 : pata_atiixp 
 [    1.168088] scsi1 : pata_atiixp 
 [    1.169918] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14 
 [    1.169923] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15 
 [    1.180077] ahci 0000:00:11.0: version 3.0 
 [    1.180103]   alloc irq_desc for 22 on node 0 
 [    1.180106]   alloc kstat_irqs on node 0 
 [    1.180116] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
 [    1.180252] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 1 ports 3 Gbps 0x1 impl SATA mode 
 [    1.180258] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc  
 [    1.182843] scsi2 : ahci 
 [    1.182955] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22 
 [    1.261760] usb 1-6: configuration #1 chosen from 1 choice 
 [    1.275058] Initializing USB Mass Storage driver... 
 [    1.275258] scsi3 : SCSI emulation for USB Mass Storage devices 
 [    1.275383] usbcore: registered new interface driver usb-storage 
 [    1.275387] USB Mass Storage support registered. 
 [    1.275395] usb-storage: device found at 3 
 [    1.275397] usb-storage: waiting for device to settle before scanning 
 [    1.380045] usb 2-3: new high speed USB device using ehci_hcd and address 2 
 [    1.640141] usb 2-3: configuration #1 chosen from 1 choice 
 [    1.720055] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
 [    1.763865] ata3.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133 
 [    1.763869] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
 [    1.766487] ata3.00: configured for UDMA/133 
 [    1.780200] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5 
 [    1.780422] sd 2:0:0:0: Attached scsi generic sg0 type 0 
 [    1.780481] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB) 
 [    1.780624] sd 2:0:0:0: [sda] Write Protect is off 
 [    1.780628] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
 [    1.780663] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
 [    1.780878]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 > 
 [    1.823274] sd 2:0:0:0: [sda] Attached SCSI disk 
 [    1.827631] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
 [    1.827668] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    1.827751] r8169 0000:03:00.0: setting latency timer to 64 
 [    1.827799]   alloc irq_desc for 28 on node 0 
 [    1.827802]   alloc kstat_irqs on node 0 
 [    1.827817] r8169 0000:03:00.0: irq 28 for MSI/MSI-X 
 [    1.829244] eth0: RTL8168d/8111d at 0xffffc9000067e000, 40:61:86:18:ba:68, XID 081000c0 IRQ 28 
 [    1.970109] usb 3-2: new full speed USB device using ohci_hcd and address 2 
 [    2.248201] usb 3-2: configuration #1 chosen from 1 choice 
 [    2.272450] EXT4-fs (sda5): INFO: recovery required on readonly filesystem 
 [    2.272457] EXT4-fs (sda5): write access will be enabled during recovery 
 [    2.952378] EXT4-fs (sda5): recovery complete 
 [    2.952966] EXT4-fs (sda5): mounted filesystem with ordered data mode 
 [    6.271185] usb-storage: device scan complete 
 [    6.273271] scsi 3:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS 
 [    6.273851] sd 3:0:0:0: Attached scsi generic sg1 type 0 
 [    6.278500] sd 3:0:0:0: [sdb] Attached SCSI removable disk 
 [   16.059090] Adding 3783268k swap on /dev/sda6.  Priority:-1 extents:1 across:3783268k  
 [   16.065339] udev: starting version 151 
 [   16.122527] lp: driver loaded but no devices found 
 [   16.220131] acpi device:04: registered as cooling_device2 
 [   16.220322] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6 
 [   16.220398] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
 [   16.378233] type=1505 audit(1281753694.904:2):  operation="profile_load" pid=495 name="/sbin/dhclient3" 
 [   16.378585] type=1505 audit(1281753694.904:3):  operation="profile_load" pid=495 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
 [   16.378782] type=1505 audit(1281753694.904:4):  operation="profile_load" pid=495 name="/usr/lib/connman/scripts/dhclient-script" 
 [   16.418682] type=1505 audit(1281753694.944:5):  operation="profile_load" pid=534 name="/usr/sbin/ntpd" 
 [   16.445207] rt3090sta: disagrees about version of symbol module_layout 
 [   16.456747] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0 
 [   16.456754] shpchp 0000:00:01.0: Cannot reserve MMIO region 
 [   16.501288] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141 
 [   16.501437] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
 [   16.520866] EDAC MC: Ver: 2.1.0 Jul  5 2010 
 [   16.551520] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0 
 [   16.554901] EDAC amd64_edac:  Ver: 3.2.0 Jul  5 2010 
 [   16.585877] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3). 
 [   16.586753] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load. 
 [   16.586755]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'. 
 [   16.586757]  (Note that use of the override may cause unknown side effects.) 
 [   16.586787] amd64_edac: probe of 0000:00:18.2 failed with error -22 
 [   16.715545] [drm] Initialized drm 1.1.0 20060810 
 [   16.723823] Bluetooth: Core ver 2.15 
 [   16.730204] NET: Registered protocol family 31 
 [   16.730208] Bluetooth: HCI device and connection manager initialized 
 [   16.730212] Bluetooth: HCI socket layer initialized 
 [   16.743990] Bluetooth: Generic Bluetooth USB driver ver 0.6 
 [   16.744271] usbcore: registered new interface driver btusb 
 [   16.764892] r8169: eth0: link down 
 [   16.765743] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   16.792255] Linux video capture interface: v2.00 
 [   16.821730] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:02c1) 
 [   16.861875] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input7 
 [   16.861960] usbcore: registered new interface driver uvcvideo 
 [   16.861964] USB Video Class driver (v0.1.0) 
 [   16.875181] Bluetooth: L2CAP ver 2.14 
 [   16.875185] Bluetooth: L2CAP socket layer initialized 
 [   16.875733] [drm] radeon defaulting to kernel modesetting. 
 [   16.875736] [drm] radeon kernel modesetting enabled. 
 [   16.884782] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
 [   16.884790] radeon 0000:01:05.0: setting latency timer to 64 
 [   16.899713] [drm] radeon: Initializing kernel modesetting. 
 [   16.912351] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 [   16.912356] Bluetooth: BNEP filters: protocol multicast 
 [   16.920100] [drm] register mmio base: 0xFE9F0000 
 [   16.920104] [drm] register mmio size: 65536 
 [   16.920947] ATOM BIOS: MS1243 
 [   16.920972] [drm] Clocks initialized ! 
 [   16.921159] [drm] Detected VRAM RAM=128M, BAR=128M 
 [   16.921165] [drm] RAM width 32bits DDR 
 [   16.937325] [TTM] Zone  kernel: Available graphics memory: 1964532 kiB. 
 [   16.937352] [drm] radeon: 128M of VRAM memory ready 
 [   16.937355] [drm] radeon: 512M of GTT memory ready. 
 [   16.937404] [drm] radeon: irq initialized. 
 [   16.937408] [drm] GART: num cpu pages 131072, num gpu pages 131072 
 [   16.938585] [drm] Loading RS780 Microcode 
 [   16.938594] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin 
 [   16.958456] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin 
 [   16.965158] Bridge firewalling registered 
 [   16.973734] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin 
 [   16.997800] Bluetooth: SCO (Voice Link) ver 0.6 
 [   16.997805] Bluetooth: SCO socket layer initialized 
 [   17.057648] [drm] ring test succeeded in 0 usecs 
 [   17.057879] [drm] radeon: ib pool ready. 
 [   17.057988] [drm] ib test succeeded in 0 usecs 
 [   17.057992] [drm] Enabling audio support 
 [   17.060179] [drm] Radeon Display Connectors 
 [   17.060183] [drm] Connector 0: 
 [   17.060185] [drm]   LVDS 
 [   17.060189] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c 
 [   17.060191] [drm]   Encoders: 
 [   17.060193] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA 
 [   17.060195] [drm] Connector 1: 
 [   17.060197] [drm]   VGA 
 [   17.060200] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c 
 [   17.060203] [drm]   Encoders: 
 [   17.060205] [drm]     CRT1: INTERNAL_KLDSCP_DAC1 
 [   17.060207] [drm] Connector 2: 
 [   17.060208] [drm]   HDMI-A 
 [   17.060211] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c 
 [   17.060214] [drm]   Encoders: 
 [   17.060216] [drm]     DFP1: INTERNAL_UNIPHY 
 [   17.110893] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   17.138322] type=1505 audit(1281753695.664:6):  operation="profile_load" pid=835 name="/usr/share/gdm/guest-session/Xsession" 
 [   17.140781] type=1505 audit(1281753695.674:7):  operation="profile_replace" pid=836 name="/sbin/dhclient3" 
 [   17.141458] type=1505 audit(1281753695.674::  operation="profile_replace" pid=836 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
 [   17.141670] type=1505 audit(1281753695.674:9):  operation="profile_replace" pid=836 name="/usr/lib/connman/scripts/dhclient-script" 
 [   17.147336] type=1505 audit(1281753695.674:10):  operation="profile_load" pid=837 name="/usr/bin/evince" 
 [   17.152352] type=1505 audit(1281753695.684:11):  operation="profile_load" pid=837 name="/usr/bin/evince-previewer" 
 [   17.198224] [drm] fb mappable at 0xF0141000 
 [   17.198228] [drm] vram apper at 0xF0000000 
 [   17.198231] [drm] size 4325376 
 [   17.198233] [drm] fb depth is 24 
 [   17.198235] [drm]    pitch is 5632 
 [   17.198383] fb0: radeondrmfb frame buffer device 
 [   17.198385] registered panic notifier 
 [   17.198392] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0 
 [   17.201262] vga16fb: initializing 
 [   17.201269] vga16fb: mapped to 0xffff8800000a0000 
 [   17.201276] vga16fb: not registering due to another framebuffer present 
 [   17.245801] Bluetooth: RFCOMM TTY layer initialized 
 [   17.245807] Bluetooth: RFCOMM socket layer initialized 
 [   17.245809] Bluetooth: RFCOMM ver 1.11 
 [   17.283939] hda_codec: ALC888: BIOS auto-probing. 
 [   17.285241] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8 
 [   17.297407] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
 [   17.297490] HDA Intel 0000:01:05.1: setting latency timer to 64 
 [   17.657996] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000 
 [   17.745909] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9 
 [   18.227071] Console: switching to colour frame buffer device 170x48 
 [   18.523704] ppdev: user-space parallel port driver 
 [   18.999460] CPU0 attaching NULL sched-domain. 
 [   18.999470] CPU1 attaching NULL sched-domain. 
 [   19.050152] CPU0 attaching sched-domain: 
 [   19.050158]  domain 0: span 0-1 level MC 
 [   19.050161]   groups: 0 1 
 [   19.050166]   domain 1: span 0-1 level CPU 
 [   19.050169]    groups: 0-1 (cpu_power = 2048) 
 [   19.050177] CPU1 attaching sched-domain: 
 [   19.050179]  domain 0: span 0-1 level MC 
 [   19.050182]   groups: 1 0 
 [   19.050186]   domain 1: span 0-1 level CPU 
 [   19.050189]    groups: 0-1 (cpu_power = 2048) 
 [   22.222329] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj. 
 [   22.670006] CPU0 attaching NULL sched-domain. 
 [   22.670017] CPU1 attaching NULL sched-domain. 
 [   22.711014] CPU0 attaching sched-domain: 
 [   22.711021]  domain 0: span 0-1 level MC 
 [   22.711024]   groups: 0 1 
 [   22.711030]   domain 1: span 0-1 level CPU 
 [   22.711032]    groups: 0-1 (cpu_power = 2048) 
 [   22.711040] CPU1 attaching sched-domain: 
 [   22.711043]  domain 0: span 0-1 level MC 
 [   22.711046]   groups: 1 0 
 [   22.711050]   domain 1: span 0-1 level CPU 
 [   22.711052]    groups: 0-1 (cpu_power = 2048) 
 [   40.269216] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.269221] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.275766] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.275770] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.515063] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.515068] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.522336] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.522341] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.546307] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.546310] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.554220] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.554224] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.577915] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.577919] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.585381] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.585385] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.609992] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.609995] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.616778] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.616782] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.642269] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.642273] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.649274] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.649277] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.674435] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.674439] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.680876] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.680879] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.706108] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.706111] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.712591] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.712594] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.738426] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.738429] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.744774] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.744777] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.770408] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.770411] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.776977] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.776980] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.802691] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.802694] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.809550] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.809553] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.833921] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.833924] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.840441] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.840444] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.865977] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.865980] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.872141] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.872144] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.897705] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.897708] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.904131] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.904134] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.929851] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.929854] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.936431] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.936434] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.961506] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.961509] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.968372] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.968375] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   40.993364] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   40.993367] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   41.000159] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   41.000162] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   41.025286] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   41.025289] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   41.032087] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   41.032090] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   41.058092] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   41.058095] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   41.064637] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   41.064640] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   46.487048] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0). 
 [   46.487054] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [   46.493541] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0). 
 [   46.493544] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known. 
 [  944.054252] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0). 
 [  944.054256] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known. 
 [  944.063242] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0). 
 [  944.063245] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known. 
 [  944.277139] CPU0 attaching NULL sched-domain. 
 [  944.277149] CPU1 attaching NULL sched-domain. 
 [  944.340970] CPU0 attaching sched-domain: 
 [  944.340977]  domain 0: span 0-1 level MC 
 [  944.340980]   groups: 0 1 
 [  944.340988] CPU1 attaching sched-domain: 
 [  944.340990]  domain 0: span 0-1 level MC 
 [  944.340993]   groups: 1 0 
 [ 1389.161805] r8169: eth0: link up 
 [ 1389.162572] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
 [ 1399.330864] eth0: no IPv6 routers present 
 [ 1912.088324] r8169: eth0: link up 
 [ 1916.339404] r8169: eth0: link up 
 [ 1917.641147] r8169: eth0: link up 
 [ 1920.428372] r8169: eth0: link up 
 [ 1921.572035] r8169: eth0: link up 
 [ 1931.750040] eth0: no IPv6 routers present 
 

 sudo lshw -C network 

   *-network UNCLAIMED      
        description: Network controller 
        product: RT3090 Wireless 802.11n 1T/1R PCIe 
        vendor: RaLink 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        version: 00 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: memory:feaf0000-feafffff 
   *-network 
        description: Ethernet interface 
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: eth0 
        version: 03 
        serial: 40:61:86:18:ba:68 
        size: 100MB/s 
        capacity: 1GB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.15 latency=0 link=yes multicast=yes port=MII speed=100MB/s 
        resources: irq:28 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable) 
 

 iwlist scan lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 pan0      Interface doesn't support scanning. 
 

 iwlist scan wlan0 iwlist: unknown command `wlan0' (check 'iwlist –help'). 
 

 uname -mr 2.6.32-24-generic x86_64
 

 sudo /etc/init.d/networking restart  * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by atpat on 2010-10-01
Same problem: was fine until the kernel upgrade that came out the other day.  I followed the very clear instructions at [http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/), using the most up-to-date versions of the files to which it refers.  This got the adapter working, but it now tries for about 5 minutes to connect and then gives up.  All the wireless networks around here are listed successfully, including mine, and yes, my WEP code is correct and yes, I know WEP isn't very secure but it is the only protocol with which all the devices I need to connect to my network are compatible and anyway I trust my neighbours not to steal my internets (I've met them, I don't think any of them would know how anyway).

Sooo, how come the update has broken the wireless (AGAIN - how many times has this happened to us??) and does anyone have a fix yet?

---

### Post by SeijiSensei on 2010-10-01
There have been problems with the Ralink driver code for a few kernel versions now.  I gave up on Lucid and went to Maverick for this reason.  It too had some regressions along the way, but the current Maverick kernel, 2.6.35-22 is the first one to work smoothly with my rt2500usb device since Ubuntu 9.10.  

Maybe some kind person who knows more about things like the backports repositories can help with installing this kernel into Lucid, or you could try the latest Maverick daily.  Other than the Ralink issue, it's been working fine for me.

Ubuntu:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Kubuntu:
[http://cdimage.ubuntu.com/kubuntu/daily-live/](http://cdimage.ubuntu.com/kubuntu/daily-live/)

---

### Post by desnaike on 2010-10-01
Yes the kernal update breaks the driver I simply uninstalled the driver with synaptic and reinstalled it using the deb file worked for me.

---

