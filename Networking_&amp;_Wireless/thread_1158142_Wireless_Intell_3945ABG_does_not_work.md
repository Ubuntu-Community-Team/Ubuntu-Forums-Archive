---
title: "Wireless Intell 3945ABG does not work"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by penchev on 2009-05-13
New install of Ubuntu 9.04 on HP Pavillion dv6000 laptop

Hereby I am copying  what the console returns on most commands listed in the howto threat.

Thanks in advance for any help
```

sandra@sandra-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
sandra@sandra-laptop:~$ 
sandra@sandra-laptop:~$ lspci -nn | grep 3945ABG
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
sandra@sandra-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

sandra@sandra-laptop:~$ 
sandra@sandra-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
iwl3945                97912  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 iwl3945
psmouse                61972  0 
led_class              12036  1 iwl3945
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
pcspkr                 10496  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
nvidia               7233756  39 
serio_raw              13316  0 
cfg80211               38032  2 iwl3945,mac80211
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
video                  25360  5 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
sandra@sandra-laptop:~$ lsmod iwl3945
Usage: lsmod
sandra@sandra-laptop:~$ 
sandra@sandra-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2B:6F:04:7A
                    ESSID:"WLAN_1C"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 0007574C414E5F3143
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD06001018020004
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001d0f3db418b
                    Extra: Last beacon: 5316ms ago
          Cell 02 - Address: 00:01:38:E2:5F:C3
                    ESSID:"WLAN_7E"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 0007574C414E5F3745
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000013320c7c1d9
                    Extra: Last beacon: 5052ms ago

pan0      Interface doesn't support scanning.
sandra@sandra-laptop:~$ lsb_release -d
Description:    Ubuntu 9.04


[    0.672801] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.672805] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.672810] pci 0000:00:01.0:   MEM window: 0xc4000000-0xc6ffffff
[    0.672815] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.672822] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.672827] pci 0000:00:1c.0:   IO window: 0x4000-0x7fff
[    0.672835] pci 0000:00:1c.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.672841] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.672851] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.672856] pci 0000:00:1c.1:   IO window: 0x8000-0xbfff
[    0.672864] pci 0000:00:1c.1:   MEM window: 0xbc000000-0xbfffffff
[    0.672870] pci 0000:00:1c.1:   PREFETCH window: 0x000000c8000000-0x000000cbffffff
[    0.672881] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    0.672885] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.672893] pci 0000:00:1c.5:   MEM window: 0xf8000000-0xf80fffff
[    0.672899] pci 0000:00:1c.5:   PREFETCH window: 0x00000088000000-0x000000880fffff
[    0.672910] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.672913] pci 0000:00:1e.0:   IO window: disabled
[    0.672921] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xf81fffff
[    0.672927] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.672946] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.672952] pci 0000:00:01.0: setting latency timer to 64
[    0.672964] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.672971] pci 0000:00:1c.0: setting latency timer to 64
[    0.672982] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.672988] pci 0000:00:1c.1: setting latency timer to 64
[    0.673008] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.673015] pci 0000:00:1c.5: setting latency timer to 64
[    0.673026] pci 0000:00:1e.0: setting latency timer to 64
[    0.673031] bus: 00 index 0 io port: [0x00-0xffff]
[    0.673034] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.673037] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.673040] bus: 01 index 1 mmio: [0xc4000000-0xc6ffffff]
[    0.673042] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.673045] bus: 01 index 3 mmio: [0x0-0x0]
[    0.673047] bus: 02 index 0 io port: [0x4000-0x7fff]
[    0.673050] bus: 02 index 1 mmio: [0xf4000000-0xf7ffffff]
[    0.673053] bus: 02 index 2 mmio: [0xf0000000-0xf3ffffff]
[    0.673056] bus: 02 index 3 mmio: [0x0-0x0]
[    0.673058] bus: 04 index 0 io port: [0x8000-0xbfff]
[    0.673061] bus: 04 index 1 mmio: [0xbc000000-0xbfffffff]
[    0.673063] bus: 04 index 2 mmio: [0xc8000000-0xcbffffff]
[    0.673066] bus: 04 index 3 mmio: [0x0-0x0]
[    0.673068] bus: 06 index 0 io port: [0xc000-0xcfff]
[    0.673071] bus: 06 index 1 mmio: [0xf8000000-0xf80fffff]
[    0.673074] bus: 06 index 2 mmio: [0x88000000-0x880fffff]
[    0.673076] bus: 06 index 3 mmio: [0x0-0x0]
[    0.673079] bus: 07 index 0 mmio: [0x0-0x0]
[    0.673081] bus: 07 index 1 mmio: [0xf8100000-0xf81fffff]
[    0.673084] bus: 07 index 2 mmio: [0x0-0x0]
[    0.673086] bus: 07 index 3 io port: [0x00-0xffff]
[    0.673089] bus: 07 index 4 mmio: [0x000000-0xffffffff]
[    0.673101] NET: Registered protocol family 2
[    0.685069] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.685399] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.685898] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.686279] TCP: Hash tables configured (established 131072 bind 65536)
[    0.686283] TCP reno registered
[    0.689140] NET: Registered protocol family 1
[    0.689307] checking if image is initramfs... it is
[    1.508979] Freeing initrd memory: 7366k freed
[    1.509044] Simple Boot Flag at 0x35 set to 0x1
[    1.509251] cpufreq: No nForce2 chipset.
[    1.509417] audit: initializing netlink socket (disabled)
[    1.509437] type=2000 audit(1242165230.508:1): initialized
[    1.518918] highmem bounce pool size: 64 pages
[    1.518924] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.520663] VFS: Disk quotas dquot_6.5.1
[    1.520740] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.521543] fuse init (API version 7.10)
[    1.521650] msgmni has been set to 1698
[    1.521863] alg: No test for stdrng (krng)
[    1.521878] io scheduler noop registered
[    1.521881] io scheduler anticipatory registered
[    1.521883] io scheduler deadline registered
[    1.521902] io scheduler cfq registered (default)
[    1.522098] pci 0000:01:00.0: Boot video device
[    1.529487] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.529540] pcieport-driver 0000:00:01.0: found MSI capability
[    1.529572] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.529586] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.529606] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.529622] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.529691] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.529753] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.529794] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.529814] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.529834] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.529849] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.529942] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.530003] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.530045] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.530065] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.530081] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.530097] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.530190] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.530251] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.530292] pcieport-driver 0000:00:1c.5: irq 2300 for MSI/MSI-X
[    1.530312] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.530329] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.530344] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.530449] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.530921] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.534142] ACPI: AC Adapter [ACAD] (on-line)
[    1.630406] ACPI: Battery Slot [BAT0] (battery present)
[    1.630510] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.630514] ACPI: Power Button (FF) [PWRF]
[    1.630570] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.630582] ACPI: Power Button (CM) [PWRB]
[    1.630637] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.630641] ACPI: Sleep Button (CM) [SLPB]
[    1.630697] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.632599] ACPI: Lid Switch [LID]
[    1.633334] ACPI: SSDT 7FED309D, 01F6 (r1  HP    30D2         3000 INTL 20060707)
[    1.633879] ACPI: SSDT 7FED2B8D, 048B (r1  HP    30D2         3001 INTL 20060707)
[    1.636822] Monitor-Mwait will be used to enter C-1 state
[    1.636827] Monitor-Mwait will be used to enter C-2 state
[    1.636845] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.636877] processor ACPI_CPU:00: registered as cooling_device0
[    1.636882] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.637325] ACPI: SSDT 7FED3293, 00C8 (r1  HP    30D2         3000 INTL 20060707)
[    1.637823] ACPI: SSDT 7FED3018, 0085 (r1  HP    30D2         3000 INTL 20060707)
[    1.639095] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.639121] processor ACPI_CPU:01: registered as cooling_device1
[    1.639126] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.650026] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.650108] isapnp: Scanning for PnP cards...
[    2.004536] isapnp: No Plug & Play device found
[    2.017330] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.018694] brd: module loaded
[    2.019096] loop: module loaded
[    2.019191] Fixed MDIO Bus: probed
[    2.019197] PPP generic driver version 2.4.2
[    2.019272] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.019313] Driver 'sd' needs updating - please use bus_type methods
[    2.019325] Driver 'sr' needs updating - please use bus_type methods
[    2.019378] ahci 0000:00:1f.2: version 3.0
[    2.019399] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.019452] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    2.019536] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    2.019540] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    2.019547] ahci 0000:00:1f.2: setting latency timer to 64
[    2.019846] scsi0 : ahci
[    2.019980] scsi1 : ahci
[    2.020054] scsi2 : ahci
[    2.020189] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 2299
[    2.020194] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 2299
[    2.020198] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 2299
[    2.340026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.340671] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.340677] ata1.00: ATA-8: FUJITSU MHY2120BH, 890B, max UDMA/100
[    2.340680] ata1.00: 234441648 sectors, multi 16: LBA48 
[    2.341408] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.341439] ata1.00: configured for UDMA/100
[    2.676023] ata2: SATA link down (SStatus 0 SControl 300)
[    3.012024] ata3: SATA link down (SStatus 0 SControl 300)
[    3.028138] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2120B 890B PQ: 0 ANSI: 5
[    3.028275] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.028296] sd 0:0:0:0: [sda] Write Protect is off
[    3.028299] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.028332] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.028422] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.028441] sd 0:0:0:0: [sda] Write Protect is off
[    3.028443] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.028476] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.028480]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.114616] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.114679] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.114753] ata_piix 0000:00:1f.1: version 2.12
[    3.114767] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.114818] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.114922] scsi3 : ata_piix
[    3.115002] scsi4 : ata_piix
[    3.115827] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    3.115830] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    3.276543] ata4.00: ATAPI: PIONEER DVDRW   DVR-K17B, 1.02, max MWDMA2
[    3.292487] ata4.00: configured for MWDMA2
[    3.469483] scsi 3:0:0:0: CD-ROM            PIONEER  DVDRW   DVR-K17B 1.02 PQ: 0 ANSI: 5
[    3.487789] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.487793] Uniform CD-ROM driver Revision: 3.20
[    3.487924] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.487980] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.488902] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.488941] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.488966] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.488970] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.489048] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.492974] ehci_hcd 0000:00:1a.7: debug port 1
[    3.492983] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.493002] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[    3.508013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.508093] usb usb1: configuration #1 chosen from 1 choice
[    3.508127] hub 1-0:1.0: USB hub found
[    3.508137] hub 1-0:1.0: 4 ports detected
[    3.508277] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.508292] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.508296] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.508348] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.512265] ehci_hcd 0000:00:1d.7: debug port 1
[    3.512274] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.512290] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[    3.528012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.528099] usb usb2: configuration #1 chosen from 1 choice
[    3.528132] hub 2-0:1.0: USB hub found
[    3.528140] hub 2-0:1.0: 6 ports detected
[    3.528264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.528288] uhci_hcd: USB Universal Host Controller Interface driver
[    3.528323] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.528332] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.528336] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.528392] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.528436] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    3.528536] usb usb3: configuration #1 chosen from 1 choice
[    3.528569] hub 3-0:1.0: USB hub found
[    3.528578] hub 3-0:1.0: 2 ports detected
[    3.528693] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.528703] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.528708] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.528765] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.528806] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    3.528903] usb usb4: configuration #1 chosen from 1 choice
[    3.528938] hub 4-0:1.0: USB hub found
[    3.528946] hub 4-0:1.0: 2 ports detected
[    3.529052] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.529060] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.529064] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.529117] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.529148] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    3.529241] usb usb5: configuration #1 chosen from 1 choice
[    3.529273] hub 5-0:1.0: USB hub found
[    3.529281] hub 5-0:1.0: 2 ports detected
[    3.529386] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.529397] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.529401] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.529467] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.529508] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    3.529597] usb usb6: configuration #1 chosen from 1 choice
[    3.529629] hub 6-0:1.0: USB hub found
[    3.529636] hub 6-0:1.0: 2 ports detected
[    3.529745] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.529753] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.529757] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.529818] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.529849] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    3.529939] usb usb7: configuration #1 chosen from 1 choice
[    3.529973] hub 7-0:1.0: USB hub found
[    3.529981] hub 7-0:1.0: 2 ports detected
[    3.530143] usbcore: registered new interface driver libusual
[    3.530183] usbcore: registered new interface driver usbserial
[    3.530200] USB Serial support registered for generic
[    3.530221] usbcore: registered new interface driver usbserial_generic
[    3.530223] usbserial: USB Serial Driver core
[    3.530290] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.573032] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.573039] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.577051] mice: PS/2 mouse device common for all mice
[    3.597091] rtc_cmos 00:08: RTC can wake from S4
[    3.597137] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    3.597174] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.597256] device-mapper: uevent: version 1.0.3
[    3.597373] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.597465] device-mapper: multipath: version 1.0.5 loaded
[    3.597469] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.597569] EISA: Probing bus 0 at eisa.0
[    3.597577] Cannot allocate resource for EISA slot 1
[    3.597581] Cannot allocate resource for EISA slot 2
[    3.597588] Cannot allocate resource for EISA slot 4
[    3.597591] Cannot allocate resource for EISA slot 5
[    3.597594] Cannot allocate resource for EISA slot 6
[    3.597597] Cannot allocate resource for EISA slot 7
[    3.597600] Cannot allocate resource for EISA slot 8
[    3.597602] EISA: Detected 0 cards.
[    3.597731] cpuidle: using governor ladder
[    3.597851] cpuidle: using governor menu
[    3.598515] TCP cubic registered
[    3.598647] NET: Registered protocol family 10
[    3.599201] lo: Disabled Privacy Extensions
[    3.599644] NET: Registered protocol family 17
[    3.599667] Bluetooth: L2CAP ver 2.11
[    3.599669] Bluetooth: L2CAP socket layer initialized
[    3.599673] Bluetooth: SCO (Voice Link) ver 0.6
[    3.599676] Bluetooth: SCO socket layer initialized
[    3.599717] Bluetooth: RFCOMM socket layer initialized
[    3.599725] Bluetooth: RFCOMM TTY layer initialized
[    3.599727] Bluetooth: RFCOMM ver 1.10
[    3.600075] Marking TSC unstable due to TSC halts in idle
[    3.600552] Using IPI No-Shortcut mode
[    3.600653] registered taskstats version 1
[    3.600825]   Magic number: 9:462:904
[    3.600930] rtc_cmos 00:08: setting system clock to 2009-05-12 21:53:53 UTC (1242165233)
[    3.600933] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.600936] EDD information not available.
[    3.601287] Freeing unused kernel memory: 532k freed
[    3.601473] Write protecting the kernel text: 4128k
[    3.601542] Write protecting the kernel read-only data: 1532k
[    3.625620] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.841052] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    3.955869] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.955898] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.955928] r8169 0000:06:00.0: setting latency timer to 64
[    4.007630] r8169 0000:06:00.0: irq 2298 for MSI/MSI-X
[    4.011644] eth0: RTL8101e at 0xf7c78000, 00:1b:24:e1:19:8a, XID 34200000 IRQ 2298
[    4.034106] usb 2-4: configuration #1 chosen from 1 choice
[    4.090364] ohci1394 0000:07:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.142160] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.598742] PM: Starting manual resume from disk
[    4.598747] PM: Resume from partition 8:6
[    4.598749] PM: Checking hibernation image.
[    4.598928] PM: Resume from disk failed.
[    4.627986] kjournald starting.  Commit interval 5 seconds
[    4.628023] EXT3-fs: mounted filesystem with ordered data mode.
[    5.436163] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0056459100]
[   10.706661] udev: starting version 141
[   10.908166] acpi device:06: registered as cooling_device2
[   10.908541] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[   10.933080] Linux video capture interface: v2.00
[   10.933423] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.989611] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[   10.990650] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
[   11.004228] usbcore: registered new interface driver uvcvideo
[   11.004262] USB Video Class driver (v0.1.0)
[   11.023193] Linux agpgart interface v0.103
[   11.365043] cfg80211: Calling CRDA to update world regulatory domain
[   11.455776] cfg80211: World regulatory domain updated:
[   11.455781]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.455784]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.455787]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.455790]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.455794]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.455797]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.023232] nvidia: module license 'NVIDIA' taints kernel.
[   12.057758] iTCO_vendor_support: vendor-support=0
[   12.060240] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.060665] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   12.060774] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.077977] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   12.087135] sdhci: Secure Digital Host Controller Interface driver
[   12.087138] sdhci: Copyright(c) Pierre Ossman
[   12.097308] sdhci-pci 0000:07:09.1: SDHCI controller found [1180:0822] (rev 22)
[   12.097329] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   12.100439] mmc0: SDHCI controller on PCI [0000:07:09.1] using PIO
[   12.103611] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.103615] ricoh-mmc: Copyright(c) Philip Langdale
[   12.103649] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 12)
[   12.103672] ricoh-mmc: Controller is now disabled.
[   12.278643] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   12.278657] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.278668] nvidia 0000:01:00.0: setting latency timer to 64
[   12.279999] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.438916] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.438921] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   12.439055] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.439071] iwl3945 0000:02:00.0: setting latency timer to 64
[   12.439148] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   12.439438] iwl3945 0000:02:00.0: irq 2297 for MSI/MSI-X
[   12.497327] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.498504] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.582494] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.605901] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.606020] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.877130] lp: driver loaded but no devices found
[   12.986150] Adding 690752k swap on /dev/sda6.  Priority:-1 extents:1 across:690752k
[   13.540712] EXT3 FS on sda5, internal journal
[   13.794377] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   13.903461] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.829674] type=1505 audit(1242158044.728:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2124
[   14.891473] type=1505 audit(1242158044.788:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2128
[   14.891622] type=1505 audit(1242158044.788:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2128
[   14.891677] type=1505 audit(1242158044.788:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2128
[   14.891730] type=1505 audit(1242158044.788:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2128
[   15.064537] type=1505 audit(1242158044.960:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2133
[   15.064782] type=1505 audit(1242158044.960:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2133
[   15.101807] type=1505 audit(1242158045.000:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2137
[   18.693901] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.693905] Bluetooth: BNEP filters: protocol multicast
[   18.705534] Bridge firewalling registered
[   20.245597] ppdev: user-space parallel port driver
[   24.104184] r8169: eth0: link up
[   24.104195] r8169: eth0: link up
[   24.105469] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   24.234560] Registered led device: iwl-phy0:radio
[   24.234882] Registered led device: iwl-phy0:assoc
[   24.238224] Registered led device: iwl-phy0:RX
[   24.238757] Registered led device: iwl-phy0:TX
[   24.244478] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.308022] eth0: no IPv6 routers present
sandra@sandra-laptop:~$ sudo lshw -C network
[sudo] password for sandra: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:57:a5:77
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:e1:19:8a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.37 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:90:77:f2:c0:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
sandra@sandra-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

sandra@sandra-laptop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
sandra@sandra-laptop:~$ lsb_release -d
Description:    Ubuntu 9.04
sandra@sandra-laptop:~$ uname -mr
2.6.28-11-generic i686
sandra@sandra-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
sandra@sandra-laptop:~$ 


```

---

### Post by Peter09 on 2009-05-13
Read this thread - look right at the end

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204)

---

### Post by chili555 on 2009-05-13
Network Manager, which is installed by default, will not allow a wireless connection if you have an ethernet connection, which you do:> ip=192.168.1.37 latency=0 link=yesPlease disconnect the wire and do:```
sudo dhclient -r eth0
sudo ifdown eth0
```Now try to connect wirelessly with the Network Manager icon.

---

### Post by penchev on 2009-05-13
Thank you Peter I have used **sudo apt-get install wicd **, restart and finally I have wireless.

@ chili Thank you very much, wicd solved the problem.

---

