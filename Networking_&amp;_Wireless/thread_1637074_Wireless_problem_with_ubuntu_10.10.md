---
title: "Wireless problem with ubuntu 10.10"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by dharmabum4732 on 2010-12-04
Hi,

I'm having a problem with my wireless connection in ubuntu 10.10.

It will connect for about 5 minutes or so and then slow down and finally disconnect.

Here is some information that might be helpful:

Here is the output of lspci
```
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01) 
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) 
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) 
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) 
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) 
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02) 
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2) 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12) 
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) 
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) 
05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) 
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10) 
```

Here is lsusb

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 002: ID 046d:c31c Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 005: ID 046d:c714 Logitech, Inc. diNovo Edge Keyboard 
Bus 003 Device 004: ID 046d:c713 Logitech, Inc. 
Bus 003 Device 003: ID 046d:0b04 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 006: ID 0781:5506 SanDisk Corp. 
Bus 002 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader 
Bus 002 Device 004: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub 
Bus 002 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

```

spci -nn | grep 'Wireless Brand' does not produce any results

iwconfig wlan0
```
wlan0     IEEE 802.11bgn  ESSID:"BusyGiraffe"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 

```

here is lsmod

```
Module                  Size  Used by 
aes_i586                7280  0 
aes_generic            26875  1 aes_i586 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_analog    59649  1 
rt2870sta             405890  0 
snd_hda_intel          22107  2 
arc4                    1165  2 
snd_hda_codec          87552  2 snd_hda_codec_analog,snd_hda_intel 
snd_hwdep               5040  1 snd_hda_codec 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi            4588  0 
rt2800usb               8367  0 
nouveau               516971  2 
snd_rawmidi            17783  1 snd_seq_midi 
rt2800lib              28897  1 rt2800usb 
usb_storage            40172  1 
snd_seq_midi_event      6047  1 snd_seq_midi 
ttm                    56633  1 nouveau 
rt2x00usb               9779  2 rt2800usb,rt2800lib 
rt2x00lib              27275  2 rt2800lib,rt2x00usb 
led_class               2633  1 rt2x00lib 
drm_kms_helper         30200  1 nouveau 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
hid_logitech            8971  0 
mac80211              231541  2 rt2x00usb,rt2x00lib 
asus_atk0110           11423  0 
ff_memless              4393  1 hid_logitech 
drm                   168054  4 nouveau,ttm,drm_kms_helper 
snd_timer              19067  2 snd_pcm,snd_seq 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              144470  2 rt2x00lib,mac80211 
joydev                  8735  0 
crc_ccitt               1351  2 rt2870sta,rt2800usb 
snd                    49006  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
serio_raw               4022  0 
x38_edac                2967  0 
soundcore                880  1 snd 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm 
agpgart                32011  2 ttm,drm 
i2c_algo_bit            5168  1 nouveau 
edac_core              38630  2 x38_edac 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp 
usbhid                 36882  1 hid_logitech 
hid                    67742  2 hid_logitech,usbhid 
r8169                  36489  0 
pata_jmicron            1855  0 
firewire_ohci          21106  0 
ahci                   19013  0 
firewire_core          46643  1 firewire_ohci 
crc_itu_t               1383  1 firewire_core 
libahci                21667  1 ahci 
mii                     4425  1 r8169 
sky2                   45127  0 

