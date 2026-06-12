---
title: "Wireless DELL M1330 - Ubuntu 11"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Gian- on 2011-05-16
Hi,
I'm new to Ubuntu. I'm trying to utilize airmon-ng but I can not detect my wlan. I can access the web.


Thank you,



gianmario@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)  
 00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)  
 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)  
 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)  
 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)  
 00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)  
 00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)  
 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)  
 00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)  
 01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)  
 03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)  
 03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)  
 03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)  
 03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)  
 09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)  
 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)  
 

 gianmario@ubuntu:~$ lsusb
 Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 002: ID 413c:8133 Dell Computer Corp. Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) Minicard GPS Port
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp.  
 Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
 Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
 Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 gianmario@ubuntu:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:15:c5:81:fa:5f   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17  
 

 eth1      Link encap:Ethernet  HWaddr 00:22:5f:1b:a6:bf   
           inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::222:5fff:fe1b:a6bf/64 Scope:Link  
           UP BROADCAST RUNNING  MTU:1500  Metric:1  
           RX packets:3400 errors:0 dropped:0 overruns:0 frame:305  
           TX packets:3306 errors:18 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:3333035 (3.3 MB)  TX bytes:521941 (521.9 KB)  
           Interrupt:17 Base address:0xc000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:16 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)  
 

 gianmario@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 eth1      IEEE 802.11  Access Point: Not-Associated    
           Link Quality:5  Signal level:212  Noise level:199  
           Rx invalid nwid:0  invalid crypt:0  invalid misc:0  
 

 gianmario@ubuntu:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12713  1  
 nls_cp437              16991  1  
 vfat                   21708  1  
 fat                    61374  1 vfat  
 rfcomm                 47694  8  
 binfmt_misc            17565  1  
 sco                    18131  2  
 bnep                   18308  2  
 l2cap                  53570  16 rfcomm,bnep  
 parport_pc             36959  0  
 ppdev                  17113  0  
 nvidia              10709116  44  
 lib80211_crypt_tkip    17387  0  
 snd_hda_codec_idt      71137  1  
 joydev                 17606  0  
 wl                   2568244  0  
 snd_hda_intel          33211  2  
 snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13604  1 snd_hda_codec  
 snd_pcm                96625  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13324  0  
 usbhid                 46956  0  
 snd_rawmidi            30486  1 snd_seq_midi  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event  
 hid                    91020  1 usbhid  
 sierra                 18384  0  
 option                 25285  0  
 usb_wwan               20407  1 option  
 dell_wmi               12681  0  
 sparse_keymap          13898  1 dell_wmi  
 snd_timer              29602  2 snd_pcm,snd_seq  
 uvcvideo               72195  0  
 usbserial              42908  3 sierra,option,usb_wwan  
 dell_laptop            13827  0  
 r852                   18246  0  
 btusb                  18600  2  
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq  
 dcdbas                 14438  1 dell_laptop  
 videodev               82052  1 uvcvideo  
 sm_common              16817  1 r852  
 v4l2_compat_ioctl32    17078  1 videodev  
 nand                   55112  2 r852,sm_common  
 bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb  
 nand_ids               12723  1 nand  
 nand_ecc               13230  1 nand  
 psmouse                73535  0  
 video                  19438  0  
 mtd                    27900  2 sm_common,nand  
 snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 lib80211               14991  2 lib80211_crypt_tkip,wl  
 serio_raw              13166  0  
 soundcore              12680  1 snd  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 lp                     17825  0  
 parport                46458  3 parport_pc,ppdev,lp  
 mmc_block              18053  1  
 sdhci_pci              13989  0  
 tg3                   141750  0  
 firewire_ohci          40370  0  
 sdhci                  27387  1 sdhci_pci  
 firewire_core          62646  1 firewire_ohci  
 crc_itu_t              12707  1 firewire_core  
 

 gianmario@ubuntu:~$ dmesg
 [    0.556286] pnp 00:0b: disabling [mem 0xdff00000-0xe06fffff] because it overlaps 0000:00:01.0 BAR 15 [mem 0xe0000000-0xefffffff 64bit pref]  
 [    0.556308] pnp 00:0b: disabling [mem 0xdff00000-0xe06fffff disabled] because it overlaps 0000:01:00.0 BAR 1 [mem 0xe0000000-0xefffffff 64bit pref]  
 [    0.556365] system 00:0b: [mem 0x00000000-0x0009efff] could not be reserved  
 [    0.556368] system 00:0b: [mem 0x0009f000-0x0009ffff] could not be reserved  
 [    0.556371] system 00:0b: [mem 0x000c0000-0x000cffff] has been reserved  
 [    0.556373] system 00:0b: [mem 0x000e0000-0x000fffff] has been reserved  
 [    0.556375] system 00:0b: [mem 0x00100000-0xdfe6d7ff] could not be reserved  
 [    0.556377] system 00:0b: [mem 0xdfe6d800-0xdfefffff] has been reserved  
 [    0.556380] system 00:0b: [mem 0xdff00000-0xdfffffff] has been reserved  
 [    0.556382] system 00:0b: [mem 0xffe00000-0xffffffff] has been reserved  
 [    0.556384] system 00:0b: [mem 0xffa00000-0xffbfffff] has been reserved  
 [    0.556387] system 00:0b: [mem 0xfec00000-0xfec0ffff] could not be reserved  
 [    0.556389] system 00:0b: [mem 0xfee00000-0xfee0ffff] has been reserved  
 [    0.556391] system 00:0b: [mem 0xfed20000-0xfed8ffff] has been reserved  
 [    0.556393] system 00:0b: [mem 0xfeda0000-0xfeda3fff] has been reserved  
 [    0.556396] system 00:0b: [mem 0xfeda4000-0xfeda4fff] has been reserved  
 [    0.556398] system 00:0b: [mem 0xfeda5000-0xfeda5fff] has been reserved  
 [    0.556400] system 00:0b: [mem 0xfeda6000-0xfeda6fff] has been reserved  
 [    0.556402] system 00:0b: [mem 0xfed18000-0xfed1bfff] has been reserved  
 [    0.556405] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved  
 [    0.556408] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)  
 [    0.556457] pnp: PnP ACPI: found 12 devices  
 [    0.556459] ACPI: ACPI bus type pnp unregistered  
 [    0.562645] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0200000-0xf03fffff]  
 [    0.562649] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]  
 [    0.562653] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]  
 [    0.562656] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf0800000-0xf09fffff 64bit pref]  
 [    0.562660] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]  
 [    0.562662] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]  
 [    0.562664] pci 0000:00:1c.5: BAR 13: assigned [io  0x4000-0x4fff]  
 [    0.562667] pci 0000:01:00.0: BAR 6: assigned [mem 0xf4000000-0xf401ffff pref]  
 [    0.562670] pci 0000:00:01.0: PCI bridge to [bus 01-01]  
 [    0.562673] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]  
 [    0.562676] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf6efffff]  
 [    0.562679] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]  
 [    0.562683] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]  
 [    0.562686] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]  
 [    0.562693] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff]  
 [    0.562697] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]  
 [    0.562705] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]  
 [    0.562708] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]  
 [    0.562714] pci 0000:00:1c.1:   bridge window [mem 0xf1f00000-0xf1ffffff]  
 [    0.562719] pci 0000:00:1c.1:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]  
 [    0.562727] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]  
 [    0.562730] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]  
 [    0.562736] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf1efffff]  
 [    0.562741] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]  
 [    0.562748] pci 0000:00:1c.5: PCI bridge to [bus 09-09]  
 [    0.562752] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]  
 [    0.562758] pci 0000:00:1c.5:   bridge window [mem 0xf1b00000-0xf1bfffff]  
 [    0.562762] pci 0000:00:1c.5:   bridge window [mem 0xf0800000-0xf09fffff 64bit pref]  
 [    0.562770] pci 0000:00:1e.0: PCI bridge to [bus 03-03]  
 [    0.562772] pci 0000:00:1e.0:   bridge window [io  disabled]  
 [    0.562778] pci 0000:00:1e.0:   bridge window [mem 0xf1a00000-0xf1afffff]  
 [    0.562783] pci 0000:00:1e.0:   bridge window [mem pref disabled]  
 [    0.562806] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.562810] pci 0000:00:01.0: setting latency timer to 64  
 [    0.562817] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.562821] pci 0000:00:1c.0: setting latency timer to 64  
 [    0.562831] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.562836] pci 0000:00:1c.1: setting latency timer to 64  
 [    0.562845] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19  
 [    0.562850] pci 0000:00:1c.3: setting latency timer to 64  
 [    0.562857] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.562862] pci 0000:00:1c.5: setting latency timer to 64  
 [    0.562870] pci 0000:00:1e.0: setting latency timer to 64  
 [    0.562874] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]  
 [    0.562876] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]  
 [    0.562878] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]  
 [    0.562880] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]  
 [    0.562882] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xf7ffffff]  
 [    0.562884] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]  
 [    0.562886] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]  
 [    0.562888] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]  
 [    0.562890] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]  
 [    0.562892] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]  
 [    0.562893] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]  
 [    0.562895] pci_bus 0000:00: resource 15 [mem 0xffc00000-0xffdfffff]  
 [    0.562897] pci_bus 0000:00: resource 16 [mem 0x220000000-0x417ffffff]  
 [    0.562900] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]  
 [    0.562902] pci_bus 0000:01: resource 1 [mem 0xf2000000-0xf6efffff]  
 [    0.562904] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]  
 [    0.562906] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]  
 [    0.562908] pci_bus 0000:0b: resource 1 [mem 0xf0200000-0xf03fffff]  
 [    0.562910] pci_bus 0000:0b: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]  
 [    0.562912] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]  
 [    0.562914] pci_bus 0000:0c: resource 1 [mem 0xf1f00000-0xf1ffffff]  
 [    0.562916] pci_bus 0000:0c: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]  
 [    0.562918] pci_bus 0000:0d: resource 0 [io  0xc000-0xcfff]  
 [    0.562920] pci_bus 0000:0d: resource 1 [mem 0xf1c00000-0xf1efffff]  
 [    0.562922] pci_bus 0000:0d: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]  
 [    0.562924] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]  
 [    0.562926] pci_bus 0000:09: resource 1 [mem 0xf1b00000-0xf1bfffff]  
 [    0.562928] pci_bus 0000:09: resource 2 [mem 0xf0800000-0xf09fffff 64bit pref]  
 [    0.562930] pci_bus 0000:03: resource 1 [mem 0xf1a00000-0xf1afffff]  
 [    0.562932] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]  
 [    0.562934] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]  
 [    0.562936] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]  
 [    0.562938] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]  
 [    0.562940] pci_bus 0000:03: resource 8 [mem 0xe0000000-0xf7ffffff]  
 [    0.562942] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]  
 [    0.562944] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]  
 [    0.562946] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]  
 [    0.562948] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]  
 [    0.562950] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]  
 [    0.562951] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]  
 [    0.562953] pci_bus 0000:03: resource 15 [mem 0xffc00000-0xffdfffff]  
 [    0.562955] pci_bus 0000:03: resource 16 [mem 0x220000000-0x417ffffff]  
 [    0.562993] NET: Registered protocol family 2  
 [    0.563221] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)  
 [    0.564922] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)  
 [    0.569490] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)  
 [    0.570166] TCP: Hash tables configured (established 524288 bind 65536)  
 [    0.570169] TCP reno registered  
 [    0.570187] UDP hash table entries: 4096 (order: 5, 131072 bytes)  
 [    0.570291] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)  
 [    0.570472] NET: Registered protocol family 1  
 [    0.570695] pci 0000:01:00.0: Boot video device  
 [    0.570907] PCI: CLS 64 bytes, default 64  
 [    0.570910] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)  
 [    0.570912] Placing 64MB software IO TLB between ffff8800dbc00000 - ffff8800dfc00000  
 [    0.570914] software IO TLB at phys 0xdbc00000 - 0xdfc00000  
 [    0.570952] Simple Boot Flag at 0x79 set to 0x1  
 [    0.571270] audit: initializing netlink socket (disabled)  
 [    0.571285] type=2000 audit(1305573101.570:1): initialized  
 [    0.574716] Freeing initrd memory: 12832k freed  
 [    0.583295] HugeTLB registered 2 MB page size, pre-allocated 0 pages  
 [    0.584939] VFS: Disk quotas dquot_6.5.2  
 [    0.584990] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)  
 [    0.585583] fuse init (API version 7.16)  
 [    0.585662] msgmni has been set to 15996  
 [    0.585923] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)  
 [    0.585953] io scheduler noop registered  
 [    0.585955] io scheduler deadline registered  
 [    0.585994] io scheduler cfq registered (default)  
 [    0.586104] pcieport 0000:00:01.0: setting latency timer to 64  
 [    0.586140] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X  
 [    0.586190] pcieport 0000:00:1c.0: setting latency timer to 64  
 [    0.586243] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X  
 [    0.586319] pcieport 0000:00:1c.1: setting latency timer to 64  
 [    0.586372] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X  
 [    0.586452] pcieport 0000:00:1c.3: setting latency timer to 64  
 [    0.586505] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X  
 [    0.586580] pcieport 0000:00:1c.5: setting latency timer to 64  
 [    0.586633] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X  
 [    0.586728] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.586748] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.586789] intel_idle: MWAIT substates: 0x3122220  
 [    0.586791] intel_idle: does not run on family 6 model 23  
 [    0.586893] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    0.586935] ACPI: AC Adapter [AC] (on-line)  
 [    0.587044] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0  
 [    0.630020] ACPI: Lid Switch [LID]  
 [    0.630063] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1  
 [    0.700028] ACPI: Power Button [PBTN]  
 [    0.700071] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2  
 [    0.700075] ACPI: Sleep Button [SBTN]  
 [    0.700249] ACPI: acpi_idle registered with cpuidle  
 [    0.700362] Monitor-Mwait will be used to enter C-1 state  
 [    0.700391] Monitor-Mwait will be used to enter C-2 state  
 [    0.700421] Monitor-Mwait will be used to enter C-3 state  
 [    0.700428] Marking TSC unstable due to TSC halts in idle  
 [    0.705388] thermal LNXTHERM:00: registered as thermal_zone0  
 [    0.705390] ACPI: Thermal Zone [THM] (47 C)  
 [    0.705414] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    0.705457] ERST: Table is not found!  
 [    0.705658] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled  
 [    0.726591] ACPI: Battery Slot [BAT0] (battery present)  
 [    1.030295] Linux agpgart interface v0.103  
 [    1.031449] brd: module loaded  
 [    1.031937] loop: module loaded  
 [    1.032007] i2c-core: driver [adp5520] using legacy suspend method  
 [    1.032008] i2c-core: driver [adp5520] using legacy resume method  
 [    1.032078] ata_piix 0000:00:1f.1: version 2.13  
 [    1.032089] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    1.032130] ata_piix 0000:00:1f.1: setting latency timer to 64  
 [    1.032426] scsi0 : ata_piix  
 [    1.032507] scsi1 : ata_piix  
 [    1.032774] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14  
 [    1.032776] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15  
 [    1.032793] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    1.032799] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]  
 [    1.032845] ata2: port disabled. ignoring.  
 [    1.190252] ata_piix 0000:00:1f.2: setting latency timer to 64  
 [    1.190517] scsi2 : ata_piix  
 [    1.190586] scsi3 : ata_piix  
 [    1.190849] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17  
 [    1.190856] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17  
 [    1.191145] Fixed MDIO Bus: probed  
 [    1.191170] PPP generic driver version 2.4.2  
 [    1.191205] tun: Universal TUN/TAP device driver, 1.6  
 [    1.191207] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>  
 [    1.191275] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    1.191297] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22  
 [    1.191314] ehci_hcd 0000:00:1a.7: setting latency timer to 64  
 [    1.191317] ehci_hcd 0000:00:1a.7: EHCI Host Controller  
 [    1.191347] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1  
 [    1.191428] ehci_hcd 0000:00:1a.7: debug port 1  
 [    1.195313] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported  
 [    1.195325] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400  
 [    1.210029] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00  
 [    1.210134] hub 1-0:1.0: USB hub found  
 [    1.210138] hub 1-0:1.0: 4 ports detected  
 [    1.210231] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    1.210250] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    1.210258] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    1.210289] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2  
 [    1.210535] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-857G, Z111, max UDMA/33  
 [    1.210742] ehci_hcd 0000:00:1d.7: debug port 1  
 [    1.214630] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported  
 [    1.214644] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000  
 [    1.230022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    1.230133] hub 2-0:1.0: USB hub found  
 [    1.230137] hub 2-0:1.0: 6 ports detected  
 [    1.230210] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    1.230221] uhci_hcd: USB Universal Host Controller Interface driver  
 [    1.230262] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    1.230268] uhci_hcd 0000:00:1a.0: setting latency timer to 64  
 [    1.230272] uhci_hcd 0000:00:1a.0: UHCI Host Controller  
 [    1.230301] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3  
 [    1.230350] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20  
 [    1.230463] hub 3-0:1.0: USB hub found  
 [    1.230467] hub 3-0:1.0: 2 ports detected  
 [    1.230535] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  
 [    1.230541] uhci_hcd 0000:00:1a.1: setting latency timer to 64  
 [    1.230544] uhci_hcd 0000:00:1a.1: UHCI Host Controller  
 [    1.230574] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4  
 [    1.230628] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00  
 [    1.230741] hub 4-0:1.0: USB hub found  
 [    1.230745] hub 4-0:1.0: 2 ports detected  
 [    1.230810] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    1.230817] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    1.230820] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    1.230854] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5  
 [    1.230899] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80  
 [    1.231006] hub 5-0:1.0: USB hub found  
 [    1.231010] hub 5-0:1.0: 2 ports detected  
 [    1.231073] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  
 [    1.231079] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    1.231082] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    1.231115] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6  
 [    1.231160] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60  
 [    1.231263] hub 6-0:1.0: USB hub found  
 [    1.231267] hub 6-0:1.0: 2 ports detected  
 [    1.231329] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22  
 [    1.231336] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    1.231339] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    1.231372] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7  
 [    1.231417] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40  
 [    1.231527] hub 7-0:1.0: USB hub found  
 [    1.231531] hub 7-0:1.0: 2 ports detected  
 [    1.231635] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12  
 [    1.234378] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    1.234384] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    1.234503] mousedev: PS/2 mouse device common for all mice  
 [    1.234634] rtc_cmos 00:03: RTC can wake from S4  
 [    1.234696] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0  
 [    1.234727] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs  
 [    1.234807] device-mapper: uevent: version 1.0.3  
 [    1.234873] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]  
 [    1.234929] device-mapper: multipath: version 1.2.0 loaded  
 [    1.234932] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    1.235098] cpuidle: using governor ladder  
 [    1.235175] cpuidle: using governor menu  
 [    1.235375] TCP cubic registered  
 [    1.235478] NET: Registered protocol family 10  
 [    1.235899] NET: Registered protocol family 17  
 [    1.235911] Registering the dns_resolver key type  
 [    1.236870] PM: Hibernation image not present or could not be loaded.  
 [    1.236882] registered taskstats version 1  
 [    1.237563]   Magic number: 11:826:192  
 [    1.237618] acpi device:1e: hash matches  
 [    1.237684] rtc_cmos 00:03: setting system clock to 2011-05-16 19:11:42 UTC (1305573102)  
 [    1.237686] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    1.237688] EDD information not available.  
 [    1.238368] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3  
 [    1.250624] ata1.00: configured for UDMA/33  
 [    1.252761] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-857G  Z111 PQ: 0 ANSI: 5  
 [    1.255171] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy  
 [    1.255175] cdrom: Uniform CD-ROM driver Revision: 3.20  
 [    1.255316] sr 0:0:0:0: Attached scsi CD-ROM sr0  
 [    1.255362] sr 0:0:0:0: Attached scsi generic sg0 type 5  
 [    1.930228] usb 3-2: new full speed USB device using uhci_hcd and address 2  
 [    2.050291] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  
 [    2.050313] ata3.01: SATA link down (SStatus 0 SControl 300)  
 [    2.070417] ata3.00: ATA-8: ST9250827AS, 3.ADB, max UDMA/133  
 [    2.070419] ata3.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 0/32)  
 [    2.110427] ata3.00: configured for UDMA/133  
 [    2.110504] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AD PQ: 0 ANSI: 5  
 [    2.110624] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)  
 [    2.110628] sd 2:0:0:0: Attached scsi generic sg1 type 0  
 [    2.110683] sd 2:0:0:0: [sda] Write Protect is off  
 [    2.110686] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    2.110746] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    2.112474] hub 3-2:1.0: USB hub found  
 [    2.114425] hub 3-2:1.0: 3 ports detected  
 [    2.181740]  sda: sda1 sda2 sda3 sda4 < sda5 >  
 [    2.182258] sd 2:0:0:0: [sda] Attached SCSI disk  
 [    2.350229] usb 2-6: new high speed USB device using ehci_hcd and address 3  
 [    2.610254] ata4.01: failed to resume link (SControl 0)  
 [    2.610310] ata4.00: SATA link down (SStatus 0 SControl 300)  
 [    2.610335] ata4.01: SATA link down (SStatus 0 SControl 0)  
 [    2.611893] Freeing unused kernel memory: 956k freed  
 [    2.612274] Write protecting the kernel read-only data: 10240k  
 [    2.613008] Freeing unused kernel memory: 184k freed  
 [    2.617326] Freeing unused kernel memory: 1444k freed  
 [    2.633756] <30>udev[78]: starting version 167  
 [    2.726835] sdhci: Secure Digital Host Controller Interface driver  
 [    2.726838] sdhci: Copyright(c) Pierre Ossman  
 [    2.727874] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19  
 [    2.732046] tg3.c:v3.116 (December 3, 2010)  
 [    2.732065] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [    2.732079] tg3 0000:09:00.0: setting latency timer to 64  
 [    2.790090] usb 4-2: new full speed USB device using uhci_hcd and address 2  
 [    2.800186] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1  
 [    2.800276] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)  
 [    2.800298] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18  
 [    2.801351] mmc0: no vmmc regulator found  
 [    2.802382] Registered led device: mmc0::  
 [    2.803423] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA  
 [    2.879209] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:15:c5:81:fa:5f  
 [    2.879212] tg3 0000:09:00.0: eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])  
 [    2.879215] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]  
 [    2.879217] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]  
 [    2.914137] mmc0: new high speed SD card at address c106  
 [    2.916947] mmcblk0: mmc0:c106 SD01G 947 MiB  
 [    2.917622]  mmcblk0:  
 [    3.240060] usb 7-1: new full speed USB device using uhci_hcd and address 2  
 [    3.300185] firewire_core: created device fw0: GUID 464fc00007d0c1e1, S400  
 [    3.511432] usb 3-2.1: new full speed USB device using uhci_hcd and address 3  
 [    3.532358] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)  
 [    3.731431] usb 3-2.2: new full speed USB device using uhci_hcd and address 4  
 [    3.951435] usb 3-2.3: new full speed USB device using uhci_hcd and address 5  
 [   17.563583] <30>udev[321]: starting version 167  
 [   17.671066] lp: driver loaded but no devices found  
 [   17.725854] lib80211: common routines for IEEE802.11 drivers  
 [   17.725857] lib80211_crypt: registered algorithm 'NULL'  
 [   17.846755] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)  
 [   17.853956] Bluetooth: Core ver 2.15 
 [   17.857579] NET: Registered protocol family 31  
 [   17.857581] Bluetooth: HCI device and connection manager initialized  
 [   17.857584] Bluetooth: HCI socket layer initialized  
 [   17.861331] Bluetooth: Generic Bluetooth USB driver ver 0.6  
 [   17.869793] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18  
 [   17.871847] Linux video capture interface: v2.00  
 [   17.879607] usbcore: registered new interface driver btusb  
 [   17.880591] r852: driver loaded succesfully  
 [   17.925602] usbcore: registered new interface driver usbserial  
 [   17.925613] USB Serial support registered for generic  
 [   17.925680] usbcore: registered new interface driver usbserial_generic  
 [   17.925682] usbserial: USB Serial Driver core  
 [   18.236500] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)  
 [   18.237307] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.  
 [   18.241689] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input4  
 [   18.241799] usbcore: registered new interface driver uvcvideo  
 [   18.241801] USB Video Class driver (v1.0.0)  
 [   18.244238] input: Dell WMI hotkeys as /devices/virtual/input/input5  
 [   18.267168] USB Serial support registered for GSM modem (1-port)  
 [   18.267240] option 4-2:1.0: GSM modem (1-port) converter detected  
 [   18.267344] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0  
 [   18.267359] option 4-2:1.1: GSM modem (1-port) converter detected  
 [   18.267416] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1  
 [   18.267462] usbcore: registered new interface driver option  
 [   18.267464] option: v0.7.2:USB Driver for GSM modems  
 [   18.273111] USB Serial support registered for Sierra USB modem  
 [   18.273158] usbcore: registered new interface driver sierra  
 [   18.273159] sierra: v.1.7.16:USB Driver for Sierra Wireless USB modems  
 [   18.323549] acpi device:31: registered as cooling_device2  
 [   18.329513] type=1400 audit(1305565919.576:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=576 comm="apparmor_parser"  
 [   18.330482] type=1400 audit(1305565919.586:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=576 comm="apparmor_parser"  
 [   18.330969] type=1400 audit(1305565919.586:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=576 comm="apparmor_parser"  
 [   18.332407] type=1400 audit(1305565919.586:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=592 comm="apparmor_parser"  
 [   18.333175] type=1400 audit(1305565919.586:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=592 comm="apparmor_parser"  
 [   18.333660] type=1400 audit(1305565919.586:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=592 comm="apparmor_parser"  
 [   18.365021] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input6 
 [   18.365386] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)  
 [   18.365444] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.  
 [   18.393525] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input7 
 [   18.394264] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0  
 [   18.399752] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input8 
 [   18.399993] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0  
 [   18.400068] usbcore: registered new interface driver usbhid  
 [   18.400071] usbhid: USB HID core driver  
 [   18.414707] wl: module license 'MIXED/Proprietary' taints kernel.  
 [   18.414710] Disabling lock debugging due to kernel taint  
 [   18.422919] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21  
 [   18.422989] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X  
 [   18.423019] HDA Intel 0000:00:1b.0: setting latency timer to 64  
 [   18.425453] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   18.425466] wl 0000:0c:00.0: setting latency timer to 64  
 [   18.455693] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0  
 [   18.491129] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9  
 [   18.554683] lib80211_crypt: registered algorithm 'TKIP'  
 [   18.870678] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38  
 [   19.060298] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10  
 [   19.060445] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11  
 [   19.060567] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12  
 [   20.436555] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k  
 [   20.503655] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro  
 [   20.519971] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   20.519981] nvidia 0000:01:00.0: setting latency timer to 64  
 [   20.520022] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem  
 [   20.520238] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011  
 [   20.806781] type=1400 audit(1305565922.056:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=819 comm="apparmor_parser"  
 [   20.808360] type=1400 audit(1305565922.056:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=818 comm="apparmor_parser"  
 [   20.810354] type=1400 audit(1305565922.066:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=819 comm="apparmor_parser"  
 [   20.810843] type=1400 audit(1305565922.066:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"  
 [   20.871069] ppdev: user-space parallel port driver  
 [   20.966022] tg3 0000:09:00.0: irq 46 for MSI/MSI-X  
 [   21.003055] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   21.069548] Bluetooth: L2CAP ver 2.15  
 [   21.069551] Bluetooth: L2CAP socket layer initialized  
 [   21.076596] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   21.076599] Bluetooth: BNEP filters: protocol multicast  
 [   21.080572] Bluetooth: SCO (Voice Link) ver 0.6  
 [   21.080574] Bluetooth: SCO socket layer initialized  
 [   21.146011] Bluetooth: RFCOMM TTY layer initialized  
 [   21.146016] Bluetooth: RFCOMM socket layer initialized  
 [   21.146017] Bluetooth: RFCOMM ver 1.11  
 [   21.731811] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0  
 [   26.019463] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0  
 [   31.320017] eth1: no IPv6 routers present  
 [   43.450264] CE: hpet increased min_delta_ns to 20113 nsec  
 [   71.010437] CE: hpet increased min_delta_ns to 30169 nsec  
 [  331.360146] eth1: no IPv6 routers present  
 

 gianmario@ubuntu:~$ gianmario@ubuntu:~$ sudo lshw -C network  
 [sudo] password for gianmario:  
   *-network                
        description: Wireless interface  
        product: BCM4312 802.11b/g LP-PHY  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:0c:00.0  
        logical name: eth1  
        version: 01  
        serial: 00:22:5f:1b:a6:bf  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.34 latency=0 wireless=IEEE 802.11bg  
        resources: irq:17 memory:f1ffc000-f1ffffff  
   *-network  
        description: Ethernet interface  
        product: NetLink BCM5906M Fast Ethernet PCI Express  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:09:00.0  
        logical name: eth0  
        version: 02  
        serial: 00:15:c5:81:fa:5f  
        capacity: 100Mbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:46 memory:f1bf0000-f1bfffff  
 

 gianmario@ubuntu:~$ iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 eth1      Interface doesn't support scanning.  
 

 gianmario@ubuntu:~$ lsb_release -d  
 Description:	Ubuntu 11.04  
 

 gianmario@ubuntu:~$ uname -mr  
 2.6.38-8-generic x86_64  
 

 gianmario@ubuntu:~$ sudo /etc/init.d/networking restart  
 [sudo] password for gianmario:  
  * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
  * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.  
                                                                          [ OK ]  
 gianmario@ubuntu:~$

---

### Post by chili555 on 2011-05-16
Does this help?> -network
description: [COLOR="Red"]Wireless interface[/COLOR]
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: [COLOR="Red"]eth1[/COLOR]
version: 01
serial: 00:22:5f:1b:a6:bf
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.34 latency=0 wireless=IEEE 802.11bg
resources: irq:17 memory:f1ffc000-f1ffffff Not all wireless interfaces are called wlan0 or even wlan-something. Yours, and coincidentally mine, are called eth1.

---

### Post by Gian- on 2011-05-17
Hi Chili555

It did help, thank you :)

The command sets the driver on monitor mode however is not recognizing the Chipset, is it OK?

thanks again for your feedback,



gianmario@ubuntu:~$ sudo airmon-ng start eth1
[sudo] password for gianmario: 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
981    avahi-daemon
982    avahi-daemon
985    NetworkManager
1148    wpa_supplicant
1528    dhclient
Process with PID 1528 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        [COLOR=Red]Unknown [/COLOR]        wl (monitor mode enabled)

---

### Post by chili555 on 2011-05-17
I don't know hardly a thing about aircrack. I just know interfaces. Sorry.

---

### Post by Gian- on 2011-05-17
I guess the problem is with my wireless interface. I'm using a BCM4312 802.11b/g LP-PHY from Broadcom Corporation 

                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:5f:1b:a6:bf
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless

I mange to start the monitor mode

root@ubuntu:/home/gianmario# airmon-ng start eth1

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
839    avahi-daemon
840    avahi-daemon
841    NetworkManager
921    wpa_supplicant
3216    dhclient
Process with PID 3216 (dhclient) is running on interface eth1

Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

however when I try to proceed with the next steps I get the following message:

root@ubuntu:/home/gianmario# airodump-ng -c 6  eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

Is anybody familiar with Aircarck and the BCM4312?

Thanks,

---

