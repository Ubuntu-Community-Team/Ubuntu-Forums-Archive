---
title: "Wireless stopped working"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by shivae on 2010-05-25
Hi,

I updated to 10.04 recently and everyhting worked fine. Yesterday my wireless stopped working. Now I just get "Networking disabled" when I mouse over the greyed out wireless icon. Everything still works fine when I boot windows.

Here's the details from the HOWTO log an wireless issue guide  [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) . sorry for the length of dmesg and lsmod , I couldn't figure out how to add a spoiler tag on this forum.

Machine Brand:
Dell Latitude D531

Wireless Details:
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


$ifconfig

lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128  Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:50 errors:0 dropped:0 overruns:0 frame:0
           TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:5160 (5.1 KB)  TX  bytes:5160 (5.1 KB)

$iwconfig

lo        no wireless  extensions.

eth0      no wireless extensions.

eth2       IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5   Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid  crypt:0  invalid misc:0

pan0      no wireless extensions.

%lsmod

Module                   Size  Used by
rfcomm                 33421  4 
binfmt_misc              6587  1 
fbcon                  35102  71 
tileblit                 2031  1 fbcon
font                    7557  1 fbcon
bitblit                  4707  1 fbcon
softcursor              1189  1  bitblit
vga16fb                11385  0 
vgastate                 8961  1 vga16fb
ppdev                   5259  0 
sco                      7885  2 
bridge                 45582  0 
stp                      1655  1 bridge
bnep                    9436  2 
l2cap                   30624  16 rfcomm,bnep
snd_hda_codec_idt      51914  1 
joydev                   8708  0 
snd_hda_intel          21877  2 
snd_hda_codec           74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep                5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss           13746  1 snd_pcm_oss
snd_pcm                70662  3  snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy            1338  0 
snd_seq_oss            26726  0 
snd_seq_midi             4557  0 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                  33024  0 
snd_seq_midi_event      6003  2  snd_seq_oss,snd_seq_midi
snd_seq                47263  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                 674135  3 
snd_timer              19098  2  snd_pcm,snd_seq
snd_seq_device          5700  5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                     49943  1 radeon
drm_kms_helper         29297  1  radeon
dell_wmi                1793  0 
yenta_socket            20408  1 
rsrc_nonstatic         10015  1 yenta_socket
lib80211_crypt_tkip      7596  0 
snd                    54148  16  snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                    162471  5 radeon,ttm,drm_kms_helper
i2c_algo_bit             5028  1 radeon
pcmcia_core            32964  3  pcmcia,yenta_socket,rsrc_nonstatic
dell_laptop             6856   0 
dcdbas                  5422  1 dell_laptop
btusb                   10925  2 
bluetooth              49892  9  rfcomm,sco,bnep,l2cap,btusb
psmouse                63245  0 
serio_raw                3978  0 
k8temp                  3024  0 
ati_agp                  5094  0 
video                  17375  0 
output                   1871  1 video
i2c_piix4               8335  0 
soundcore                6620  1 snd
snd_page_alloc          7076  2  snd_hda_intel,snd_pcm
wl                   1959598  0 
lib80211                 5046  2 lib80211_crypt_tkip,wl
shpchp                  28820  0 
agpgart                31724  3 ttm,drm,ati_agp
lp                       7028  0 
parport                32635  2 ppdev,lp
ohci1394                26950  0 
ieee1394               81181  1 ohci1394
pata_atiixp              3148  0 
tg3                   109292  0 
ahci                    32008  2 


$dmesg