lsmod | grep r8169 (is this right??)
r8169                  36489  0 
mii                     4425  1 r8169 
```

here is dmesg

```
[    0.463884] PPP generic driver version 2.4.2 
[    0.463915] tun: Universal TUN/TAP device driver, 1.6 
[    0.463916] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.463976] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.463989]   alloc irq_desc for 18 on node -1 
[    0.463991]   alloc kstat_irqs on node -1 
[    0.463994] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    0.464002] ehci_hcd 0000:00:1a.7: setting latency timer to 64 
[    0.464005] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
[    0.464031] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1 
[    0.464051] ehci_hcd 0000:00:1a.7: debug port 1 
[    0.467930] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported 
[    0.467942] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00 
[    0.483653] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00 
[    0.483751] hub 1-0:1.0: USB hub found 
[    0.483755] hub 1-0:1.0: 6 ports detected 
[    0.483815]   alloc irq_desc for 23 on node -1 
[    0.483816]   alloc kstat_irqs on node -1 
[    0.483820] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    0.483828] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    0.483831] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    0.483864] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2 
[    0.483882] ehci_hcd 0000:00:1d.7: debug port 1 
[    0.487769] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    0.487780] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800 
[    0.503655] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    0.503732] hub 2-0:1.0: USB hub found 
[    0.503736] hub 2-0:1.0: 6 ports detected 
[    0.503795] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.503807] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.503820] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.503824] uhci_hcd 0000:00:1a.0: setting latency timer to 64 
[    0.503827] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
[    0.503856] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3 
[    0.503882] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800 
[    0.503968] hub 3-0:1.0: USB hub found 
[    0.503972] hub 3-0:1.0: 2 ports detected 
[    0.504019]   alloc irq_desc for 21 on node -1 
[    0.504021]   alloc kstat_irqs on node -1 
[    0.504024] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    0.504029] uhci_hcd 0000:00:1a.1: setting latency timer to 64 
[    0.504031] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
[    0.504057] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4 
[    0.504085] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880 
[    0.504176] hub 4-0:1.0: USB hub found 
[    0.504180] hub 4-0:1.0: 2 ports detected 
[    0.504227] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    0.504231] uhci_hcd 0000:00:1a.2: setting latency timer to 64 
[    0.504234] uhci_hcd 0000:00:1a.2: UHCI Host Controller 
[    0.504258] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5 
[    0.504277] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00 
[    0.504364] hub 5-0:1.0: USB hub found 
[    0.504367] hub 5-0:1.0: 2 ports detected 
[    0.504416] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    0.504420] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    0.504423] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    0.504450] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6 
[    0.504470] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080 
[    0.504559] hub 6-0:1.0: USB hub found 
[    0.504562] hub 6-0:1.0: 2 ports detected 
[    0.504609]   alloc irq_desc for 19 on node -1 
[    0.504610]   alloc kstat_irqs on node -1 
[    0.504614] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    0.504618] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    0.504621] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    0.504647] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7 
[    0.504673] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400 
[    0.504761] hub 7-0:1.0: USB hub found 
[    0.504769] hub 7-0:1.0: 2 ports detected 
[    0.504817] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    0.504821] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    0.504823] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    0.504850] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8 
[    0.504870] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480 
[    0.504956] hub 8-0:1.0: USB hub found 
[    0.504959] hub 8-0:1.0: 2 ports detected 
[    0.505063] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[    0.505066] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp 
[    0.505556] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.505601] mice: PS/2 mouse device common for all mice 
[    0.505691] rtc_cmos 00:03: RTC can wake from S4 
[    0.505718] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    0.505739] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs 
[    0.505821] device-mapper: uevent: version 1.0.3 
[    0.505902] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com 
[    0.505969] device-mapper: multipath: version 1.1.1 loaded 
[    0.505971] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    0.506054] EISA: Probing bus 0 at eisa.0 
[    0.506056] EISA: Cannot allocate resource for mainboard 
[    0.506058] Cannot allocate resource for EISA slot 1 
[    0.506059] Cannot allocate resource for EISA slot 2 
[    0.506061] Cannot allocate resource for EISA slot 3 
[    0.506063] Cannot allocate resource for EISA slot 4 
[    0.506064] Cannot allocate resource for EISA slot 5 
[    0.506066] Cannot allocate resource for EISA slot 6 
[    0.506067] Cannot allocate resource for EISA slot 7 
[    0.506068] Cannot allocate resource for EISA slot 8 
[    0.506070] EISA: Detected 0 cards. 
[    0.506177] cpuidle: using governor ladder 
[    0.506178] cpuidle: using governor menu 
[    0.506415] TCP cubic registered 
[    0.506517] NET: Registered protocol family 10 
[    0.506812] lo: Disabled Privacy Extensions 
[    0.507000] NET: Registered protocol family 17 
[    0.507603] Using IPI No-Shortcut mode 
[    0.507663] PM: Resume from disk failed. 
[    0.507672] registered taskstats version 1 
[    0.507934]   Magic number: 6:866:349 
[    0.507979] rtc_cmos 00:03: setting system clock to 2010-12-03 22:19:24 UTC (1291414764) 
[    0.507982] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.507983] EDD information not available. 
[    0.545779] Freeing initrd memory: 10500k freed 
[    0.811110] isapnp: No Plug & Play device found 
[    0.939715] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    0.939857] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    0.948714] ata4.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133 
[    0.948718] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    0.956805] ata4.00: configured for UDMA/133 
[    0.975282] ata3.00: ATA-8: ST31500341AS, CC1H, max UDMA/133 
[    0.975286] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    1.020509] usb 1-3: new high speed USB device using ehci_hcd and address 4 
[    1.031268] ata3.00: configured for UDMA/133 
[    1.256068] ata1.00: SATA link down (SStatus 0 SControl 300) 
[    1.256084] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.256089] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.256109] ata2.01: SATA link down (SStatus 0 SControl 300) 
[    1.272202] ata1.01: ATAPI: ASUS    DRW-2014L1T, 1.02, max UDMA/66 
[    1.273255] ata2.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133 
[    1.273259] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    1.281276] ata2.00: configured for UDMA/133 
[    1.288142] ata1.01: configured for UDMA/66 
[    1.288883] scsi 0:0:1:0: CD-ROM            ASUS     DRW-2014L1T      1.02 PQ: 0 ANSI: 5 
[    1.292091] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray 
[    1.292095] Uniform CD-ROM driver Revision: 3.20 
[    1.292183] sr 0:0:1:0: Attached scsi CD-ROM sr0 
[    1.292228] sr 0:0:1:0: Attached scsi generic sg0 type 5 
[    1.292331] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5 
[    1.292424] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB) 
[    1.292432] sd 1:0:0:0: Attached scsi generic sg1 type 0 
[    1.292488] sd 1:0:0:0: [sda] Write Protect is off 
[    1.292491] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.292509] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.292523] scsi 2:0:0:0: Direct-Access     ATA      ST31500341AS     CC1H PQ: 0 ANSI: 5 
[    1.292615]  sda: 
[    1.292620] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[    1.292627] sd 2:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB) 
[    1.292677] sd 2:0:0:0: [sdb] Write Protect is off 
[    1.292680] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[    1.292702] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.292726] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5 
[    1.292817] sd 3:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB) 
[    1.292832] sd 3:0:0:0: Attached scsi generic sg3 type 0 
[    1.292860]  sdb: 
[    1.292927] sd 3:0:0:0: [sdc] Write Protect is off 
[    1.292929] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00 
[    1.292952] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.293070]  sdc: sdb1 
[    1.317252] sd 2:0:0:0: [sdb] Attached SCSI disk 
[    1.321931]  sdc1 
[    1.322137] sd 3:0:0:0: [sdc] Attached SCSI disk 
[    1.322709]  sda1 
[    1.322881] sd 1:0:0:0: [sda] Attached SCSI disk 
[    1.322891] Freeing unused kernel memory: 684k freed 
[    1.323145] Write protecting the kernel text: 4932k 
[    1.323191] Write protecting the kernel read-only data: 1976k 
[    1.337018] usb 2-5: new high speed USB device using ehci_hcd and address 3 
[    1.337021] udev[107]: starting version 163 
[    1.358356] sky2: driver version 1.28 
[    1.358387] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    1.358397] sky2 0000:02:00.0: setting latency timer to 64 
[    1.358419] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3 
[    1.358496]   alloc irq_desc for 44 on node -1 
[    1.358498]   alloc kstat_irqs on node -1 
[    1.358510] sky2 0000:02:00.0: irq 44 for MSI/MSI-X 
[    1.360690] sky2 0000:02:00.0: eth0: addr 00:1f:c6:51:10:0c 
[    1.377160] ahci 0000:03:00.0: version 3.0 
[    1.377179] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.377226] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    1.377281] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode 
[    1.377284] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.377289] ahci 0000:03:00.0: setting latency timer to 64 
[    1.377993] scsi4 : ahci 
[    1.378265] scsi5 : ahci 
[    1.378359] ata5: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16 
[    1.378363] ata6: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe180 irq 16 
[    1.378427] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    1.378451] pata_jmicron 0000:03:00.1: setting latency timer to 64 
[    1.378528] scsi6 : pata_jmicron 
[    1.378577] scsi7 : pata_jmicron 
[    1.379280] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17 
[    1.379283] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17 
[    1.464512] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0 
[    1.464534] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    1.464552] r8169 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.464578] r8169 0000:05:04.0: (unregistered net_device): no PCI Express capability 
[    1.465077] r8169 0000:05:04.0: eth1: RTL8169sc/8110sc at 0xf812ec00, 00:1f:c6:51:0d:85, XID 18000000 IRQ 16 
[    1.470065] hub 2-5:1.0: USB hub found 
[    1.470145] hub 2-5:1.0: 2 ports detected 
[    1.696812] ata6: SATA link down (SStatus 0 SControl 300) 
[    1.696815] ata5: SATA link down (SStatus 0 SControl 300) 
[    1.709515] usb 3-1: new full speed USB device using uhci_hcd and address 2 
[    1.881827] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null) 
[    1.907196] usbcore: registered new interface driver hiddev 
[    1.909436] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2 
[    1.909516] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1/input0 
[    1.914103] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input3 
[    1.914190] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1/input1 
[    1.914205] usbcore: registered new interface driver usbhid 
[    1.914206] usbhid: USB HID core driver 
[    1.957572] firewire_core: created device fw0: GUID 001e8c00012a5b8a, S400 
[    2.140527] usb 3-2: new full speed USB device using uhci_hcd and address 3 
[    2.321083] hub 3-2:1.0: USB hub found 
[    2.323034] hub 3-2:1.0: 3 ports detected 
[    2.569511] usb 7-2: new low speed USB device using uhci_hcd and address 2 
[    2.780288] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input4 
[    2.780362] generic-usb 0003:046D:C31C.0003: input,hidraw2: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:1d.1-2/input0 
[    2.827946] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input5 
[    2.828021] generic-usb 0003:046D:C31C.0004: input,hidraw3: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:1d.1-2/input1 
[    2.900635] usb 2-5.1: new high speed USB device using ehci_hcd and address 4 
[    2.992685] hub 2-5.1:1.0: USB hub found 
[    2.992750] hub 2-5.1:1.0: 4 ports detected 
[    3.069132] usb 3-2.2: new full speed USB device using uhci_hcd and address 4 
[    3.228482] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input6 
[    3.228551] generic-usb 0003:046D:C713.0005: input,hidraw4: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.0-2.2/input0 
[    3.303099] usb 3-2.3: new full speed USB device using uhci_hcd and address 5 
[    3.544171] usb 2-5.1.1: new high speed USB device using ehci_hcd and address 5 
[    3.793186] usb 2-5.1.4: new high speed USB device using ehci_hcd and address 6 
[    8.616026] udev[410]: starting version 163 
[    8.624298] lp: driver loaded but no devices found 
[    8.637811] EDAC MC: Ver: 2.1.0 Sep 19 2010 
[    8.648459] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0 
[    8.648738] Linux agpgart interface v0.103 
[    8.673908] udev[460]: renamed network interface eth0 to eth0-eth1 
[    8.757194] cfg80211: Calling CRDA to update world regulatory domain 
[    8.772638] type=1400 audit(1291436372.760:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=631 comm="apparmor_parser" 
[    8.773217] type=1400 audit(1291436372.760:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser" 
[    8.773513] type=1400 audit(1291436372.760:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=631 comm="apparmor_parser" 
[    8.783801] [drm] Initialized drm 1.1.0 20060810 
[    8.785290] cfg80211: World regulatory domain updated: 
[    8.785292]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[    8.785295]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    8.785297]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[    8.785299]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[    8.785301]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    8.785303]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    8.793909] udev[493]: renamed network interface eth1 to eth0 
[    8.799568] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input7 
[    8.799692] logitech 0003:046D:C714.0006: input,hiddev97,hidraw5: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.0-2.3/input0 
[    8.820618] Initializing USB Mass Storage driver... 
[    8.834050] udev[460]: renamed network interface eth0-eth1 to eth1 
[    8.839689] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    8.839694] nouveau 0000:01:00.0: setting latency timer to 64 
[    8.840370] scsi8 : usb-storage 2-5.1.1:1.0 
[    8.842121] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x092000a2) 
[    8.842711] scsi9 : usb-storage 2-5.1.4:1.0 
[    8.842865] usbcore: registered new interface driver usb-storage 
[    8.842867] USB Mass Storage support registered. 
[    8.844458] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN 
[    8.879486] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[    8.879558]   alloc irq_desc for 45 on node -1 
[    8.879560]   alloc kstat_irqs on node -1 
[    8.879575] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X 
[    8.879617] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[    8.879994] phy0: Selected rate control algorithm 'minstrel' 
[    8.880549] Registered led device: rt2800usb-phy0::radio 
[    8.880567] Registered led device: rt2800usb-phy0::assoc 
[    8.880590] Registered led device: rt2800usb-phy0::quality 
[    8.880850] usbcore: registered new interface driver rt2800usb 
[    8.881304] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned. 
[    8.885586] rtusb init ---> 
[    8.885644] usbcore: registered new interface driver rt2870 
[    8.900361] [drm] nouveau 0000:01:00.0: ... appears to be valid 
[    8.900365] [drm] nouveau 0000:01:00.0: BIT BIOS found 
[    8.900367] [drm] nouveau 0000:01:00.0: Bios version 62.92.25.00 
[    8.900370] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported 
[    8.900372] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0 
[    8.900374] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028 
[    8.900377] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00000030 
[    8.900379] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028 
[    8.900381] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00000030 
[    8.900382] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080 
[    8.900385] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4 
[    8.900387] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07 
[    8.900390] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08 
[    8.900392] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff 
[    8.900394] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff 
[    8.900396] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff 
[    8.900403] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xC17F 
[    8.945656] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xC530 
[    8.961007] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD2AB 
[    8.961014] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD3CD 
[    8.969574] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xD5FD 
[    8.969577] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xD662 
[    8.993012] [drm] nouveau 0000:01:00.0: 0xD662: Condition still not met after 20ms, skipping following opcodes 
[    8.993019] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0 
[    8.993022] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0 
[    8.993024] [drm] nouveau 0000:01:00.0: 0x9FAE: parsing output script 0 
[    8.993030] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM 
[    9.073859] [TTM] Zone  kernel: Available graphics memory: 428158 kiB. 
[    9.073861] [TTM] Zone highmem: Available graphics memory: 1677186 kiB. 
[    9.073862] [TTM] Initializing pool allocator. 
[    9.088298] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture) 
[    9.088304] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining 
[    9.088469] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1 
[    9.091933] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1 
[    9.092392] [drm] nouveau 0000:01:00.0: Detected a DAC output 
[    9.092394] [drm] nouveau 0000:01:00.0: Detected a TMDS output 
[    9.092396] [drm] nouveau 0000:01:00.0: Detected a DAC output 
[    9.092398] [drm] nouveau 0000:01:00.0: Detected a TMDS output 
[    9.092400] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown 
[    9.092402] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector 
[    9.092475] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector 
[    9.092551] [drm] nouveau 0000:01:00.0: Detected a TV connector 
[    9.092580] [drm] nouveau 0000:01:00.0:   no encoders, ignoring 
[    9.268651] [drm] nouveau 0000:01:00.0: allocated 1920x1200 fb: 0x40250000, bo dead8c00 
[    9.272333] [drm] nouveau 0000:01:00.0: 0xB3B4: parsing output script 1 
[    9.272367] [drm] nouveau 0000:01:00.0: 0xB3B5: parsing output script 2 
[    9.272384] [drm] nouveau 0000:01:00.0: 0xB2FB: parsing clock script 0 
[    9.272409] Console: switching to colour frame buffer device 240x75 
[    9.275209] fb0: nouveaufb frame buffer device 
[    9.275211] drm: registered panic notifier 
[    9.275214] Slow work thread pool: Starting up 
[    9.275252] Slow work thread pool: Ready 
[    9.275257] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0 
[    9.844890] scsi 9:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2 
[    9.845386] sd 9:0:0:0: Attached scsi generic sg4 type 0 
[    9.847090] sd 9:0:0:0: [sdd] 8027789 512-byte logical blocks: (4.11 GB/3.82 GiB) 
[    9.848089] sd 9:0:0:0: [sdd] Write Protect is off 
[    9.848091] sd 9:0:0:0: [sdd] Mode Sense: 03 00 00 00 
[    9.848093] sd 9:0:0:0: [sdd] Assuming drive cache: write through 
[    9.850097] sd 9:0:0:0: [sdd] Assuming drive cache: write through 
[    9.850104]  sdd: sdd1 
[    9.851472] scsi 8:0:0:0: Direct-Access     Generic  Flash HS-CF      4.44 PQ: 0 ANSI: 0 
[    9.852086] sd 9:0:0:0: [sdd] Assuming drive cache: write through 
[    9.852089] sd 9:0:0:0: [sdd] Attached SCSI removable disk 
[    9.855227] scsi 8:0:0:1: Direct-Access     Generic  Flash HS-MS      4.44 PQ: 0 ANSI: 0 
[    9.858975] scsi 8:0:0:2: Direct-Access     Generic  Flash HS-SM      4.44 PQ: 0 ANSI: 0 
[    9.862226] scsi 8:0:0:3: Direct-Access     Generic  Flash HS-SD/MMC  4.44 PQ: 0 ANSI: 0 
[    9.862560] sd 8:0:0:0: Attached scsi generic sg5 type 0 
[    9.865252] sd 8:0:0:1: Attached scsi generic sg6 type 0 
[    9.866149] sd 8:0:0:2: Attached scsi generic sg7 type 0 
[    9.866415] sd 8:0:0:3: Attached scsi generic sg8 type 0 
[    9.928239] sd 8:0:0:3: [sdh] Attached SCSI removable disk 
[    9.984599] sd 8:0:0:1: [sdf] Attached SCSI removable disk 
[    9.996727] sd 8:0:0:0: [sde] Attached SCSI removable disk 
[   10.009739] sd 8:0:0:2: [sdg] Attached SCSI removable disk 
[   10.011025] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
[   10.034182] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro 
[   10.136391] ppdev: user-space parallel port driver 
[   10.153014] type=1400 audit(1291436374.140:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1175 comm="apparmor_parser" 
[   10.154321] type=1400 audit(1291436374.140:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1176 comm="apparmor_parser" 
[   10.154880] type=1400 audit(1291436374.140:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1176 comm="apparmor_parser" 
[   10.155196] type=1400 audit(1291436374.140:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1176 comm="apparmor_parser" 
[   10.157924] type=1400 audit(1291436374.144:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1177 comm="apparmor_parser" 
[   10.162357] type=1400 audit(1291436374.148:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1182 comm="apparmor_parser" 
[   10.164821] type=1400 audit(1291436374.152:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1177 comm="apparmor_parser" 
[   10.364553] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   10.368624] sky2 0000:02:00.0: eth1: enabling interface 
[   10.368764] ADDRCONF(NETDEV_UP): eth1: link is not ready 
[   10.386523] r8169 0000:05:04.0: eth0: link down 
[   10.386668] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   10.526078] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0 
[   10.641216] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2 
[   10.644729] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2 
[   12.549902] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0 
[   21.741537] wlan0: authenticate with 68:7f:74:90:3d:36 (try 1) 
[   21.745664] wlan0: authenticated 
[   21.745675] wlan0: associate with 68:7f:74:90:3d:36 (try 1) 
[   21.748914] wlan0: RX AssocResp from 68:7f:74:90:3d:36 (capab=0x11 status=0 aid=1) 
[   21.748916] wlan0: associated 
[   21.767329] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   21.814169] padlock: VIA PadLock not detected. 
[   32.097006] wlan0: no IPv6 routers present 
[  135.440011] No probe response from AP 68:7f:74:90:3d:36 after 500ms, disconnecting. 
[  135.553532] cfg80211: All devices are disconnected, going to restore regulatory settings 
[  135.553537] cfg80211: Restoring regulatory settings 
[  135.553540] cfg80211: Calling CRDA to update world regulatory domain 
[  135.556439] cfg80211: World regulatory domain updated: 
[  135.556442]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[  135.556444]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  135.556446]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[  135.556448]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[  135.556451]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  135.556453]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  136.967405] wlan0: authenticate with 68:7f:74:90:3d:36 (try 1) 
[  137.165008] wlan0: authenticate with 68:7f:74:90:3d:36 (try 2) 
[  137.364009] wlan0: authenticate with 68:7f:74:90:3d:36 (try 3) 
[  137.564008] wlan0: authentication with 68:7f:74:90:3d:36 timed out 
[  148.289991] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  148.488010] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  148.688010] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  148.888010] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
[  152.546022] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  152.744011] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  152.944012] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  153.144009] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
[  163.863859] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  164.061508] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  164.260009] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  164.460009] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
[  175.178319] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  175.376011] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  175.576013] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  175.776009] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
[  186.481562] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  186.680009] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  186.881012] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  187.081008] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
[  197.825311] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  198.025009] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  198.224012] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  198.425508] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
[  209.141333] wlan0: direct probe to 68:7f:74:90:3d:36 (try 1) 
[  209.340011] wlan0: direct probe to 68:7f:74:90:3d:36 (try 2) 
[  209.540010] wlan0: direct probe to 68:7f:74:90:3d:36 (try 3) 
[  209.740010] wlan0: direct probe to 68:7f:74:90:3d:36 timed out 
```

here is iwlist scan

```
 lo        Interface doesn't support scanning. 

