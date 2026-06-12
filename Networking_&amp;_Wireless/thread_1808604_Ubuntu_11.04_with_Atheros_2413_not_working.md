---
title: "Ubuntu 11.04 with Atheros 2413 not working"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by JadeLinux on 2011-07-20
Hello All,
This is my first post and am very new to linux. I have a Acer Aspire 9300 with atheros wireless nic. (ar2413) I cannot get it to work properly. I have only been able to get it to work once, but every time it reboots it stops working, it just keeps trying to connect, and asking me for the authentication key. I know the key is correct, but i don not know enough about how to diagnose the issue. Can someone help?
 
I have used some tips from a lot of the posts, i am not ever blocked i dont think. I need to find a permanent fix for this so i can have inet connection when i log on.

It seems to have a problem associating with my access point

---

### Post by JadeLinux on 2011-07-20
lspci when wireless is working

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by JadeLinux on 2011-07-20
ifconfig when wireless is working

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:9b:d7:1d  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe9b:d71d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1711995 (1.7 MB)  TX bytes:351362 (351.3 KB)

iwconfig when wireless is working

wlan0     IEEE 802.11bg  ESSID:"MonkeyWireless"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:18:01:FD:A7:4C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:41   Missed beacon:0

---

### Post by JadeLinux on 2011-07-20
markfrazer@mobiledaddy:~$ lsmod
Module                  Size  Used by
ath5k                 155466  0 
sparse_keymap          13898  0 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
snd_hda_codec_realtek   336771  1 
binfmt_misc            17565  1 
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
vboxdrv               286726  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
gspca_m5602            65289  0 
pcmcia                 49166  0 
gspca_main             36853  1 gspca_m5602
videodev               82052  1 gspca_main
v4l2_compat_ioctl32    17078  1 videodev
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    23773  1 ath5k
mac80211              294370  1 ath5k
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              13042  0 
tifm_core              15654  1 tifm_7xx1
snd_timer              29602  2 snd_pcm,snd_seq
nvidia              10709116  41 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath5k,ath,mac80211
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73535  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53845  0 
nv_tco                 13603  0 
serio_raw              13166  0 
k8temp                 13016  0 
edac_mce_amd           23464  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
forcedeth              63555  0 
pata_amd               14130  2

---