[    0.329052]  cpufreq-nforce2: No nForce2 chipset.
[    0.329077] Scanning for low  memory corruption every 60 seconds
[    0.329181] audit: initializing  netlink socket (disabled)
[    0.329191] type=2000  audit(1274870992.328:1): initialized
[    0.339351] Trying to unpack  rootfs image as initramfs...
[    0.352089] highmem bounce pool size:  64 pages
[    0.352095] HugeTLB registered 4 MB page size,  pre-allocated 0 pages
[    0.353502] VFS: Disk quotas dquot_6.5.2
[     0.353560] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[     0.360342] fuse init (API version 7.13)
[    0.360453] msgmni has  been set to 1693
[    0.360670] alg: No test for stdrng (krng)
[     0.360727] Block layer SCSI generic (bsg) driver version 0.4 loaded  (major 253)
[    0.360730] io scheduler noop registered
[     0.360732] io scheduler anticipatory registered
[    0.360735] io  scheduler deadline registered
[    0.360779] io scheduler cfq  registered (default)
[    0.360908]   alloc irq_desc for 24 on node  -1
[    0.360911]   alloc kstat_irqs on node -1
[    0.360919]  pcieport 0000:00:05.0: irq 24 for MSI/MSI-X
[    0.360925] pcieport  0000:00:05.0: setting latency timer to 64
[    0.360995]   alloc  irq_desc for 25 on node -1
[    0.360997]   alloc kstat_irqs on node  -1
[    0.361002] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
[     0.361007] pcieport 0000:00:06.0: setting latency timer to 64
[     0.361065] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[     0.361090] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[     0.361216] ACPI: AC Adapter [AC] (on-line)
[    0.361286] input:  Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[     0.361747] ACPI: Lid Switch [LID]
[    0.361790] input: Power  Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[     0.361799] ACPI: Power Button [PBTN]
[    0.361843] input: Sleep  Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[     0.361846] ACPI: Sleep Button [SBTN]
[    0.362121] processor  LNXCPU:00: registered as cooling_device0
[    0.406230] thermal  LNXTHERM:01: registered as thermal_zone0
[    0.406240] ACPI: Thermal  Zone [THM] (65 C)
[    0.407758] Serial: 8250/16550 driver, 4 ports,  IRQ sharing enabled
[    0.407881] serial8250: ttyS0 at I/O 0x3f8  (irq = 4) is a 16550A
[    0.408257] 00:09: ttyS0 at I/O 0x3f8 (irq =  4) is a 16550A
[    0.409222] brd: module loaded
[    0.409660]  loop: module loaded
[    0.409754] input: Macintosh mouse button  emulation as /devices/virtual/input/input3
[    0.409895]   alloc  irq_desc for 16 on node -1
[    0.409897]   alloc kstat_irqs on node  -1
[    0.409905] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16  (level, low) -> IRQ 16
[    0.410239] Fixed MDIO Bus: probed
[     0.410272] PPP generic driver version 2.4.2
[    0.410312] tun:  Universal TUN/TAP device driver, 1.6
[    0.410314] tun: (C)  1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[    0.410400] ehci_hcd:  USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.410420]    alloc irq_desc for 20 on node -1
[    0.410421]   alloc kstat_irqs on  node -1
[    0.410426] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 20  (level, low) -> IRQ 20
[    0.410443] ehci_hcd 0000:00:13.5: EHCI  Host Controller
[    0.410472] ehci_hcd 0000:00:13.5: new USB bus  registered, assigned bus number 1
[    0.410497] ehci_hcd  0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[     0.410511] ehci_hcd 0000:00:13.5: debug port 1
[    0.410533] ehci_hcd  0000:00:13.5: irq 20, io mem 0xffa80000
[    0.416497] ACPI: Battery  Slot [BAT0] (battery absent)
[    0.416532] ACPI: Battery Slot  [BAT1] (battery absent)
[    0.416551] isapnp: Scanning for PnP  cards...
[    0.422100] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI  1.00
[    0.422225] usb usb1: configuration #1 chosen from 1 choice
[     0.422253] hub 1-0:1.0: USB hub found
[    0.422264] hub 1-0:1.0:  10 ports detected
[    0.422346] ohci_hcd: USB 1.1 'Open' Host  Controller (OHCI) Driver
[    0.422367] ohci_hcd 0000:00:13.0: PCI  INT A -> GSI 16 (level, low) -> IRQ 16
[    0.422386] ohci_hcd  0000:00:13.0: OHCI Host Controller
[    0.422421] ohci_hcd  0000:00:13.0: new USB bus registered, assigned bus number 2
[     0.422452] ohci_hcd 0000:00:13.0: irq 16, io mem 0xffb00000
[     0.484332] usb usb2: configuration #1 chosen from 1 choice
[     0.484362] hub 2-0:1.0: USB hub found
[    0.484378] hub 2-0:1.0: 2  ports detected
[    0.484434]   alloc irq_desc for 17 on node -1
[     0.484436]   alloc kstat_irqs on node -1
[    0.484444] ohci_hcd  0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[     0.484462] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.484498]  ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[     0.484529] ohci_hcd 0000:00:13.1: irq 17, io mem 0xffb01000
[     0.568261] usb usb3: configuration #1 chosen from 1 choice
[     0.568289] hub 3-0:1.0: USB hub found
[    0.568305] hub 3-0:1.0: 2  ports detected
[    0.568361]   alloc irq_desc for 18 on node -1
[     0.568364]   alloc kstat_irqs on node -1
[    0.568371] ohci_hcd  0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[     0.568390] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.568432]  ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[     0.568463] ohci_hcd 0000:00:13.2: irq 18, io mem 0xffb02000
[     0.660288] usb usb4: configuration #1 chosen from 1 choice
[     0.660325] hub 4-0:1.0: USB hub found
[    0.660341] hub 4-0:1.0: 2  ports detected
[    0.660394] ohci_hcd 0000:00:13.3: PCI INT B ->  GSI 17 (level, low) -> IRQ 17
[    0.660413] ohci_hcd  0000:00:13.3: OHCI Host Controller
[    0.660451] ohci_hcd  0000:00:13.3: new USB bus registered, assigned bus number 5
[     0.660474] ohci_hcd 0000:00:13.3: irq 17, io mem 0xffb03000
[     0.752459] usb usb5: configuration #1 chosen from 1 choice
[     0.752492] hub 5-0:1.0: USB hub found
[    0.752507] hub 5-0:1.0: 2  ports detected
[    0.752561] ohci_hcd 0000:00:13.4: PCI INT C ->  GSI 18 (level, low) -> IRQ 18
[    0.752581] ohci_hcd  0000:00:13.4: OHCI Host Controller
[    0.752617] ohci_hcd  0000:00:13.4: new USB bus registered, assigned bus number 6
[     0.752640] ohci_hcd 0000:00:13.4: irq 18, io mem 0xffb04000
[     0.785906] Freeing initrd memory: 7778k freed
[    0.834233] hub  1-0:1.0: unable to enumerate USB device on port 8
[    0.838402] usb  usb6: configuration #1 chosen from 1 choice
[    0.838431] hub  6-0:1.0: USB hub found
[    0.838447] hub 6-0:1.0: 2 ports detected
[     0.838506] uhci_hcd: USB Universal Host Controller Interface driver
[     0.838588] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at  0x60,0x64 irq 1,12
[    0.841484] serio: i8042 KBD port at 0x60,0x64  irq 1
[    0.841492] serio: i8042 AUX port at 0x60,0x64 irq 12
[     0.841612] mice: PS/2 mouse device common for all mice
[     0.841739] rtc_cmos 00:03: RTC can wake from S4
[    0.841777]  rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.841808]  rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[     0.841911] device-mapper: uevent: version 1.0.3
[    0.842034]  device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[     0.842088] device-mapper: multipath: version 1.1.0 loaded
[     0.842091] device-mapper: multipath round-robin: version 1.0.0 loaded
[     0.842211] EISA: Probing bus 0 at eisa.0
[    0.842215] EISA:  Cannot allocate resource for mainboard
[    0.842218] Cannot allocate  resource for EISA slot 1
[    0.842220] Cannot allocate resource for  EISA slot 2
[    0.842248] EISA: Detected 0 cards.
[    0.842317]  cpuidle: using governor ladder
[    0.842359] cpuidle: using  governor menu
[    0.842779] TCP cubic registered
[    0.842929]  NET: Registered protocol family 10
[    0.843351] lo: Disabled  Privacy Extensions
[    0.843649] NET: Registered protocol family 17
[     0.843679] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor  3600+ processors (1 cpu cores) (version 2.20.00)
[    0.843726]  powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[    0.843729]  powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xf
[    0.843732]  powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x10
[    0.843736]  powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[    0.843773] Using  IPI No-Shortcut mode
[    0.843860] PM: Resume from disk failed.
[     0.843875] registered taskstats version 1
[    0.844303]   Magic  number: 10:793:831
[    0.844393] rtc_cmos 00:03: setting system  clock to 2010-05-26 10:49:53 UTC (1274870993)
[    0.844397] BIOS EDD  facility v0.16 2004-Jun-25, 0 devices found
[    0.844400] EDD  information not available.
[    0.975266] isapnp: No Plug & Play  device found
[    0.975294] Freeing unused kernel memory: 656k freed
[     0.975726] Write protecting the kernel text: 4676k
[    0.975757]  Write protecting the kernel read-only data: 1840k
[    0.976702]  input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[     0.997495] udev: starting version 151
[    1.293738] ahci  0000:00:12.0: version 3.0
[    1.293760]   alloc irq_desc for 22 on  node -1
[    1.293763]   alloc kstat_irqs on node -1
[     1.293771] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) ->  IRQ 22
[    1.293800] ahci 0000:00:12.0: controller can't do 64bit  DMA, forcing 32bit
[    1.293894] ahci 0000:00:12.0: AHCI 0001.0100  32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.293898] ahci  0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[     1.296432] tg3.c:v3.102 (September 1, 2009)
[    1.296488] tg3  0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[     1.296496] tg3 0000:09:00.0: setting latency timer to 64
[     1.308768] scsi0 : ahci
[    1.308997] scsi1 : ahci
[    1.309104]  scsi2 : ahci
[    1.309196] scsi3 : ahci
[    1.309375] ata1: SATA  max UDMA/133 abar m1024@0xfec01000 port 0xfec01100 irq 22
[     1.309381] ata2: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01180  irq 22
[    1.309385] ata3: SATA max UDMA/133 abar m1024@0xfec01000  port 0xfec01200 irq 22
[    1.309390] ata4: SATA max UDMA/133 abar  m1024@0xfec01000 port 0xfec01280 irq 22
[    1.309783] scsi4 :  pata_atiixp
[    1.309901] scsi5 : pata_atiixp
[    1.311363]  ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[     1.311367] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq  15
[    1.321230] usb 5-2: new full speed USB device using ohci_hcd  and address 2
[    1.321855] eth0: Tigon3 [partno(BCM95755m) rev  a002] (PCI Express) MAC address 00:1d:09:b0:10:b7
[    1.321859]  eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[     1.321862] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[     1.321865] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[     1.472516] ata5.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A100, max UDMA/33
[     1.488475] ata5.00: configured for UDMA/33
[    1.505664] usb 5-2:  configuration #1 chosen from 1 choice
[    1.632055] ata3: SATA link  down (SStatus 0 SControl 300)
[    1.632087] ata4: SATA link down  (SStatus 0 SControl 300)
[    1.632116] ata2: SATA link down (SStatus  0 SControl 300)
[    1.796035] ata1: softreset failed (device not  ready)
[    1.796038] ata1: applying SB600 PMP SRST workaround and  retrying
[    1.960045] ata1: SATA link up 1.5 Gbps (SStatus 113  SControl 300)
[    2.011555] ata1.00: ATA-8: WDC WD1200BEVS-75UST0,  01.01A01, max UDMA/133
[    2.011558] ata1.00: 234441648 sectors,  multi 8: LBA48 NCQ (depth 31/32), AA
[    2.011580] ata1.00: SB600  AHCI: limiting to 255 sectors per cmd
[    2.012532] ata1.00: SB600  AHCI: limiting to 255 sectors per cmd
[    2.012535] ata1.00:  configured for UDMA/133
[    2.028137] scsi 0:0:0:0: Direct-Access      ATA      WDC WD1200BEVS-7 01.0 PQ: 0 ANSI: 5
[    2.028291] sd  0:0:0:0: Attached scsi generic sg0 type 0
[    2.028666] sd 0:0:0:0:  [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[     2.028710] sd 0:0:0:0: [sda] Write Protect is off
[    2.028713] sd  0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.028736] sd 0:0:0:0:  [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or  FUA
[    2.028864]  sda:
[    2.031924] scsi 4:0:0:0: CD-ROM             HL-DT-ST DVD+-RW GSA-T21N A100 PQ: 0 ANSI: 5
[    2.040513]   sda1 sda2 < sda5sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2  cdda tray
[    2.042937] Uniform CD-ROM driver Revision: 3.20
[     2.043214] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.043335] sr  4:0:0:0: Attached scsi generic sg1 type 5
[    2.057968]  sda6 >
[     2.058532] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.199779]  ohci1394 0000:03:01.4: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[     2.253081] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]   MMIO=[fe6ff000-fe6ff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[     2.575277] EXT4-fs (sda5): mounted filesystem with ordered data mode
[     3.524149] ieee1394: Host added: ID:BUS[0-00:1023]   GUID[4a4fc0002d07e438]
[   14.856313] udev: starting version 151
[    14.901562] Adding 2530196k swap on /dev/sda6.  Priority:-1 extents:1  across:2530196k 
[   14.943832] lp: driver loaded but no devices  found
[   15.046072] lib80211: common routines for IEEE802.11 drivers
[    15.046076] lib80211_crypt: registered algorithm 'NULL'
[    15.048130] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    15.051088] wl: module license 'MIXED/Proprietary' taints kernel.
[    15.051091] Disabling lock debugging due to kernel taint
[    15.054564] Linux agpgart interface v0.103
[   15.376053] type=1505  audit(1274835008.031:2):  operation="profile_load" pid=567  name="/sbin/dhclient3"
[   15.376460] type=1505  audit(1274835008.031:3):  operation="profile_load" pid=567  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    15.376619] type=1505 audit(1274835008.031:4):  operation="profile_load"  pid=567 name="/usr/lib/connman/scripts/dhclient-script"
[    15.431887] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x10c0,  revision 0
[   15.439393] k8temp 0000:00:18.3: Temperature readouts  might be wrong - check erratum #141
[   15.464783] input: Video Bus  as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2c/LNXVIDEO:00/input/input5
[    15.464836] ACPI: Video Device [VID] (multi-head: yes  rom: no  post:  no)
[   15.466263] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level,  low) -> IRQ 17
[   15.466275] wl 0000:0b:00.0: setting latency  timer to 64
[   15.493280] Bluetooth: Core ver 2.15
[   15.498112]  NET: Registered protocol family 31
[   15.498115] Bluetooth: HCI  device and connection manager initialized
[   15.498119] Bluetooth:  HCI socket layer initialized
[   15.502166] dcdbas dcdbas: Dell  Systems Management Base Driver (version 5.6.0-3.2)
[   15.511990]  Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.512263]  usbcore: registered new interface driver btusb
[   15.668893] [drm]  Initialized drm 1.1.0 20060810
[   15.688829] lib80211_crypt:  registered algorithm 'TKIP'
[   15.690252] input: Dell WMI hotkeys as  /devices/virtual/input/input6
[   15.696763] yenta_cardbus  0000:03:01.0: CardBus bridge found [1028:0206]
[   15.696793]  yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[    15.696796] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write  burst
[   15.711249] eth1: Broadcom BCM4311 802.11 Hybrid Wireless  Controller 5.60.48.36 
[   15.762631] udev: renamed network interface  eth1 to eth2
[   15.825043] yenta_cardbus 0000:03:01.0: ISA IRQ mask  0x0cb8, PCI irq 23
[   15.825049] yenta_cardbus 0000:03:01.0: Socket  status: 30000006
[   15.825053] pci_bus 0000:03: Raising subordinate  bus# of parent bus (#03) from #04 to #07
[   15.825063]  yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000  - 0x2fff
[   15.825068] pcmcia_socket pcmcia_socket0: cs: IO port  probe 0x2000-0x2fff: clean.
[   15.825272] yenta_cardbus  0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xfe600000 -  0xfe6fffff
[   15.825275] yenta_cardbus 0000:03:01.0: pcmcia: parent  PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   15.862753]  [drm] radeon defaulting to kernel modesetting.
[   15.862758] [drm]  radeon kernel modesetting enabled.
[   15.862832]   alloc irq_desc  for 19 on node -1
[   15.862835]   alloc kstat_irqs on node -1
[    15.862842] radeon 0000:01:05.0: PCI INT B -> GSI 19 (level, low)  -> IRQ 19
[   15.873980] [drm] radeon: Initializing kernel  modesetting.
[   15.877405] [drm] register mmio base: 0xFE9F0000
[    15.877408] [drm] register mmio size: 65536
[   15.877537] ATOM  BIOS: ATI
[   15.877756] [drm] GPU reset succeed  (RBBM_STATUS=0x10000140)
[   15.877773] [drm] radeon: VRAM 160M
[    15.877775] [drm] radeon: VRAM from 0x76000000 to 0x7FFFFFFF
[    15.877777] [drm] radeon: GTT 512M
[   15.877779] [drm] radeon: GTT  from 0x80000000 to 0x9FFFFFFF
[   15.877814]   alloc irq_desc for 26  on node -1
[   15.877817]   alloc kstat_irqs on node -1
[    15.877826] radeon 0000:01:05.0: irq 26 for MSI/MSI-X
[   15.877830]  [drm] radeon: using MSI.
[   15.877855] [drm] radeon: irq  initialized.
[   15.877930] [drm] Detected VRAM RAM=160M, BAR=256M
[    15.877935] [drm] RAM width 128bits DDR
[   15.888130] [TTM] Zone   kernel: Available graphics memory: 437780 kiB.
[   15.888134] [TTM]  Zone highmem: Available graphics memory: 965508 kiB.
[   15.888151]  [drm] radeon: 160M of VRAM memory ready
[   15.888153] [drm] radeon:  512M of GTT memory ready.
[   15.888170] [drm] GART: num cpu pages  131072, num gpu pages 131072
[   15.891791] [drm] radeon: 1 quad  pipes, 1 z pipes initialized.
[   15.891849] [drm] radeon: cp idle  (0x10000C03)
[   15.891951] [drm] Loading RS690/RS740 Microcode
[    15.892372] platform radeon_cp.0: firmware: requesting  radeon/RS690_cp.bin
[   15.944627] [drm] radeon: ring at  0x0000000080000000
[   15.944648] [drm] ring test succeeded in 1  usecs
[   15.944775] [drm] radeon: ib pool ready.
[   15.944840]  [drm] ib test succeeded in 0 usecs
[   15.944974] [drm] Default TV  standard: NTSC
[   15.945038] [drm] Radeon Display Connectors
[    15.945040] [drm] Connector 0:
[   15.945042] [drm]   VGA
[    15.945045] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c  0x7e4c
[   15.945047] [drm]   Encoders:
[   15.945049] [drm]      CRT1: INTERNAL_KLDSCP_DAC1
[   15.945052] [drm] Connector 1:
[    15.945053] [drm]   LVDS
[   15.945056] [drm]   DDC: 0x7e40 0x7e50  0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   15.945058] [drm]    Encoders:
[   15.945060] [drm]     LCD1: INTERNAL_LVTM1
[    15.945062] [drm] Connector 2:
[   15.945064] [drm]   S-video
[    15.945065] [drm]   Encoders:
[   15.945067] [drm]     TV1:  INTERNAL_KLDSCP_DAC1
[   15.945069] [drm] Connector 3:
[    15.945071] [drm]   DVI-D
[   15.945073] [drm]   HPD2
[    15.945075] [drm]   DDC: 0x7e40 0x7e60 0x7e44 0x7e64 0x7e48 0x7e68 0x7e4c  0x7e6c
[   15.945078] [drm]   Encoders:
[   15.945080] [drm]      DFP2: INTERNAL_DDI
[   16.036383] HDA Intel 0000:00:14.2: PCI INT A  -> GSI 16 (level, low) -> IRQ 16
[   16.127844] input:  DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[    16.146757] input: AlpsPS/2 ALPS DualPoint TouchPad as  /devices/platform/i8042/serio1/input/input8
[   16.204951]  type=1505 audit(1274835008.859:5):  operation="profile_load" pid=812  name="/usr/share/gdm/guest-session/Xsession"
[   16.214236]  type=1505 audit(1274835008.867:6):  operation="profile_replace" pid=815  name="/sbin/dhclient3"
[   16.214536] type=1505  audit(1274835008.867:7):  operation="profile_replace" pid=815  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    16.214700] type=1505 audit(1274835008.867:8):   operation="profile_replace" pid=815 name="/usr/lib/connman/scripts/dhclient-script"
[    16.217001] pcmcia_socket pcmcia_socket0: cs: IO port probe  0x100-0x3af: clean.
[   16.218965] pcmcia_socket pcmcia_socket0: cs:  IO port probe 0x3e0-0x4ff: clean.
[   16.219750] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.220831]  pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding  0xcd8-0xcdf
[   16.221384] pcmcia_socket pcmcia_socket0: cs: IO port  probe 0xa00-0xaff: clean.
[   16.238839] type=1505  audit(1274835008.891:9):  operation="profile_load" pid=817  name="/usr/bin/evince"
[   16.242757] input: HDA Digital PCBeep as  /devices/pci0000:00/0000:00:14.2/input/input9
[   16.265206]  type=1505 audit(1274835008.919:10):  operation="profile_load" pid=817  name="/usr/bin/evince-previewer"
[   16.267483] type=1505  audit(1274835008.919:11):  operation="profile_load" pid=817  name="/usr/bin/evince-thumbnailer"
[   16.304709] input: HDA ATI  SB Mic at Ext Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    16.304954] input: HDA ATI SB HP Out at Ext Left Jack as  /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[    16.608374] Bluetooth: L2CAP ver 2.14
[   16.608378] Bluetooth: L2CAP  socket layer initialized
[   16.624873] Bluetooth: BNEP (Ethernet  Emulation) ver 1.3
[   16.624877] Bluetooth: BNEP filters: protocol  multicast
[   16.661146] Bridge firewalling registered
[    16.684297] Bluetooth: SCO (Voice Link) ver 0.6
[   16.684302]  Bluetooth: SCO socket layer initialized
[   16.697330] ppdev:  user-space parallel port driver
[   16.802637] [drm] fb mappable at  0xE0040000
[   16.802640] [drm] vram apper at 0xE0000000
[    16.802642] [drm] size 4096000
[   16.802644] [drm] fb depth is 24
[    16.802646] [drm]    pitch is 5120
[   16.805320] fb0: radeondrmfb  frame buffer device
[   16.805324] registered panic notifier
[    16.805330] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on  minor 0
[   16.812981] vga16fb: initializing
[   16.812987]  vga16fb: mapped to 0xc00a0000
[   16.812992] vga16fb: not registering  due to another framebuffer present
[   17.009379] Console: switching  to colour frame buffer device 160x50
[   17.020036] Bluetooth:  RFCOMM TTY layer initialized
[   17.020048] Bluetooth: RFCOMM socket  layer initialized
[   17.020051] Bluetooth: RFCOMM ver 1.11
[    77.504043] Clocksource tsc unstable (delta = -86401757 ns)
[   720.606164] pcmcia: Detected deprecated PCMCIA ioctl usage from process:  lshw.
[  720.606169] pcmcia: This interface will soon be removed  from the kernel; please expect breakage unless you upgrade to new tools.
[   720.606172] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html)  for details.
[  796.432076] usb 2-1: new low speed USB device using  ohci_hcd and address 2
[  796.598533] usb 2-1: configuration #1  chosen from 1 choice
[  796.684357] usbcore: registered new interface  driver hiddev
[  796.691994] input: USB Optical Mouse as  /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input12
[   796.692955] generic-usb 0003:0461:4D22.0001: input,hidraw0: USB HID  v1.11 Mouse [USB Optical Mouse] on usb-0000:00:13.0-1/input0
[   796.693026] usbcore: registered new interface driver usbhid
[   796.695067] usbhid: v2.6:USB HID core driver