eth1      Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 
```

here is iwlist scan wlan0

```
iwlist: unknown command `wlan0' (check 'iwlist &#8211;help').
```

here is lsb_release -d

```
Description:	Ubuntu 10.10 
```

here is uname -mr

```
2.6.35-22-generic i686
```

and here is sudo /etc/init.d/networking restart

```
* Reconfiguring network interfaces...                                   [ OK ] 
```

I hope this is the right information.  Does anyone have any advice?

Thanks!
-Max

---

### Post by northd_tech on 2010-12-04
Here is [mostly] the network-related output from what I observed:

> **lspci**
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12) 
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

**lsusb**
Bus 001 Device 004: ID 0b05:**1742 ASUSTek** Computer, Inc. **802.11n** Network Adapter 

**lsmod**
Module Size Used by
rt2800usb               8367  0 
rt2800lib              28897  1 rt2800usb 
rt2x00usb               9779  2 rt2800usb,rt2800lib 
rt2x00lib              27275  2 rt2800lib,rt2x00usb 
led_class               2633  1 rt2x00lib
mac80211              231541  2 rt2x00usb,rt2x00lib 
cfg80211              144470  2 rt2x00lib,mac80211
crc_ccitt               1351  2 rt2870sta,rt2800usb 
rt2870sta             405890  0 