### Post by JadeLinux on 2011-07-20
[    0.501399] pci 0000:04:06.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.501405] pci 0000:04:06.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.501409] pci 0000:04:06.0: BAR 13: assigned [io  0x5000-0x50ff]
[    0.501413] pci 0000:04:06.0: BAR 14: assigned [io  0x5400-0x54ff]
[    0.501417] pci 0000:04:06.0: CardBus bridge to [bus 05-08]
[    0.501420] pci 0000:04:06.0:   bridge window [io  0x5000-0x50ff]
[    0.501425] pci 0000:04:06.0:   bridge window [io  0x5400-0x54ff]
[    0.501431] pci 0000:04:06.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.501436] pci 0000:04:06.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.501441] pci 0000:00:10.0: PCI bridge to [bus 04-05]
[    0.501445] pci 0000:00:10.0:   bridge window [io  0x5000-0x5fff]
[    0.501450] pci 0000:00:10.0:   bridge window [mem 0xc3000000-0xc30fffff]
[    0.501455] pci 0000:00:10.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.501469] pci 0000:00:02.0: setting latency timer to 64
[    0.501475] pci 0000:00:03.0: setting latency timer to 64
[    0.501481] pci 0000:00:04.0: setting latency timer to 64
[    0.501488] pci 0000:00:10.0: setting latency timer to 64
[    0.501640] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 11
[    0.501658] pci 0000:04:06.0: PCI INT A -> Link[LNK4] -> GSI 11 (level, low) -> IRQ 11
[    0.501666] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.501669] pci_bus 0000:00: resource 5 [mem 0x40000000-0xfcffffffff]
[    0.501673] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.501677] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.501680] pci_bus 0000:02: resource 1 [mem 0xc4000000-0xc40fffff]
[    0.501684] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
[    0.501687] pci_bus 0000:04: resource 1 [mem 0xc3000000-0xc30fffff]
[    0.501691] pci_bus 0000:04: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.501695] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.501698] pci_bus 0000:04: resource 5 [mem 0x40000000-0xfcffffffff]
[    0.501701] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.501705] pci_bus 0000:05: resource 0 [io  0x5000-0x50ff]
[    0.501708] pci_bus 0000:05: resource 1 [io  0x5400-0x54ff]
[    0.501712] pci_bus 0000:05: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.501715] pci_bus 0000:05: resource 3 [mem 0x48000000-0x4bffffff]
[    0.501774] NET: Registered protocol family 2
[    0.501927] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.502837] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.504744] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.505604] TCP: Hash tables configured (established 131072 bind 65536)
[    0.505608] TCP reno registered
[    0.505622] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.505644] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.505778] NET: Registered protocol family 1
[    0.505858] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.505887] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.505920] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.505930] pci 0000:00:05.0: Boot video device
[    0.710101] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.710157] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.710190] PCI: CLS 64 bytes, default 64
[    0.781006] Simple Boot Flag at 0x36 set to 0x1
[    0.781458] audit: initializing netlink socket (disabled)
[    0.781473] type=2000 audit(1311161792.780:1): initialized
[    0.820487] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.823192] VFS: Disk quotas dquot_6.5.2
[    0.823283] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.824279] fuse init (API version 7.16)
[    0.824416] msgmni has been set to 1457
[    0.824828] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.824868] io scheduler noop registered
[    0.824871] io scheduler deadline registered
[    0.824933] io scheduler cfq registered (default)
[    0.825146] pcieport 0000:00:02.0: setting latency timer to 64
[    0.825182] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.825289] pcieport 0000:00:03.0: setting latency timer to 64
[    0.825318] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.825403] pcieport 0000:00:04.0: setting latency timer to 64
[    0.825428] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    0.825534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.825568] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.826314] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.826772] ACPI: AC Adapter [ADP1] (on-line)
[    0.826878] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.914899] Freeing initrd memory: 12872k freed
[    0.950049] ACPI: Lid Switch [LID0]
[    0.950128] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.980070] ACPI: Sleep Button [SLPB]
[    0.980190] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.980198] ACPI: Power Button [PWRB]
[    0.980298] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.980303] ACPI: Power Button [PWRF]
[    0.980589] ACPI: acpi_idle registered with cpuidle
[    0.980624] ACPI: processor limited to max C-state 1
[    0.990069] thermal LNXTHERM:00: registered as thermal_zone0
[    0.990073] ACPI: Thermal Zone [TZS0] (53 C)
[    0.992967] thermal LNXTHERM:01: registered as thermal_zone1
[    0.992971] ACPI: Thermal Zone [TZS1] (57 C)
[    0.993065] ERST: Table is not found!
[    0.993196] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.044469] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.044480] ACPI: Battery Slot [BAT0] (battery present)
[    1.410594] Linux agpgart interface v0.103
[    1.412390] brd: module loaded
[    1.413252] loop: module loaded
[    1.413412] i2c-core: driver [adp5520] using legacy suspend method
[    1.413416] i2c-core: driver [adp5520] using legacy resume method
[    1.413763] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    1.414406] Fixed MDIO Bus: probed
[    1.414459] PPP generic driver version 2.4.2
[    1.414556] tun: Universal TUN/TAP device driver, 1.6
[    1.414559] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.414698] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.415078] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
[    1.415102] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
[    1.415123] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    1.415128] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    1.415242] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.440101] ehci_hcd 0000:00:0b.1: debug port 1
[    1.440111] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    1.440142] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xc0005000
[    1.460051] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.460238] hub 1-0:1.0: USB hub found
[    1.460245] hub 1-0:1.0: 8 ports detected
[    1.460396] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.460777] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    1.460803] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    1.460828] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.460832] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.460929] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.461026] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
[    1.522234] hub 2-0:1.0: USB hub found
[    1.522244] hub 2-0:1.0: 8 ports detected
[    1.522392] uhci_hcd: USB Universal Host Controller Interface driver
[    1.522561] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.522894] i8042: Detected active multiplexing controller, rev 1.1
[    1.522992] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.523002] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.523006] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.523010] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.523014] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.523140] mousedev: PS/2 mouse device common for all mice
[    1.523382] rtc_cmos 00:06: RTC can wake from S4
[    1.525982] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.550104] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.550147] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.550316] device-mapper: uevent: version 1.0.3
[    1.550444] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    1.550608] device-mapper: multipath: version 1.2.0 loaded
[    1.550612] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.550816] cpuidle: using governor ladder
[    1.550820] cpuidle: using governor menu
[    1.551227] TCP cubic registered
[    1.551417] NET: Registered protocol family 10
[    1.552136] NET: Registered protocol family 17
[    1.552169] Registering the dns_resolver key type
[    1.552220] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 (2 cpu cores) (version 2.20.00)
[    1.552296] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    1.552299] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    1.552520] PM: Hibernation image not present or could not be loaded.
[    1.552535] registered taskstats version 1
[    1.552857]   Magic number: 3:256:631
[    1.552991] rtc_cmos 00:06: setting system clock to 2011-07-20 11:36:34 UTC (1311161794)
[    1.552996] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.552998] EDD information not available.
[    1.555665] Freeing unused kernel memory: 956k freed
[    1.556303] Write protecting the kernel read-only data: 10240k
[    1.557433] Freeing unused kernel memory: 184k freed
[    1.564904] Freeing unused kernel memory: 1440k freed
[    1.598108] <30>udev[99]: starting version 167
[    1.772138] pata_amd 0000:00:0d.0: version 0.4.1
[    1.772209] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.775594] scsi0 : pata_amd
[    1.776436] scsi1 : pata_amd
[    1.777142] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.777146] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.780053] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.780263] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.780561] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.780586] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, high) -> IRQ 21
[    1.780593] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.950537] ata1.00: ATA-6: ST9120821A, 3.06, max UDMA/100
[    1.950542] ata1.00: 234441648 sectors, multi 16: LBA48 
[    1.950555] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
[    1.990461] ata1.00: configured for UDMA/100
[    1.990684] scsi 0:0:0:0: Direct-Access     ATA      ST9120821A       3.06 PQ: 0 ANSI: 5
[    1.990954] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.991028] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.991101] sd 0:0:0:0: [sda] Write Protect is off
[    1.991105] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.991136] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.038128]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.038801] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.170358] ata2.00: ATAPI: PHILIPS DVD-RAM SDVD8821, EX02, max UDMA/33
[    2.170371] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c000) ACPI=0x701f (60:600:0x13)
[    2.210287] ata2.00: configured for UDMA/33
[    2.212053] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD-RAM SDVD8821 EX02 PQ: 0 ANSI: 5
[    2.220220] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.220225] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.220429] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.220539] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.311266] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:d3:4b:11:31
[    2.311273] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    2.390069] usb 2-8: new low speed USB device using ohci_hcd and address 2
[    2.666081] input: Microsoft Microsoft IntelliMouse® Explorer as /devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0/input/input5
[    2.666265] generic-usb 0003:045E:0095.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft IntelliMouse® Explorer] on usb-0000:00:0b.0-8/input0
[    2.666297] usbcore: registered new interface driver usbhid
[    2.666300] usbhid: USB HID core driver
[    3.052456] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   22.486044] <30>udev[359]: starting version 167
[   22.502463] Adding 783356k swap on /dev/sda6.  Priority:-1 extents:1 across:783356k 
[   22.559338] lp: driver loaded but no devices found
[   22.670071] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   22.674145] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   22.674251] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.913277] type=1400 audit(1311187015.849:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=557 comm="apparmor_parser"
[   22.913832] type=1400 audit(1311187015.849:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=557 comm="apparmor_parser"
[   22.914080] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   22.914142] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   22.914161] type=1400 audit(1311187015.849:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=557 comm="apparmor_parser"
[   22.931995] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   22.932188] NV_TCO: Watchdog reboot not detected.
[   22.948514] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[   22.955732] MCE: In-kernel MCE decoding enabled.
[   23.010104] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   23.056234] EDAC MC: Ver: 2.1.0 Jun 28 2011
[   23.069636] EDAC amd64_edac: v3.3.0
[   23.079361] nvidia: module license 'NVIDIA' taints kernel.
[   23.079367] Disabling lock debugging due to kernel taint
[   23.085966] EDAC amd64: DRAM ECC disabled.
[   23.085978] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   23.085980]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   23.085982]  (Note that use of the override may cause unknown side effects.)
[   23.118862] forcedeth 0000:00:14.0: eth0: no link during initialization
[   23.126461] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.714517] cfg80211: Calling CRDA to update world regulatory domain
[   23.928866] yenta_cardbus 0000:04:06.0: CardBus bridge found [1025:0112]
[   23.928886] yenta_cardbus 0000:04:06.0: Using CSCINT to route CSC interrupts to PCI
[   23.928890] yenta_cardbus 0000:04:06.0: Routing CardBus interrupts to PCI
[   23.928896] yenta_cardbus 0000:04:06.0: TI: mfunc 0x013a1b22, devctl 0x64
[   24.192883] cfg80211: World regulatory domain updated:
[   24.192889] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.192894] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.192898] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.192901] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.192905] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.192909] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.197877] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 20
[   24.197907] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 20 (level, high) -> IRQ 20
[   24.197919] nvidia 0000:00:05.0: setting latency timer to 64
[   24.197926] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   24.198883] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   24.242055] type=1400 audit(1311187017.179:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=804 comm="apparmor_parser"
[   24.245025] type=1400 audit(1311187017.179:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=803 comm="apparmor_parser"
[   24.246287] type=1400 audit(1311187017.179:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=804 comm="apparmor_parser"
[   24.246630] type=1400 audit(1311187017.179:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=804 comm="apparmor_parser"
[   24.265817] type=1400 audit(1311187017.199:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=812 comm="apparmor_parser"
[   24.267127] type=1400 audit(1311187017.199:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=808 comm="apparmor_parser"
[   24.267866] type=1400 audit(1311187017.199:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=812 comm="apparmor_parser"
[   24.328319] Linux video capture interface: v2.00
[   24.330842] yenta_cardbus 0000:04:06.0: ISA IRQ mask 0x04f8, PCI irq 11
[   24.330848] yenta_cardbus 0000:04:06.0: Socket status: 30000006
[   24.330853] pci_bus 0000:04: Raising subordinate bus# of parent bus (#04) from #05 to #08
[   24.330866] yenta_cardbus 0000:04:06.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   24.330871] yenta_cardbus 0000:04:06.0: pcmcia: parent PCI bridge window: [mem 0xc3000000-0xc30fffff]
[   24.330876] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc3000000-0xc30fffff: excluding 0xc3000000-0xc301ffff
[   24.330895] yenta_cardbus 0000:04:06.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   24.330899] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   24.348930] tifm_7xx1 0000:04:06.2: PCI INT A -> Link[LNK4] -> GSI 11 (level, low) -> IRQ 11
[   24.353092] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 19
[   24.353125] ath5k 0000:04:05.0: PCI INT A -> Link[LNK2] -> GSI 19 (level, high) -> IRQ 19
[   24.353203] ath5k 0000:04:05.0: registered as 'phy0'
[   24.360449] gspca: v2.12.0 registered
[   24.381418] gspca: probing 0402:5602
[   24.381425] ALi m5602: Probing for a po1030 sensor
[   24.409933] ALi m5602: Probing for a mt9m111 sensor
[   24.429599] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   24.429674] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   24.429744] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   24.441822] ALi m5602: Probing for a s5k4aa sensor
[   24.488169] ALi m5602: Probing for an ov9650 sensor
[   24.528669] ALi m5602: Sensor reported 0xffff
[   24.528675] ALi m5602: Probing for a s5k83a sensor
[   24.548417] ALi m5602: Detected a s5k83a sensor
[   24.620106] gspca: video0 created
[   24.620833] usbcore: registered new interface driver ALi m5602
[   25.004602] HDA Intel 0000:00:10.1: power state changed by ACPI to D0
[   25.004610] HDA Intel 0000:00:10.1: power state changed by ACPI to D0
[   25.004817] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 18
[   25.004843] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 18 (level, high) -> IRQ 18
[   25.004848] hda_intel: Disable MSI for Nvidia chipset
[   25.004891] HDA Intel 0000:00:10.1: setting latency timer to 64
[   25.060824] ath: EEPROM regdomain: 0x63
[   25.060829] ath: EEPROM indicates we should expect a direct regpair map
[   25.060835] ath: Country alpha2 being used: 00
[   25.060838] ath: Regpair used: 0x63
[   25.060857] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   25.060862] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060865] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   25.060869] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060872] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   25.060876] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060879] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   25.060882] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060885] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   25.060889] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060892] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   25.060896] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060899] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   25.060902] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060905] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   25.060909] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060912] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   25.060916] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060919] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   25.060922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060925] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   25.060929] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060932] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   25.060936] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060939] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   25.060943] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   25.060946] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   25.061207] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   25.135042] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   25.135938] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   25.178490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.202139] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000/0x0
[   25.231788] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   25.325608] vboxdrv: Found 2 processor cores.
[   25.327236] vboxdrv: fAsync=1 offMin=0x171e99 offMax=0x171e99
[   25.329232] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   25.329238] vboxdrv: Successfully loaded version 4.1.0 (interface 0x00190000).
[   25.555967] vboxpci: IOMMU not found (not registered)
[   26.332244] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   27.000242] ath5k 0000:04:05.0: PCI INT A disabled
[   27.018131] ath5k 0000:04:05.0: PCI INT A -> Link[LNK2] -> GSI 19 (level, high) -> IRQ 19
[   27.018205] ath5k 0000:04:05.0: registered as 'phy1'
[   27.721362] ath: EEPROM regdomain: 0x63
[   27.721365] ath: EEPROM indicates we should expect a direct regpair map
[   27.721371] ath: Country alpha2 being used: 00
[   27.721373] ath: Regpair used: 0x63
[   27.721378] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   27.721382] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721386] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   27.721390] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721393] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   27.721397] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721400] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   27.721403] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721406] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   27.721410] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721413] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   27.721417] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721420] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   27.721424] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721427] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   27.721431] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721434] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   27.721438] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721441] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   27.721445] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721448] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   27.721451] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721455] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   27.721458] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721461] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   27.721465] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   27.721468] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   27.721550] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   27.721724] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[   27.722723] ath5k phy1: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   27.752560] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.310067] hda_codec: ALC883: SKU not ready 0x411111f0
[   28.991029] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
[   30.679084] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90001c80000, using 3072k, total 3072k
[   30.679091] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   30.679094] vesafb: scrolling: redraw
[   30.679098] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   30.679365] Console: switching to colour frame buffer device 128x48
[   30.679396] fb0: VESA VGA frame buffer device
[   30.703993] ppdev: user-space parallel port driver
[   30.731341] audit_printk_skb: 9 callbacks suppressed
[   30.731346] type=1400 audit(1311187023.669:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1222 comm="apparmor_parser"
[   30.732035] type=1400 audit(1311187023.669:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1222 comm="apparmor_parser"
[   37.360393] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[  598.360028] CE: hpet increased min_delta_ns to 11520 nsec
[ 1123.050866] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2790.691644] acer-wmi: Acer Laptop ACPI-WMI Extras
[ 2809.681703] acer-wmi: Acer Laptop WMI Extras unloaded
[ 3675.870411] ath5k 0000:04:05.0: PCI INT A disabled
[ 3728.041926] ath5k 0000:04:05.0: PCI INT A -> Link[LNK2] -> GSI 19 (level, high) -> IRQ 19
[ 3728.042097] ath5k 0000:04:05.0: registered as 'phy2'
[ 3728.747086] ath: EEPROM regdomain: 0x63
[ 3728.747089] ath: EEPROM indicates we should expect a direct regpair map
[ 3728.747094] ath: Country alpha2 being used: 00
[ 3728.747096] ath: Regpair used: 0x63
[ 3728.747101] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747105] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747108] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747112] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747115] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747119] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747122] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747126] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747129] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747133] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747136] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747140] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747143] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747147] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747150] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747154] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747157] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747161] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747164] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747168] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747171] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747175] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747178] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747182] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747185] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 3728.747189] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 3728.747192] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[ 3728.747264] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3728.747511] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[ 3728.748496] ath5k phy2: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[ 3728.801477] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6327.853931] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6328.050107] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6328.250080] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6328.450086] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6338.953622] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6339.150127] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6339.350110] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6339.550123] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6350.023671] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6350.220207] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6350.420088] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6350.620095] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6361.182734] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6361.380083] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6361.580087] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6361.780086] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6372.315848] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6372.510100] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6372.710109] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6372.910101] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6383.404944] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6383.600099] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6383.800109] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6384.000095] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6397.962898] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6398.160099] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6398.360140] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6398.560120] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6409.062923] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6409.260133] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6409.460113] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6409.660138] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6420.143256] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6420.340110] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6420.540104] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6420.750164] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6431.253404] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6431.450121] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6431.650139] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6431.850111] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6442.333753] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6442.530105] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6442.730116] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6442.930114] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6453.492935] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6453.690083] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6453.890083] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6454.090088] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6461.072798] wlan0: direct probe to 00:18:01:fd:a7:4c (try 1/3)
[ 6461.270099] wlan0: direct probe to 00:18:01:fd:a7:4c (try 2/3)
[ 6461.470108] wlan0: direct probe to 00:18:01:fd:a7:4c (try 3/3)
[ 6461.680058] wlan0: direct probe to 00:18:01:fd:a7:4c timed out
[ 6472.252795] wlan0: authenticate with 00:18:01:fd:a7:4c (try 1)
[ 6472.254348] wlan0: authenticated
[ 6472.254456] wlan0: associate with 00:18:01:fd:a7:4c (try 1)
[ 6472.256746] wlan0: RX AssocResp from 00:18:01:fd:a7:4c (capab=0x431 status=0 aid=1)
[ 6472.256757] wlan0: associated
[ 6472.258452] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6472.258637] cfg80211: Calling CRDA for country: US
[ 6472.563922] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.563937] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.563944] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.563952] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.563959] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.563966] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.563973] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.563980] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.563986] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.563994] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564000] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.564008] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564014] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.564021] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564027] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.564035] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564041] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.564049] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564055] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.564062] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564068] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 6472.564076] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 6472.564082] cfg80211: Disabling freq 2467 MHz
[ 6472.564086] cfg80211: Disabling freq 2472 MHz
[ 6472.564091] cfg80211: Disabling freq 2484 MHz
[ 6472.564104] cfg80211: Regulatory domain changed to country: US
[ 6472.564109] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6472.564116] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 6472.564124] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 6472.564131] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6472.564138] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6472.564145] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6472.564152] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 6483.140056] wlan0: no IPv6 routers present

