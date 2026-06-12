---
title: "amilo Pa 2510 wireless problems."
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by big-t on 2008-12-30
hello, i just installed ubuntu on my amilo Pa 2510 computer.

everything was great, just that my wireless card don't work.
i did search on the net, and i got nothing :/
i need wireless at my school....

can someone plz help me :D?

(and yes, i did search, dont flame me, i am not the best at computers :P)

---

### Post by teaker1s on 2008-12-30
[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")
follow instructions and post output

---

### Post by big-t on 2008-12-30
here you go

aina@aina-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
00:04.0 PCI bridge: ATI Technologies Inc Device 7914 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01) 
aina@aina-laptop:~$ 


aina@aina-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
00:04.0 PCI bridge: ATI Technologies Inc Device 7914 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01) 
aina@aina-laptop:~$ 



aina@aina-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
00:04.0 PCI bridge: ATI Technologies Inc Device 7914 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01) 
aina@aina-laptop:~$ 

aina@aina-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
00:04.0 PCI bridge: ATI Technologies Inc Device 7914 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01) 
aina@aina-laptop:~$ 


aina@aina-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 



aina@aina-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 




aina@aina-laptop:~$ lsmod 
Module                  Size  Used by 
ipv6                  263972  10 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep 
bluetooth              61924  6 rfcomm,bnep,sco,l2cap 
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats 
sbs                    19464  0 
container              11520  0 
pci_slot               12552  0 
wmi                    14504  0 
sbshc                  13440  1 sbs 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter 
x_tables               22916  1 ip_tables 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp 
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
evdev                  17696  10 
psmouse                45200  0 
serio_raw              13444  0 
pcspkr                 10624  0 
i2c_piix4              16144  0 
k8temp                 12416  0 
snd_timer              29960  2 snd_pcm,snd_seq 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
i2c_core               31892  1 i2c_piix4 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15328  1 snd 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm 
ath_pci                99096  0 
wlan                  211952  1 ath_pci 
ath_hal               198864  1 ath_pci 
video                  25104  0 
output                 11008  1 video 
ac                     12292  0 
battery                18436  0 
button                 14224  0 
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp 
ext3                  133256  1 
jbd                    55444  1 ext3 
mbcache                16004  1 ext3 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod 
sg                     39732  0 
pata_atiixp            12800  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ahci                   37132  2 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
libata                177312  4 pata_atiixp,pata_acpi,ata_generic,ahci 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata 
dock                   16656  1 libata 
usbcore               148848  3 ehci_hcd,ohci_hcd 
r8169                  35972  0 
thermal                23708  0 
processor              42156  3 powernow_k8,thermal 
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon 
font                   16512  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 
fuse                   60828  3 
aina@aina-laptop:~$ 



aina@aina-laptop:~$ lsmod grep "wlan_module_name" 
Usage: lsmod 

