---
title: "Dell Vostro 1400 Wireless"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by JosefF70 on 2012-12-27
Hello i just installed unbuntu 12.04 on the Dell Vostro 1400. I need help getting the wireless and hard line connected.

Thank you 

Joe

---

### Post by Pjotr123 on 2012-12-27
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by JosefF70 on 2012-12-27
i tried that route and no luck maybe it is me. I did the terminal commands and the wireless still shows as being off. Oh also when I plug a cable in it to connect to the router but it doesnt see the connection

---

### Post by JosefF70 on 2012-12-28
Hey can anyone help me ? i cant even hook a cable up to it. I know the pc works i just wiped it clean from Vista and everything worked.

thanks Joe

---

### Post by ahallubuntu on 2012-12-28
Please follow these steps and report the output here:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

I know, without a direct internet connection, it might be a pain to copy-and-paste the output.  You could save the output to a text file, save that to a thumb drive, and copy that to another computer to paste it here.

You probably have a Broadcom BCM4311 though.  I personally dislike Broadcom cards and avoid them when using Linux.  The good news is: lots of people have them and you can get them working.  Googling for "Ubuntu BCM4311" (once you've verified that that's the card you really have) might yield some more specific instructions.

---

### Post by bkratz on 2012-12-28
If it does turn out to be the BCM4311 and you can get a temporary wired connection, the two commands in the following post would take care of your wireless.