asus_atk0110           11423  0 

r8169                  36489  0 
mii                     4425  1 r8169 

That looks to be an ASUSTek 1742 wireless sent through a USB interface.  I only found one more thread here about that kind of a setup:

[http://ubuntuforums.org/showthread.php?t=916845](http://ubuntuforums.org/showthread.php?t=916845)

It must be somewhat rare with only 2 threads in over 1.5 years... :o

You also appear to have 2 ethernet adapters- a Realtek 8169SC and a Marvell 88E8056 (unless this is a multi-function adapter showing up as 2 "cards" for some reason).  There is a LOT going on with all those modules loaded, and I suspect there may be a conflict there- but I don't know what the proper setup is for that hardware.

Can you also post the output of the following terminal commands:

```
ifconfig
iwconfig
```I would do a lot of searching about "ASUS 1742 USB wireless" and take good notes- sorry I'm not more help with this one.  You might want to see what information is available from the manufacturer/website about that wireless interface and post it here if it looks useful.

---

### Post by dharmabum4732 on 2010-12-04
Hi northd_tech,

Thanks for responding to my post!

Here is some information on my motherboard--my wifi is controlled by it.

[http://usa.asus.com/product.aspx?P_ID=cRo5Hpv4T1MXAGCk](http://usa.asus.com/product.aspx?P_ID=cRo5Hpv4T1MXAGCk)

and here is the output of iwconfig

```
lo        no wireless extensions. 
 
eth1      no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bgn  ESSID:"BusyGiraffe"   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=18 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
```

and of ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:51:0d:85   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 Base address:0x8c00  
 
eth1      Link encap:Ethernet  HWaddr 00:1f:c6:51:10:0c   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 
 
wlan0     Link encap:Ethernet  HWaddr 00:15:af:72:36:3e   
          inet6 addr: fe80::215:afff:fe72:363e/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:2577 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1660 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1766849 (1.7 MB)  TX bytes:194384 (194.3 KB) 
```

Thanks again!

Let me know what you think.

---

### Post by dharmabum4732 on 2010-12-04
I found that there are linux drivers for my motherboard.  Do you think it would help to install them?

	
 	
 Version -

 	
 Description	Support Linux Drivers.

 File Size	12.56 (MBytes)	2008/05/28 update

 Download from	 Global (DLM) Global China   P2P

---

### Post by dharmabum4732 on 2010-12-04
Well, I downloaded the asus software... I think this is WAY over my head.  I suppose I'll just wait for a potential fix for this issue in later distributions.

Thanks for your help!

---

### Post by northd_tech on 2010-12-04
I was going to take a look at the "readme" files for that download and see what is involved there, but I can't seem to access the download page.  It only gives me a choice to "Select OS" (without any OS'es listed!) and then says "0 files found" at the "Download" link.

[http://usa.asus.com/product.aspx?P_ID=cRo5Hpv4T1MXAGCk#](http://usa.asus.com/product.aspx?P_ID=cRo5Hpv4T1MXAGCk#)

If there is a Linux motherboard driver package, you might need to install a bunch of header files and possibly kernel "backports" to get things working better/properly, and that motherboard might be more of a "semi-Linux-supported" thing right now.

Looking at this output, your wireless is currently "talking" to the WiFi modem, but there might still be something incorrect or less than optimal in the driver setup.  I have read a lot about unstable and slow wireless connections for many people here with "working" hardware, and it might also be an authentication/encryption (WPA, WEP, WEP2, etc.) or configuration problem and not in the drivers *per se*.

> **iwconfig**
wlan0     IEEE 802.11bgn  **ESSID:"BusyGiraffe"**   
          Mode:Managed  **Frequency:2.412 GHz**  Access Point: Not-Associated    
          **Tx-Power=18 dBm  **  
          Retry  long limit:7   RTS thr: off   Fragment thr: off 
          Power Management: on

**ifconfig**
wlan0     Link encap:Ethernet  HWaddr 00:15:af:72:36:3e   
          inet6 addr: fe80::215:afff:fe72:363e/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:2577 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1660 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          **RX bytes:1766849 (1.7 MB)  TX bytes:194384 (194.3 KB)**the RX/TX shows that internet traffic **is flowing** both ways, and according to the ASUS website, your motherboard can act as a router for another computer or network switch (that's why there are 2 ethernet RJ45 sockets on the MoBo and 2 cards listed in the **lspci** output above, I'm guessing).

I did find a few more threads here about ASUS P5Qx motherboards, and the first 2 might be helpful:

[http://ubuntuforums.org/showthread.php?t=1103467&highlight=ASUS+1742+USB&page=2](http://ubuntuforums.org/showthread.php?t=1103467&highlight=ASUS+1742+USB&page=2)

[http://ubuntuforums.org/showthread.php?t=916845&highlight=ASUS+1742+USB](http://ubuntuforums.org/showthread.php?t=916845&highlight=ASUS+1742+USB)

[http://ubuntuforums.org/showthread.php?t=903816&highlight=ASUS+1742+USB&page=2](http://ubuntuforums.org/showthread.php?t=903816&highlight=ASUS+1742+USB&page=2)

Can you post a direct link where you dowloaded the Linux drivers from?  I've unblocked the scripts in my browser, but I still cannot access the "Downloads" at that ASUS page.

eta:  Have you tried a cable connection directly to your cable modem/WiFi router to see if that works better, or is that not an option?

---

### Post by northd_tech on 2010-12-04
Hi again Max-

I found where those same wireless modules appear to be used by a Ralink 3070 USB wireless interface (yours might use the same chipset).  Chili555 found conflicting modules and found a "blacklist" fix for the Ralink 3070 USB WiFi (see posts 8-10 on this thread):

[http://ubuntuforums.org/showthread.php?t=1378782](http://ubuntuforums.org/showthread.php?t=1378782)

---