$sudo lshw -C  network

  *-network DISABLED      
       description:  Wireless interface
       product: BCM4311 802.11b/g WLAN
        vendor: Broadcom Corporation
       physical id: 0
       bus  info: pci@0000:0b:00.0
       logical name: eth2
       version:  01
       serial: 00:1f:3a:24:18:b8
       width: 32 bits
        clock: 33MHz
       capabilities: pm msi pciexpress bus_master  cap_list ethernet physical wireless
       configuration:  broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0  multicast=yes wireless=IEEE 802.11bg
       resources: irq:17  memory:fe8fc000-fe8fffff
  *-network DISABLED
       description:  Ethernet interface
       product: NetXtreme BCM5755M Gigabit  Ethernet PCI Express
       vendor: Broadcom Corporation
        physical id: 0
       bus info: pci@0000:09:00.0
       logical  name: eth0
       version: 02
       serial: 00:1d:09:b0:10:b7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.102 duplex=half firmware=5755m-v3.29 latency=0 link=yes  multicast=yes port=twisted pair
       resources: irq:18  memory:fe7f0000-fe7fffff

$iwlist
lo        Interface doesn't  support scanning.

eth0      Interface doesn't support scanning.

eth2       Interface doesn't support scanning.

pan0      Interface  doesn't support scanning.

$lsb_release -d
Description: Ubuntu 10.04 LTS

$uname -mr
2.6.32-22-generic i686

$sudo /etc/init.d/networking restart
 
*Reconfiguring network interfaces...                         [ OK ]

---

### Post by sezal on 2010-06-24
if you have dell-wmi package installed try to uninstall it.
Wifi stopped working on my dell inspiron 1525 after upgrade to 10.04 and uninstalling of dell-wmi helped me.

---