[http://ubuntuforums.org/showpost.php?p=12094989&postcount=12](http://ubuntuforums.org/showpost.php?p=12094989&postcount=12)

---

### Post by Hadaka on 2012-12-28
Hi,you can load the b43 driver for your 4311 card without
internet access. 

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
 
```

---

### Post by JosefF70 on 2012-12-29
ok i did all the commands to compile the data but I might have pasted some info in the wrong place

1 ) Machine Brand and Model (PC/Laptop):

Dell Vostro 1400 model PP26L
Code:
wirless chip set  broadcomm bcm94311mcg 802.11b/g pci express rev 2
Ethernet controller bcm5906m

andrew@andrew-Vostro-1400:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1c:23:f9:42:21  
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
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:18080 (18.0 KB)  TX bytes:18080 (18.0 KB) 

wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on    0.806434] Freeing initrd memory: 13816k freed 





4 ) Check for modules:
Code:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 05dc:a788 Lexar Media, Inc. 



5 ) Kernel boot messages
[    0.874192] isapnp: No Plug & Play device found 
[    0.932720] Linux agpgart interface v0.103 
[    0.936193] brd: module loaded 
[    0.937759] loop: module loaded 
[    0.938020] ahci 0000:00:1f.2: version 3.0 
[    0.938042] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.938122] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X 
[    0.938220] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode 
[    0.938227] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    0.938235] ahci 0000:00:1f.2: setting latency timer to 64 
[    0.944654] scsi0 : ahci 
[    0.944826] scsi1 : ahci 
[    0.944979] scsi2 : ahci 
[    0.945261] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 45 
[    0.945266] ata2: DUMMY 
[    0.945272] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 45 
[    0.945411] ata_piix 0000:00:1f.1: version 2.13 
[    0.945425] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.945479] ata_piix 0000:00:1f.1: setting latency timer to 64 
[    0.946075] scsi3 : ata_piix 
[    0.946218] scsi4 : ata_piix 
[    0.946813] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14 
[    0.946819] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15 
[    0.946946] ata5: port disabled--ignoring 
[    0.947590] Fixed MDIO Bus: probed 
[    0.947632] tun: Universal TUN/TAP device driver, 1.6 
[    0.947637] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.947840] PPP generic driver version 2.4.2 
[    0.948056] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.948084] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[    0.948108] ehci_hcd 0000:00:1a.7: setting latency timer to 64 
[    0.948114] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
[    0.948200] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1 
[    0.948242] ehci_hcd 0000:00:1a.7: debug port 1 
[    0.952151] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported 
[    0.952178] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400 
[    0.968029] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00 
[    0.968277] hub 1-0:1.0: USB hub found 
[    0.968286] hub 1-0:1.0: 4 ports detected 
[    0.968428] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.968449] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    0.968455] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    0.968545] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2 
[    0.968584] ehci_hcd 0000:00:1d.7: debug port 1 
[    0.972475] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported 
[    0.972500] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000 
[    0.988028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    0.988246] hub 2-0:1.0: USB hub found 
[    0.988254] hub 2-0:1.0: 6 ports detected 
[    0.988410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.988439] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.988470] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.988483] uhci_hcd 0000:00:1a.0: setting latency timer to 64 
[    0.988489] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
[    0.988586] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3 
[    0.988623] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20 
[    0.988862] hub 3-0:1.0: USB hub found 
[    0.988870] hub 3-0:1.0: 2 ports detected 
[    0.989003] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    0.989016] uhci_hcd 0000:00:1a.1: setting latency timer to 64 
[    0.989022] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
[    0.989110] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4 
[    0.989160] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00 
[    0.989397] hub 4-0:1.0: USB hub found 
[    0.989405] hub 4-0:1.0: 2 ports detected 
[    0.989540] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.989553] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    0.989559] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    0.989641] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5 
[    0.989677] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80 
[    0.989919] hub 5-0:1.0: USB hub found 
[    0.989926] hub 5-0:1.0: 2 ports detected 
[    0.990059] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    0.990072] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    0.990078] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    0.990164] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6 
[    0.990200] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60 
[    0.990441] hub 6-0:1.0: USB hub found 
[    0.990449] hub 6-0:1.0: 2 ports detected 
[    0.990580] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[    0.990592] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    0.990598] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    0.990693] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7 
[    0.990730] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40 
[    0.990982] hub 7-0:1.0: USB hub found 
[    0.990989] hub 7-0:1.0: 2 ports detected 
[    0.991226] usbcore: registered new interface driver libusual 
[    0.991321] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    0.994173] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.994184] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    0.994436] mousedev: PS/2 mouse device common for all mice 
[    0.994763] rtc_cmos 00:03: RTC can wake from S4 
[    0.994954] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    0.995009] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs 
[    0.995117] device-mapper: uevent: version 1.0.3 
[    0.995259] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email] 
[    0.995324] EISA: Probing bus 0 at eisa.0 
[    0.995328] EISA: Cannot allocate resource for mainboard 
[    0.995333] Cannot allocate resource for EISA slot 1 
[    0.995336] Cannot allocate resource for EISA slot 2 
[    0.995340] Cannot allocate resource for EISA slot 3 
[    0.995344] Cannot allocate resource for EISA slot 4 
[    0.995348] Cannot allocate resource for EISA slot 5 
[    0.995351] Cannot allocate resource for EISA slot 6 
[    0.995355] Cannot allocate resource for EISA slot 7 
[    0.995358] Cannot allocate resource for EISA slot 8 
[    0.995362] EISA: Detected 0 cards. 
[    0.995378] cpufreq-nforce2: No nForce2 chipset. 
[    0.995499] cpuidle: using governor ladder 
[    0.995697] cpuidle: using governor menu 
[    0.995701] EFI Variables Facility v0.08 2004-May-17 
[    0.996248] TCP cubic registered 
[    0.996485] NET: Registered protocol family 10 
[    0.997638] NET: Registered protocol family 17 
[    0.997656] Registering the dns_resolver key type 
[    0.997692] Using IPI No-Shortcut mode 
[    0.997980] PM: Hibernation image not present or could not be loaded. 
[    0.998000] registered taskstats version 1 
[    1.006060] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3 
[    1.018489]   Magic number: 8:948:393 
[    1.018622] rtc_cmos 00:03: setting system clock to 2012-12-29 18:23:11 UTC (1356805391) 
[    1.019799] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.019802] EDD information not available. 
[    1.108630] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A100, max UDMA/33 
[    1.124502] ata4.00: configured for UDMA/33 
[    1.264219] ata3: SATA link down (SStatus 0 SControl 300) 
[    1.268228] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.270947] ata1.00: ATA-8: WDC WD3200BPVT-22JJ5T0, 01.01A01, max UDMA/133 
[    1.270952] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32), AA 
[    1.273840] ata1.00: configured for UDMA/133 
[    1.274104] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BPVT-2 01.0 PQ: 0 ANSI: 5 
[    1.274347] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB) 
[    1.274351] sd 0:0:0:0: [sda] 4096-byte physical blocks 
[    1.274395] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    1.274434] sd 0:0:0:0: [sda] Write Protect is off 
[    1.274439] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.274475] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.278130] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A100 PQ: 0 ANSI: 5 
[    1.283070] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
[    1.283075] cdrom: Uniform CD-ROM driver Revision: 3.20 
[    1.283316] sr 3:0:0:0: Attached scsi CD-ROM sr0 
[    1.283473] sr 3:0:0:0: Attached scsi generic sg1 type 5 
[    1.300094] usb 2-1: new high-speed USB device number 2 using ehci_hcd 
[    1.352931]  sda: sda1 sda2 < sda5 > 
[    1.353782] sd 0:0:0:0: [sda] Attached SCSI disk 
[    1.353968] Freeing unused kernel memory: 740k freed 
[    1.354384] Write protecting the kernel text: 5816k 
[    1.354427] Write protecting the kernel read-only data: 2376k 
[    1.354430] NX-protecting the kernel data: 4424k 
[    1.380613] udevd[100]: starting version 175 
[    1.444932] Initializing USB Mass Storage driver... 
[    1.446284] scsi5 : usb-storage 2-1:1.0 
[    1.446415] usbcore: registered new interface driver usb-storage 
[    1.446419] USB Mass Storage support registered. 
[    1.503162] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    1.503177] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64 
[    1.508672] tg3.c:v3.121 (November 2, 2011) 
[    1.508700] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    1.508718] tg3 0000:09:00.0: setting latency timer to 64 
[    1.520184] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243) 
[    1.520198] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243) 
[    1.520210] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243) 
[    1.520226] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243) 
[    1.530743] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    1.538840] sdhci: Secure Digital Host Controller Interface driver 
[    1.538844] sdhci: Copyright(c) Pierre Ossman 
[    1.560652] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1c:23:f9:42:21 
[    1.560659] tg3 0000:09:00.0: eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0]) 
[    1.560665] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0] 
[    1.560669] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit] 
[    1.584234] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0 
[    1.592210] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11 
[    1.592329] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22) 
[    1.592363] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
[    1.593418] mmc0: no vmmc regulator found 
[    1.594461] Registered led device: mmc0:: 
[    1.596511] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA 
[    1.803165] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null) 
[    2.092243] firewire_core: created device fw0: GUID 334fc000371391a1, S400 
[    2.445124] scsi 5:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS 
[    2.446313] sd 5:0:0:0: Attached scsi generic sg2 type 0 
[    2.446832] sd 5:0:0:0: [sdb] 31326208 512-byte logical blocks: (16.0 GB/14.9 GiB) 
[    2.447445] sd 5:0:0:0: [sdb] Write Protect is off 
[    2.447451] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00 
[    2.448081] sd 5:0:0:0: [sdb] No Caching mode page present 
[    2.448086] sd 5:0:0:0: [sdb] Assuming drive cache: write through 
[    2.451205] sd 5:0:0:0: [sdb] No Caching mode page present 
[    2.451210] sd 5:0:0:0: [sdb] Assuming drive cache: write through 
[    2.452306]  sdb: sdb1 
[    2.454457] sd 5:0:0:0: [sdb] No Caching mode page present 
[    2.454462] sd 5:0:0:0: [sdb] Assuming drive cache: write through 
[    2.454467] sd 5:0:0:0: [sdb] Attached SCSI removable disk 
[   11.049174] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   11.066862] udevd[332]: starting version 175 
[   11.126328] Adding 4191228k swap on /dev/sda5.  Priority:-1 extents:1 across:4191228k 
[   11.141662] lp: driver loaded but no devices found 
[   11.257060] wmi: Mapper loaded 
[   11.292393] acpi device:31: registered as cooling_device2 
[   11.293068] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input4 
[   11.293192] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no) 
[   11.293268] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work. 
[   11.297383] type=1400 audit(1356805401.773:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=419 comm="apparmor_parser" 
[   11.298073] type=1400 audit(1356805401.773:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=419 comm="apparmor_parser" 
[   11.298460] type=1400 audit(1356805401.773:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=419 comm="apparmor_parser" 
[   11.355509] [drm] Initialized drm 1.1.0 20060810 
[   11.437901] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro 
[   11.440784] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
[   11.441992] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   11.442002] nouveau 0000:01:00.0: setting latency timer to 64 
[   11.445414] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x086700a2) 

  11.454898] r592: driver successfully loaded 
[   11.455348] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN 
[   11.575943] [drm] nouveau 0000:01:00.0: ... appears to be valid 
[   11.575950] [drm] nouveau 0000:01:00.0: BIT BIOS found 
[   11.575954] [drm] nouveau 0000:01:00.0: Bios version 60.86.45.00 
[   11.575960] [drm] nouveau 0000:01:00.0: TMDS table version 2.0 
[   11.575964] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0 
[   11.575969] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000323 00010034 
[   11.575974] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000028 
[   11.575977] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 010223f1 00c0c080 
[   11.575981] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000 
[   11.575987] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 14 2 
[   11.575991] [drm] nouveau 0000:01:00.0:   0: 0x00000041: type 0x41 idx 0 tag 0xff 
[   11.575996] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff 
[   11.576023] [drm] nouveau 0000:01:00.0:   2: 0x00000310: type 0x10 idx 2 tag 0xff 
[   11.576028] [drm] nouveau 0000:01:00.0:   3: 0x00000311: type 0x11 idx 3 tag 0xff 
[   11.576032] [drm] nouveau 0000:01:00.0:   4: 0x00000313: type 0x13 idx 4 tag 0xff 
[   11.576039] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xC42B 
[   11.599159] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xC76B 
[   11.602466] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
[   11.606930] cfg80211: Calling CRDA to update world regulatory domain 
[   11.615900] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD1C0 
[   11.615913] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD2B2 
[   11.617001] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xD4AC 
[   11.617011] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xD511 
[   11.618701] r852: driver loaded successfully 
[   11.626036] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
[   11.636862] [drm] nouveau 0000:01:00.0: 0xD511: Condition still not met after 20ms, skipping following opcodes 
[   12.133511] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[   12.133598] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X 
[   12.133643] snd_hda_intel 0000:00:1b.0: setting latency timer to 64 
[   12.156963] [drm] nouveau 0000:01:00.0: 3 available performance level(s) 
[   12.156972] [drm] nouveau 0000:01:00.0: 0: core 169MHz shader 338MHz memory 100MHz timing 0 voltage 1150mV fanspeed 100% 
[   12.156979] [drm] nouveau 0000:01:00.0: 1: core 275MHz shader 550MHz memory 300MHz timing 0 voltage 1150mV fanspeed 100% 
[   12.156986] [drm] nouveau 0000:01:00.0: 2: core 400MHz shader 800MHz memory 500MHz timing 2 voltage 1150mV fanspeed 100% 
[   12.157016] [drm] nouveau 0000:01:00.0: c: core 275MHz shader 550MHz memory 399MHz voltage 1150mV 
[   12.174692] [TTM] Zone  kernel: Available graphics memory: 423522 kiB. 
[   12.174697] [TTM] Zone highmem: Available graphics memory: 2063164 kiB. 
[   12.174700] [TTM] Initializing pool allocator. 
[   12.174717] [drm] nouveau 0000:01:00.0: Detected 128MiB VRAM 
[   12.174727] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining 
[   12.174751] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture) 
[   12.198550] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input5 
[   12.202722] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown 
[   12.202727] [drm] nouveau 0000:01:00.0: TV-1 has no encoders, removing 
[   12.206158] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
[   12.206781] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own 
[   12.214829] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6 
[   12.255663] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010). 
[   12.255667] [drm] No driver support for vblank timestamp query. 
[   12.272465] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272471] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272475] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272479] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272483] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272488] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272491] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272496] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272499] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272504] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272507] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272512] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272516] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272520] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272524] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272528] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272532] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272536] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272540] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272544] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272548] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272552] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm) 
[   12.272556] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272560] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm) 
[   12.272564] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272568] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm) 
[   12.272572] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule: 
[   12.272576] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm) 
[   12.290677] input: Dell WMI hotkeys as /devices/virtual/input/input7 
[   12.342086] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342093] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342097] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342101] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342105] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342109] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342113] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342118] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342122] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342126] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342130] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342135] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342138] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342143] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342146] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342151] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342155] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342163] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342167] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342171] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342175] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342179] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342183] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.342187] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342191] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.342195] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule: 
[   12.342200] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.342204] cfg80211: World regulatory domain updated: 
[   12.342207] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   12.342212] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342216] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.342220] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.342224] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.342228] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.397202] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht' 
[   12.398282] Registered led device: b43-phy0::tx 
[   12.398321] Registered led device: b43-phy0::rx 
[   12.398357] Registered led device: b43-phy0::radio 
[   12.398381] Broadcom 43xx driver loaded [ Features: PNL ] 
[   12.466094] [drm] nouveau 0000:01:00.0: allocated 1280x800 fb: 0x310000, bo f11b3a00 
[   12.466216] fbcon: nouveaufb (fb0) is primary device 
[   12.466344] Console: switching to colour frame buffer device 160x50 
[   12.466387] fb0: nouveaufb frame buffer device 
[   12.466390] drm: registered panic notifier 
[   12.466400] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0 
[   12.604768] init: failsafe main process (664) killed by TERM signal 
[   12.633337] Bluetooth: Core ver 2.16 
[   12.633570] NET: Registered protocol family 31 
[   12.633574] Bluetooth: HCI device and connection manager initialized 
[   12.633579] Bluetooth: HCI socket layer initialized 
[   12.633582] Bluetooth: L2CAP socket layer initialized 
[   12.633592] Bluetooth: SCO socket layer initialized 
[   12.642202] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   12.642207] Bluetooth: BNEP filters: protocol multicast 
[   12.663083] ppdev: user-space parallel port driver 
[   12.809591] Bluetooth: RFCOMM TTY layer initialized 
[   12.809600] Bluetooth: RFCOMM socket layer initialized 
[   12.809603] Bluetooth: RFCOMM ver 1.11 
[   12.948921] type=1400 audit(1356805403.425:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=752 comm="apparmor_parser" 
[   12.953369] type=1400 audit(1356805403.429:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=752 comm="apparmor_parser" 
[   13.237919] type=1400 audit(1356805403.713:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=805 comm="apparmor_parser" 
[   13.238621] type=1400 audit(1356805403.713:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=805 comm="apparmor_parser" 
[   13.239014] type=1400 audit(1356805403.713:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=805 comm="apparmor_parser" 
[   13.239089] type=1400 audit(1356805403.713:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=804 comm="apparmor_parser" 
[   13.256787] type=1400 audit(1356805403.733:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=806 comm="apparmor_parser" 
[   13.304629] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   13.304635] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   13.304640] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   13.304873] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   13.308277] tg3 0000:09:00.0: irq 47 for MSI/MSI-X 
[   13.340699] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   13.341437] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   13.731355] init: anacron main process (890) killed by TERM signal 
[   46.822947] audit_printk_skb: 36 callbacks suppressed 
[   46.822952] type=1400 audit(1356805437.297:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1822 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0 




6 ) Network configuration
*-network                
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:f9ffc000-f9ffffff 
  *-network 
       description: Ethernet interface 
       product: NetLink BCM5906M Fast Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1c:23:f9:42:21 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:47 memory:f9bf0000-f9bfffff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:1e:4c:13:ac:23 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-29-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg 
andrew@andrew-Vostro-1400:


7 ) Scan for networks:
lo        Interface doesn't support scanning. 

wlan0     Failed to read scan data : Network is down 

eth0      Interface doesn't support scanning. 

8 ) Ubuntu Version: 
12.04.1 lts
9 ) Kernel/architecture (including 32 vs. 64 bit)
3.2.0-29-generic-PAE I686
10. restart network
restarting the network
andrew@andrew-Vostro-1400:~$ sudo /etc/init.d/networking restart 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
 * Reconfiguring network interfaces...                                                                                         [ OK ] 
andrew@andrew-Vostro-1400:~$

---

### Post by Hadaka on 2012-12-29
Hi you need..

```
sudo apt-get install linux-firmware-nonfree 
```but...you need a wired connection to get that and i dont have
a zip file for that.

How did you load ubuntu on that machine?

---

### Post by JosefF70 on 2012-12-29
Hey Hadaka 

i tried your way and this is what i got:

andrew@andrew-Vostro-1400:~$ sudo mkdir /lib/firmware/b43
[sudo] password for andrew: 
mkdir: cannot create directory `/lib/firmware/b43': File exists
andrew@andrew-Vostro-1400:~$ sudo cp Desktop/43/* /lib/firmware/b43
cp: cannot stat `Desktop/43/*': No such file or directory
andrew@andrew-Vostro-1400:~$ sudo cp Desktop/b43/* /lib/firmare/b43
cp: target `/lib/firmare/b43' is not a directory
andrew@andrew-Vostro-1400:~$ sudormmod -f b43
sudormmod: command not found
andrew@andrew-Vostro-1400:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': Resource temporarily unavailable
andrew@andrew-Vostro-1400:~$ sudo modprobe b43
andrew@andrew-Vostro-1400:~$

---

### Post by JosefF70 on 2012-12-29
hey Bkratz

i tried your way:

andrew@andrew-Vostro-1400:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
E: Unable to locate package broadcom-sta-common
E: Unable to locate package broadcom-sta-source
andrew@andrew-Vostro-1400:~$ 


thanks

Joe

---

### Post by JosefF70 on 2012-12-29
hey Bkratz

i tried your way:

andrew@andrew-Vostro-1400:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
E: Unable to locate package broadcom-sta-common
E: Unable to locate package broadcom-sta-source
andrew@andrew-Vostro-1400:~$ 


thanks

---

### Post by Hadaka on 2012-12-29
ok how did you transfer the b43 zip file to the ubuntu machine?
and did you copy and paste the commands after extracted the
zip file in the Desktop? and again.how did you load ubuntu on
the vostro?

---

### Post by JosefF70 on 2012-12-29
Hello I loaded unbuntu up on the vostro from a disk that I burned. I used a iso burning program. I put the zip file on a flash drive, then extracted it to he desk top. i hand typed the commands but i will copy the commands put them on a file and use the flash drive to past the commands to the terminal


Joe

---

### Post by JosefF70 on 2012-12-29
Haddaka

I copied everything and pasted it. thank you very much it worked. now what was it that you had me do? I assume the zip was a driver download?

Joe

---

### Post by drivingmemad on 2012-12-29
Hi JosefF70,
If its any help I had a similar issue on my Dell1720. See this post

[http://ubuntuforums.org/showthread.php?t=2048958](http://ubuntuforums.org/showthread.php?t=2048958)

Hope this helps :D

---

### Post by Hadaka on 2012-12-29
Glad you got it working....yes..the zip file was the b43 driver
please use thread tools and mark this thread SOLVED
thanks.

---

### Post by JosefF70 on 2012-12-29
Thank you everyone for helping... Especially Hadaka!

Joe

---