---

### Post by JadeLinux on 2011-07-20
markfrazer@mobiledaddy:~$ sudo lshw -c network
[sudo] password for markfrazer: 
  *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:9b:d7:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.9 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:c3000000-c300ffff

---

### Post by JadeLinux on 2011-07-20
Cell 02 - Address: 00:18:01:FD:A7:4C
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"MonkeyWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000528864f7268
                    Extra: Last beacon: 12130ms ago
                    IE: Unknown: 000E4D6F6E6B6579576972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00

---

### Post by JadeLinux on 2011-07-20
markfrazer@mobiledaddy:~$ uname -mr
2.6.38-10-generic x86_64

---

### Post by JadeLinux on 2011-07-20
sorry for all the posts, but i went down a list of what i thought i was supposed to post to diagnose issue.

---

### Post by bkratz on 2011-07-20
This looks to be interesting and relatively current

[http://ubuntuforums.org/showthread.php?p=10884683](http://ubuntuforums.org/showthread.php?p=10884683)

---

### Post by JadeLinux on 2011-07-20
not really exactly sure what i did, but for some reason my wifi is working now. the only thing i can think of is i searched the software center for atheros, and installed hostapd package. Now for some reason that i dont understand it seems to be connecting fine.
 
ooops spoke too soon, this is a very tempermental bug, every time i reboot it is totally random as to whether it works or not.  It seems to really struggle to find my access point.  And it continuously asks for the pass key.
 
Is there a way to disable the keyring password from popping up?

---