[    3.919828] EISA: Detected 0 cards. 
[    3.919832] cpuidle: using governor ladder 
[    3.919834] cpuidle: using governor menu 
[    3.920401] TCP cubic registered 
[    3.920430] Using IPI No-Shortcut mode 
[    3.920694] registered taskstats version 1 
[    3.920848]   Magic number: 4:856:1004 
[    3.920862] tty ttye3: hash matches 
[    3.920978] i8042 kbd 00:06: hash matches 
[    3.921052] rtc_cmos 00:04: setting system clock to 2008-12-30 20:58:33 UTC (1230670713) 
[    3.921056] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    3.921058] EDD information not available. 
[    3.921365] Freeing unused kernel memory: 424k freed 
[    3.921440] Write protecting the kernel text: 2576k 
[    3.921485] Write protecting the kernel read-only data: 936k 
[    3.955819] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[    4.081094] fuse init (API version 7.9) 
[    4.120226] ACPI: processor limited to max C-state 1 
[    4.120403] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[    4.120473] processor ACPI0007:00: registered as cooling_device0 
[    4.120478] ACPI: Processor [CPU0] (supports 8 throttling states) 
[    4.120559] processor ACPI0007:01: registered as cooling_device1 
[    4.123789] thermal LNXTHERM:01: registered as thermal_zone0 
[    4.124829] ACPI: Thermal Zone [TZ00] (69 C) 
[    4.578913] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    4.578937] r8169 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    4.578962] r8169 0000:08:00.0: setting latency timer to 64 
[    4.579549] eth0: RTL8101e at 0xf8840000, 00:03:0d:6d:fd:52, XID 34000000 IRQ 220 
[    4.594746] usbcore: registered new interface driver usbfs 
[    4.594779] usbcore: registered new interface driver hub 
[    4.594858] No dock devices found. 
[    4.609711] usbcore: registered new device driver usb 
[    4.610183] SCSI subsystem initialized 
[    4.657454] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[    4.657704] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    4.657732] ohci_hcd 0000:00:13.0: OHCI Host Controller 
[    4.658293] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1 
[    4.658322] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000 
[    4.658361] libata version 3.00 loaded. 
[    4.712231] usb usb1: configuration #1 chosen from 1 choice 
[    4.712264] hub 1-0:1.0: USB hub found 
[    4.712281] hub 1-0:1.0: 2 ports detected 
[    4.816366] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    4.816386] ohci_hcd 0000:00:13.1: OHCI Host Controller 
[    4.816414] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2 
[    4.816443] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000 
[    4.872242] usb usb2: configuration #1 chosen from 1 choice 
[    4.872280] hub 2-0:1.0: USB hub found 
[    4.872297] hub 2-0:1.0: 2 ports detected 
[    4.976436] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    4.976455] ohci_hcd 0000:00:13.3: OHCI Host Controller 
[    4.976484] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 3 
[    4.976503] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0007000 
[    5.032247] usb usb3: configuration #1 chosen from 1 choice 
[    5.032282] hub 3-0:1.0: USB hub found 
[    5.032298] hub 3-0:1.0: 2 ports detected 
[    5.136300] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    5.136318] ohci_hcd 0000:00:13.4: OHCI Host Controller 
[    5.136345] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 4 
[    5.136371] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0008000 
[    5.192131] usb usb4: configuration #1 chosen from 1 choice 
[    5.192168] hub 4-0:1.0: USB hub found 
[    5.192183] hub 4-0:1.0: 2 ports detected 
[    5.296312] ahci 0000:00:12.0: version 3.0 
[    5.296332] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[    5.296355] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit 
[    5.296450] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode 
[    5.296454] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    5.296857] scsi0 : ahci 
[    5.296994] scsi1 : ahci 
[    5.298623] scsi2 : ahci 
[    5.299054] scsi3 : ahci 
[    5.299182] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 22 
[    5.299186] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 22 
[    5.299191] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 22 
[    5.299195] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 22 
[    5.780032] ata1: softreset failed (device not ready) 
[    5.780039] ata1: failed due to HW bug, retry pmp=0 
[    5.944038] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    5.991165] ata1.00: ATA-7: WDC WD1600BEVS-07RST0, 04.01G04, max UDMA/133 
[    5.991169] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32) 
[    5.991181] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd 
[    5.991981] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd 
[    5.991985] ata1.00: configured for UDMA/133 
[    6.324041] ata2: SATA link down (SStatus 0 SControl 300) 
[    6.660039] ata3: SATA link down (SStatus 0 SControl 300) 
[    6.996037] ata4: SATA link down (SStatus 0 SControl 300) 
[    7.012141] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 04.0 PQ: 0 ANSI: 5 
[    7.012392] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    7.012407] ehci_hcd 0000:00:13.5: EHCI Host Controller 
[    7.012441] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 5 
[    7.012483] ehci_hcd 0000:00:13.5: debug port 1 
[    7.012504] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400 
[    7.024028] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    7.024185] usb usb5: configuration #1 chosen from 1 choice 
[    7.024216] hub 5-0:1.0: USB hub found 
[    7.024227] hub 5-0:1.0: 10 ports detected 
[    7.136647] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    7.136694] pata_acpi 0000:00:14.1: setting latency timer to 64 
[    7.140647] scsi4 : pata_atiixp 
[    7.140748] scsi5 : pata_atiixp 
[    7.141676] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14 
[    7.141680] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15 
[    7.166254] scsi 0:0:0:0: Attached scsi generic sg0 type 0 
[    7.209593] Driver 'sd' needs updating - please use bus_type methods 
[    7.209732] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB) 
[    7.209760] sd 0:0:0:0: [sda] Write Protect is off 
[    7.209763] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    7.209809] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    7.209900] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB) 
[    7.209924] sd 0:0:0:0: [sda] Write Protect is off 
[    7.209927] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    7.209971] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    7.209976]  sda: sda1 sda2 < sda5 > 
[    7.279235] sd 0:0:0:0: [sda] Attached SCSI disk 
[    7.305536] ata5.00: ATAPI: Optiarc DVD RW AD-7540A, 1.42, max UDMA/33 
[    7.320473] ata5.00: configured for UDMA/33 
[    7.477111] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7540A  1.42 PQ: 0 ANSI: 5 
[    7.477294] scsi 4:0:0:0: Attached scsi generic sg1 type 5 
[    7.507372] Driver 'sr' needs updating - please use bus_type methods 
[    7.510489] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray 
[    7.510495] Uniform CD-ROM driver Revision: 3.20 
[    7.510605] sr 4:0:0:0: Attached scsi CD-ROM sr0 
[    7.722494] PM: Starting manual resume from disk 
[    7.722499] PM: Resume from partition 8:5 
[    7.722501] PM: Checking hibernation image. 
[    7.722731] PM: Resume from disk failed. 
[    7.786925] kjournald starting.  Commit interval 5 seconds 
[    7.786953] EXT3-fs: mounted filesystem with ordered data mode. 
[   14.292681] udevd version 124 started 
[   14.600756] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   14.681491] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   14.776595] Linux agpgart interface v0.103 
[   14.847178] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[   14.868047] ACPI: Power Button (FF) [PWRF] 
[   14.868148] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3 
[   14.900027] ACPI: Power Button (CM) [PWRB] 
[   14.900127] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4 
[   14.932060] ACPI: Sleep Button (CM) [SLPB] 
[   14.932200] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0D:00/input/input5 
[   14.932274] ACPI: Lid Switch [LID] 
[   15.086609] ACPI: Battery Slot [BAT0] (battery present) 
[   15.147757] ACPI: AC Adapter [AC0] (on-line) 
[   15.403503] ath_hal: module license 'Proprietary' taints kernel. 
[   15.405180] ACPI Error (utobject-0508): Unsupported Reference opcode=88 in object f74b1208 [20080609] 
[   15.414144] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413) 
[   15.426416] acpi device:22: registered as cooling_device2 
[   15.427616] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1f/device:20/input/input6 
[   15.449027] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   15.457911] wlan: 0.9.4 
[   15.474899] ath_pci: 0.9.4 
[   15.477418] ath_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   15.477430] ath_pci 0000:02:00.0: setting latency timer to 64 
[   15.501880] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13) 
[   15.501898] ath_pci 0000:02:00.0: PCI INT A disabled 
[   16.106535] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0 
[   16.132216] input: PC Speaker as /devices/platform/pcspkr/input/input7 
[   16.534750] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   16.568749] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS... 
[   16.885816] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000 
[   16.924223] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8 
[   18.363406] lp: driver loaded but no devices found 
[   18.552819] Adding 5686968k swap on /dev/sda5.  Priority:-1 extents:1 across:5686968k 
[   19.105794] EXT3 FS on sda1, internal journal 
[   20.210303] type=1505 audit(1230670730.038:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4154 
[   20.427423] type=1505 audit(1230670730.255:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4159 
[   20.427677] type=1505 audit(1230670730.255:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4159 
[   20.560742] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   21.205954] ACPI: WMI: Mapper loaded 
[   21.551071] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00) 
[   21.551136] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13 
[   21.551141] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15 
[   21.551144] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e 
[   21.551192] powernow-k8: ph2 null fid transition 0xa 
[   22.171076] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   22.214323] apm: BIOS not found. 
[   22.398255] ppdev: user-space parallel port driver 
[   23.620231] Bluetooth: Core ver 2.13 
[   23.622229] NET: Registered protocol family 31 
[   23.622238] Bluetooth: HCI device and connection manager initialized 
[   23.622243] Bluetooth: HCI socket layer initialized 
[   23.637320] Bluetooth: L2CAP ver 2.11 
[   23.637327] Bluetooth: L2CAP socket layer initialized 
[   23.650208] Bluetooth: SCO (Voice Link) ver 0.6 
[   23.650217] Bluetooth: SCO socket layer initialized 
[   23.669593] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   23.669602] Bluetooth: BNEP filters: protocol multicast 
[   23.698118] Bridge firewalling registered 
[   23.698489] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   23.970738] Bluetooth: RFCOMM socket layer initialized 
[   23.972494] Bluetooth: RFCOMM TTY layer initialized 
[   23.972510] Bluetooth: RFCOMM ver 1.10 
[   24.000050] Clocksource tsc unstable (delta = -151641107 ns) 
[   25.908643] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[   26.378529] [drm] Initialized drm 1.1.0 20060810 
[   26.398071] [drm] Initialized radeon 1.29.0 20080528 on minor 0 
[   27.136167] [drm] Setting GART location based on new memory map 
[   27.137593] [drm] Loading RS690 Microcode 
[   27.137624] [drm] Num pipes: 1 
[   27.137635] [drm] writeback test succeeded in 1 usecs 
[   28.141886] r8169: eth0: link down 
[   31.651656] hda-intel: Invalid position buffer, using LPIB read method instead. 
[   58.138076] CPU0 attaching NULL sched-domain. 
[   58.138096] CPU1 attaching NULL sched-domain. 
[   58.139953] CPU0 attaching sched-domain: 
[   58.139962]  domain 0: span 0-1 level CPU 
[   58.139966]   groups: 0 1 
[   58.139975] CPU1 attaching sched-domain: 
[   58.139978]  domain 0: span 0-1 level CPU 
[   58.139981]   groups: 1 0 
[  123.351177] type=1503 audit(1230670833.178:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5774/net/" pid=5774 profile="/usr/sbin/cupsd" 
[  123.433484] NET: Registered protocol family 10 
[  123.434993] lo: Disabled Privacy Extensions 
[  123.436486] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  123.438265] type=1503 audit(1230670833.266:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438280] type=1503 audit(1230670833.266:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438289] type=1503 audit(1230670833.266:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438297] type=1503 audit(1230670833.266:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438306] type=1503 audit(1230670833.266:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438315] type=1503 audit(1230670833.266:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438324] type=1503 audit(1230670833.266:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438332] type=1503 audit(1230670833.266:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5774 profile="/usr/sbin/cupsd" 
[  123.438406] type=1503 audit(1230670833.266:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5774/net/dev" pid=5774 profile="/usr/sbin/cupsd" 
[  888.968025] APIC error on CPU1: 00(40) 
[  888.968039] APIC error on CPU0: 00(40) 
[  954.357756] compiz.real[5494]: segfault at 6f72702d ip 08055c8c sp bf84d0a0 error 4 in compiz.real[8048000+34000] 
[  954.853572] [drm] Num pipes: 1 
[  957.115937] [drm] Setting GART location based on new memory map 
[  957.118063] [drm] Loading RS690 Microcode 
[  957.118125] [drm] Num pipes: 1 
[  957.118136] [drm] writeback test succeeded in 1 usecs 
[  994.763391] CPU0 attaching NULL sched-domain. 
[  994.763412] CPU1 attaching NULL sched-domain. 
[  994.781126] CPU0 attaching sched-domain: 
[  994.781137]  domain 0: span 0-1 level CPU 
[  994.781140]   groups: 0 1 
[  994.781150] CPU1 attaching sched-domain: 
[  994.781152]  domain 0: span 0-1 level CPU 
[  994.781155]   groups: 1 0 
[ 1056.676580] type=1503 audit(1230671766.506:15): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6689/net/" pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.679539] type=1503 audit(1230671766.506:16): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.682005] type=1503 audit(1230671766.510:17): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.684046] type=1503 audit(1230671766.514:18): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.684065] type=1503 audit(1230671766.514:19): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.684081] type=1503 audit(1230671766.514:20): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.684097] type=1503 audit(1230671766.514:21): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.684113] type=1503 audit(1230671766.514:22): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1056.684129] type=1503 audit(1230671766.514:23): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6689 profile="/usr/sbin/cupsd" 
[ 1157.593174] [drm] Num pipes: 1 
[ 1160.926943] PM: Syncing filesystems ... done. 
[ 1160.927669] PM: Preparing system for mem sleep 
[ 1160.928750] Freezing user space processes ... (elapsed 0.00 seconds) done. 
[ 1160.930069] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done. 
[ 1160.930157] PM: Entering mem sleep 
[ 1160.930160] Suspending console(s) (use no_console_suspend to debug) 
[ 1160.930571] sd 0:0:0:0: [sda] Synchronizing SCSI cache 
[ 1161.255036] sd 0:0:0:0: [sda] Stopping disk 
[ 1162.461281] ACPI handle has no context! 
[ 1162.461287] ACPI handle has no context! 
[ 1162.508043] HDA Intel 0000:00:14.2: PCI INT A disabled 
[ 1162.524260] ehci_hcd 0000:00:13.5: PCI INT D disabled 
[ 1162.540055] ohci_hcd 0000:00:13.4: PCI INT C disabled 
[ 1162.540089] ohci_hcd 0000:00:13.3: PCI INT B disabled 
[ 1162.540123] ohci_hcd 0000:00:13.1: PCI INT B disabled 
[ 1162.540156] ohci_hcd 0000:00:13.0: PCI INT A disabled 
[ 1162.604200] ahci 0000:00:12.0: PCI INT A disabled 
[ 1162.604325] PM: suspend devices took 1.676 seconds 
[ 1162.604422] ACPI: Preparing to enter system sleep state S3 
[ 1162.604662] Disabling non-boot CPUs ... 
[ 1162.708030] CPU 1 is now offline 
[ 1162.708034] SMP alternatives: switching to UP code 
[ 1162.718488] CPU0 attaching NULL sched-domain. 
[ 1162.718492] CPU1 attaching NULL sched-domain. 
[ 1162.718536] CPU0 attaching sched-domain: 
[ 1162.718539]  domain 0: span 0 level CPU 
[ 1162.718541]   groups: 0 
[ 1162.718860] CPU1 is down 
[ 1162.718860] Back to C! 
[ 1162.718860] ahci 0000:00:12.0: set SATA to AHCI mode 
[ 1162.718860] Enabling non-boot CPUs ... 
[ 1162.718860] SMP alternatives: switching to SMP code 
[ 1162.730162] Booting processor 1/1 ip 6000 
[ 1162.608823] Initializing CPU#1 
[ 1162.608823] Calibrating delay using timer specific routine.. 3591.02 BogoMIPS (lpj=7182054) 
[ 1162.608823] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[ 1162.608823] CPU: L2 Cache: 512K (64 bytes/line) 
[ 1162.608823] CPU 1(2) -> Core 1 
[ 1162.820194] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02 
[ 1162.820234] CPU0 attaching NULL sched-domain. 
[ 1162.820283] Switch to broadcast mode on CPU1 
[ 1162.820311] CPU0 attaching sched-domain: 
[ 1162.820314]  domain 0: span 0-1 level CPU 
[ 1162.820316]   groups: 0 1 
[ 1162.820321] CPU1 attaching sched-domain: 
[ 1162.820323]  domain 0: span 0-1 level CPU 
[ 1162.820325]   groups: 1 0 
[ 1162.820624] CPU1 is up 
[ 1162.820627] ACPI: Waking up from system sleep state S3 
[ 1162.824034] Switched to high resolution mode on CPU 1 
[ 1163.071001] __ratelimit: 3 callbacks suppressed 
[ 1163.071004] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[ 1163.115690] pci 0000:00:01.0: restoring config space at offset 0x9 (was 0x10001, writing 0xcff1c801) 
[ 1163.115695] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2209191, writing 0x22209191) 
[ 1163.115715] pcieport-driver 0000:00:04.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff) 
[ 1163.115721] pcieport-driver 0000:00:04.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1) 
[ 1163.115725] pcieport-driver 0000:00:04.0: restoring config space at offset 0x8 (was 0x0, writing 0xc030c030) 
[ 1163.115730] pcieport-driver 0000:00:04.0: restoring config space at offset 0x7 (was 0x101, writing 0x200001f1) 
[ 1163.115734] pcieport-driver 0000:00:04.0: restoring config space at offset 0x6 (was 0x0, writing 0x40200) 
[ 1163.115739] pcieport-driver 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008) 
[ 1163.115744] pcieport-driver 0000:00:04.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407) 
[ 1163.115762] pcieport-driver 0000:00:04.0: setting latency timer to 64 
[ 1163.115773] pcieport-driver 0000:00:06.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff) 
[ 1163.115779] pcieport-driver 0000:00:06.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1) 
[ 1163.115783] pcieport-driver 0000:00:06.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0) 
[ 1163.115787] pcieport-driver 0000:00:06.0: restoring config space at offset 0x7 (was 0x101, writing 0x1f1) 
[ 1163.115791] pcieport-driver 0000:00:06.0: restoring config space at offset 0x6 (was 0x0, writing 0x70500) 
[ 1163.115797] pcieport-driver 0000:00:06.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008) 
[ 1163.115801] pcieport-driver 0000:00:06.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100404) 
[ 1163.115818] pcieport-driver 0000:00:06.0: setting latency timer to 64 
[ 1163.115828] pcieport-driver 0000:00:07.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff) 
[ 1163.115834] pcieport-driver 0000:00:07.0: restoring config space at offset 0x9 (was 0x10001, writing 0x88018801) 
[ 1163.115838] pcieport-driver 0000:00:07.0: restoring config space at offset 0x8 (was 0x0, writing 0xc040c040) 
[ 1163.115843] pcieport-driver 0000:00:07.0: restoring config space at offset 0x7 (was 0x101, writing 0xa1a1) 
[ 1163.115847] pcieport-driver 0000:00:07.0: restoring config space at offset 0x6 (was 0x0, writing 0xa0800) 
[ 1163.115853] pcieport-driver 0000:00:07.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008) 
[ 1163.115857] pcieport-driver 0000:00:07.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407) 
[ 1163.115874] pcieport-driver 0000:00:07.0: setting latency timer to 64 
[ 1163.115890] ahci 0000:00:12.0: restoring config space at offset 0xf (was 0x100, writing 0x10b) 
[ 1163.115902] ahci 0000:00:12.0: restoring config space at offset 0x9 (was 0xfec01000, writing 0xc0004000) 
[ 1163.115908] ahci 0000:00:12.0: restoring config space at offset 0x8 (was 0x1, writing 0x8401) 
[ 1163.115914] ahci 0000:00:12.0: restoring config space at offset 0x7 (was 0x1, writing 0x8431) 
[ 1163.115919] ahci 0000:00:12.0: restoring config space at offset 0x6 (was 0x1, writing 0x8439) 
[ 1163.115925] ahci 0000:00:12.0: restoring config space at offset 0x5 (was 0x1, writing 0x8435) 
[ 1163.115930] ahci 0000:00:12.0: restoring config space at offset 0x4 (was 0x1, writing 0x8441) 
[ 1163.115936] ahci 0000:00:12.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000) 
[ 1163.115943] ahci 0000:00:12.0: restoring config space at offset 0x1 (was 0x2300000, writing 0x2300007) 
[ 1163.115960] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[ 1163.116153] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[ 1163.140023] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[ 1163.164022] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[ 1163.188023] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[ 1163.228021] ehci_hcd 0000:00:13.5: enabling device (0000 -> 0002) 
[ 1163.228026] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[ 1163.228061] ehci_hcd 0000:00:13.5: restoring config space at offset 0x1 (was 0x2b00006, writing 0x2b00017) 
[ 1163.228130] pata_atiixp 0000:00:14.1: restoring config space at offset 0x3 (was 0x0, writing 0x4000) 
[ 1163.228136] pata_atiixp 0000:00:14.1: restoring config space at offset 0x2 (was 0x1018a00, writing 0x1018200) 
[ 1163.244030] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa) 
[ 1163.244053] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002) 
[ 1163.244067] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[ 1163.244188] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[ 1163.260039] r8169 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104) 
[ 1163.260056] r8169 0000:08:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xc0400004) 
[ 1163.260063] r8169 0000:08:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xa001) 
[ 1163.260069] r8169 0000:08:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10) 
[ 1163.260076] r8169 0000:08:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407) 
[ 1163.263470] sd 0:0:0:0: [sda] Starting disk 
[ 1163.408534] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out 
[ 1163.408537] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out 
[ 1163.424524] ata5.00: configured for UDMA/33 
[ 1163.436077] ata4: SATA link down (SStatus 0 SControl 300) 
[ 1163.436108] ata2: SATA link down (SStatus 0 SControl 300) 
[ 1163.436140] ata3: SATA link down (SStatus 0 SControl 300) 
[ 1163.600023] ata1: softreset failed (device not ready) 
[ 1163.600027] ata1: failed due to HW bug, retry pmp=0 
[ 1163.764032] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[ 1165.949640] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd 
[ 1165.950449] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd 
[ 1165.950451] ata1.00: configured for UDMA/133 
[ 1165.964086] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB) 
[ 1165.964110] sd 0:0:0:0: [sda] Write Protect is off 
[ 1165.964112] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[ 1165.964151] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 1166.020390] PM: resume devices took 2.952 seconds 
[ 1166.020468] PM: Finishing wakeup. 
[ 1166.020470] Restarting tasks ... done. 
[ 1167.444124] r8169: eth0: link down 
[ 1167.444671] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 1168.421305] [drm] Loading RS690 Microcode 
[ 1168.421346] [drm] Num pipes: 1 
[ 1211.558166] CPU0 attaching NULL sched-domain. 
[ 1211.558199] CPU1 attaching NULL sched-domain. 
[ 1211.569154] CPU0 attaching sched-domain: 
[ 1211.569172]  domain 0: span 0-1 level MC 
[ 1211.569180]   groups: 0 1 
[ 1211.569192]   domain 1: span 0-1 level CPU 
[ 1211.569199]    groups: 0-1 
[ 1211.569210] CPU1 attaching sched-domain: 
[ 1211.569215]  domain 0: span 0-1 level MC 
[ 1211.569221]   groups: 1 0 
[ 1211.569230]   domain 1: span 0-1 level CPU 
[ 1211.569235]    groups: 0-1 
[ 1265.115801] CPU0 attaching NULL sched-domain. 
[ 1265.115832] CPU1 attaching NULL sched-domain. 
[ 1265.118796] CPU0 attaching sched-domain: 
[ 1265.118812]  domain 0: span 0-1 level CPU 
[ 1265.118820]   groups: 0 1 
[ 1265.118837] CPU1 attaching sched-domain: 
[ 1265.118843]  domain 0: span 0-1 level CPU 
[ 1265.118849]   groups: 1 0 



aina@aina-laptop:~$ sudo lshw - C network 
[sudo] password for aina: 

aina@aina-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

pan0      Interface doesn't support scanning. 

aina@aina-laptop:~$ 


aina@aina-laptop:~$ iwlist scan wlan0 
iwlist: unknown command `wlan0' (check 'iwlist --help'). 
aina@aina-laptop:~$ 



aina@aina-laptop:~$ lsb_release -d 
Description:	Ubuntu 8.10 
aina@aina-laptop:~$ 


aina@aina-laptop:~$ uname -mr 
2.6.27-7-generic i686 
aina@aina-laptop:~$ 

aina@aina-laptop:~$ sudo /etc/init.d/networking restart

---

### Post by big-t on 2008-12-30
i realy hope someone can help me whit this, i realy want to use this system.
i can't stand windows vista anymore...

---

### Post by teaker1s on 2008-12-30
[COLOR="Red"]02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) [/COLOR]

first want to look under System on desktop panel and locate
System->Administration->Restricted Drivers/Hardware Drivers 

See if you can enable it there, if not first link below

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html")

---

### Post by big-t on 2008-12-30
thanx for fast respond, i will try now :)

---

