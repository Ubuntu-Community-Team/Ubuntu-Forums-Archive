---
title: "Slow wireless connection - 1mbit out of 10mbit (12.04lts 64bit)"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by Magnus Solmyr on 2012-09-10
[B]Wireless Connection Speed Issue
[/B]I recently formated and wanted to try Ubuntu instead of Windows 7, but I have an issue with my wireless connection speed. My connection Speed with Windows 7 was 12mbit download, but with Ubuntu I only have 1mbit or less download speed.  That is to slow for me, and I really want the speed im paying for. Can also notice that other computers in the house have no issues with Internet speed. 

So if Someone can try to help me, that would be nice. I have also tried some solutions that I have googled up, but with no success... 
 
**1 ) Machine Brand and Model (PC/Laptop)**:
     Code:
     [ASUS P8Z77-V Z77 S-1155 ATX IVY]("https://www.dustinhome.no/product/5010625155/") 

**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     Using the onboard wi-fi GO!

([COLOR=Red]hint[/COLOR]) use **grep** to get only information about the Wireless
     Code:
     06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)


**3 ) check interface:**
     Code:
     $ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:60:00:e2:26:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7400000-f7420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:169002 (169.0 KB)  TX bytes:169002 (169.0 KB)

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:41:02:ba  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe41:2ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12289524 (12.2 MB)  TX bytes:1682190 (1.6 MB)


$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"privat0455alv"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:13:49:80:14:4A   
          Bit Rate=36 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

eth0      no wireless extensions.


 **4 ) Check for modules:**
     Code:
     $ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
nvidia              11257276  41 
snd_usb_audio         122982  2 
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
snd                    78855  26 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 132390  0 
mac80211              506816  1 ath9k
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
ath9k_common           14053  1 ath9k
soundcore              15091  1 snd
sparse_keymap          13890  1 asus_wmi
mxm_wmi                12979  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
psmouse                87692  0 
serio_raw              13211  0 
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19596  0 
wmi                    19256  2 asus_wmi,mxm_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
e1000e                156693  0 



**5 ) Kernel boot messages**
     Code:
     $ dmesg
[    1.195877] pci 0000:00:1c.7: setting latency timer to 64
[    1.195879] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.195880] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.195882] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.195883] pci_bus 0000:00: resource 7 [mem 0x000d8000-0x000dbfff]
[    1.195884] pci_bus 0000:00: resource 8 [mem 0x000dc000-0x000dffff]
[    1.195885] pci_bus 0000:00: resource 9 [mem 0xe0000000-0xfeafffff]
[    1.195887] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    1.195888] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    1.195889] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
[    1.195890] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    1.195891] pci_bus 0000:03: resource 1 [mem 0xf7300000-0xf73fffff]
[    1.195893] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.195894] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.195895] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.195896] pci_bus 0000:04: resource 7 [mem 0x000d8000-0x000dbfff]
[    1.195897] pci_bus 0000:04: resource 8 [mem 0x000dc000-0x000dffff]
[    1.195898] pci_bus 0000:04: resource 9 [mem 0xe0000000-0xfeafffff]
[    1.195900] pci_bus 0000:05: resource 8 [io  0x0000-0x0cf7]
[    1.195901] pci_bus 0000:05: resource 9 [io  0x0d00-0xffff]
[    1.195902] pci_bus 0000:05: resource 10 [mem 0x000a0000-0x000bffff]
[    1.195903] pci_bus 0000:05: resource 11 [mem 0x000d8000-0x000dbfff]
[    1.195904] pci_bus 0000:05: resource 12 [mem 0x000dc000-0x000dffff]
[    1.195905] pci_bus 0000:05: resource 13 [mem 0xe0000000-0xfeafffff]
[    1.195906] pci_bus 0000:06: resource 1 [mem 0xf7200000-0xf72fffff]
[    1.195908] pci_bus 0000:07: resource 1 [mem 0xf7100000-0xf71fffff]
[    1.195924] NET: Registered protocol family 2
[    1.196102] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.196626] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.197413] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.197510] TCP: Hash tables configured (established 524288 bind 65536)
[    1.197512] TCP reno registered
[    1.197524] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    1.197560] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    1.197627] NET: Registered protocol family 1
[    1.197641] pci 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.197697] pci 0000:00:14.0: PCI INT A disabled
[    1.197706] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.217623] pci 0000:00:1a.0: PCI INT A disabled
[    1.217642] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.237581] pci 0000:00:1d.0: PCI INT A disabled
[    1.237597] pci 0000:01:00.0: Boot video device
[    1.237618] pci 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.237655] pci 0000:07:00.0: PCI INT A disabled
[    1.237658] PCI: CLS 64 bytes, default 64
[    1.237659] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.237661] Placing 64MB software IO TLB between ffff8800d9f5d000 - ffff8800ddf5d000
[    1.237662] software IO TLB at phys 0xd9f5d000 - 0xddf5d000
[    1.238018] audit: initializing netlink socket (disabled)
[    1.238022] type=2000 audit(1347269269.952:1): initialized
[    1.253563] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.255048] VFS: Disk quotas dquot_6.5.2
[    1.255073] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.255310] fuse init (API version 7.17)
[    1.255355] msgmni has been set to 32004
[    1.255532] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.255546] io scheduler noop registered
[    1.255547] io scheduler deadline registered
[    1.255564] io scheduler cfq registered (default)
[    1.255612] pcieport 0000:00:01.0: setting latency timer to 64
[    1.255627] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.255664] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.255699] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.255752] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.255786] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    1.255839] pcieport 0000:00:1c.6: setting latency timer to 64
[    1.255874] pcieport 0000:00:1c.6: irq 43 for MSI/MSI-X
[    1.255926] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.255960] pcieport 0000:00:1c.7: irq 44 for MSI/MSI-X
[    1.256020] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    1.256021] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.256023] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.256024] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    1.256036] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.256039] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.256052] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.256053] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.256056] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    1.256067] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
[    1.256069] pci 0000:06:00.0: Signaling PME through PCIe PME interrupt
[    1.256072] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
[    1.256083] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    1.256084] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    1.256087] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    1.256098] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.256109] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.256146] efifb: probing for efifb
[    1.256465] efifb: framebuffer at 0xf1000000, mapped to 0xffffc9000b700000, using 1920k, total 1920k
[    1.256466] efifb: mode is 800x600x32, linelength=3200, pages=1
[    1.256467] efifb: scrolling: redraw
[    1.256468] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.256511] Console: switching to colour frame buffer device 100x37
[    1.256519] fb0: EFI VGA frame buffer device
[    1.256522] intel_idle: MWAIT substates: 0x1120
[    1.256523] intel_idle: does not run on family 6 model 58
[    1.256573] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.256577] ACPI: Power Button [PWRB]
[    1.256599] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.256600] ACPI: Power Button [PWRF]
[    1.256648] ACPI: Fan [FAN0] (off)
[    1.256665] ACPI: Fan [FAN1] (off)
[    1.256681] ACPI: Fan [FAN2] (off)
[    1.256695] ACPI: Fan [FAN3] (off)
[    1.256710] ACPI: Fan [FAN4] (off)
[    1.289630] Monitor-Mwait will be used to enter C-1 state
[    1.313579] thermal LNXTHERM:00: registered as thermal_zone0
[    1.313580] ACPI: Thermal Zone [TZ00] (28 C)
[    1.313684] thermal LNXTHERM:01: registered as thermal_zone1
[    1.313685] ACPI: Thermal Zone [TZ01] (30 C)
[    1.313709] ERST: Table is not found!
[    1.313710] GHES: HEST is not enabled!
[    1.313744] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.334094] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.409692] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.445308] Linux agpgart interface v0.103
[    1.446067] brd: module loaded
[    1.446432] loop: module loaded
[    1.446493] ahci 0000:00:1f.2: version 3.0
[    1.446498] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.446532] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.461156] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0xb impl SATA mode
[    1.461158] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.461161] ahci 0000:00:1f.2: setting latency timer to 64
[    1.477340] scsi0 : ahci
[    1.477382] scsi1 : ahci
[    1.477417] scsi2 : ahci
[    1.477450] scsi3 : ahci
[    1.477483] scsi4 : ahci
[    1.477517] scsi5 : ahci
[    1.477657] ata1: SATA max UDMA/133 abar m2048@0xf7436000 port 0xf7436100 irq 45
[    1.477659] ata2: SATA max UDMA/133 abar m2048@0xf7436000 port 0xf7436180 irq 45
[    1.477660] ata3: DUMMY
[    1.477661] ata4: SATA max UDMA/133 abar m2048@0xf7436000 port 0xf7436280 irq 45
[    1.477662] ata5: DUMMY
[    1.477663] ata6: DUMMY
[    1.477677] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.477734] ahci 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.477766] ahci: SSS flag set, parallel bus scan disabled
[    1.477817] ahci 0000:03:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.477819] ahci 0000:03:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    1.477825] ahci 0000:03:00.0: setting latency timer to 64
[    1.477976] scsi6 : ahci
[    1.478012] scsi7 : ahci
[    1.478036] ata7: SATA max UDMA/133 abar m512@0xf7300000 port 0xf7300100 irq 46
[    1.478039] ata8: SATA max UDMA/133 abar m512@0xf7300000 port 0xf7300180 irq 46
[    1.478206] Fixed MDIO Bus: probed
[    1.478215] tun: Universal TUN/TAP device driver, 1.6
[    1.478215] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.478242] PPP generic driver version 2.4.2
[    1.478292] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.478300] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.478310] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.478312] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.478338] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.478357] ehci_hcd 0000:00:1a.0: debug port 2
[    1.482229] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.482238] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7438000
[    1.497072] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.497139] hub 1-0:1.0: USB hub found
[    1.497141] hub 1-0:1.0: 2 ports detected
[    1.497173] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.497181] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.497183] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.497208] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.497224] ehci_hcd 0000:00:1d.0: debug port 2
[    1.501114] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.501123] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7437000
[    1.513040] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.513096] hub 2-0:1.0: USB hub found
[    1.513100] hub 2-0:1.0: 2 ports detected
[    1.513132] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.513138] uhci_hcd: USB Universal Host Controller Interface driver
[    1.513152] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.513169] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.513171] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.513195] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.513264] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.513267] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf7420000
[    1.513301] xhci_hcd 0000:00:14.0: irq 47 for MSI/MSI-X
[    1.513368] xHCI xhci_add_endpoint called for root hub
[    1.513370] xHCI xhci_check_bandwidth called for root hub
[    1.513382] hub 3-0:1.0: USB hub found
[    1.513387] hub 3-0:1.0: 4 ports detected
[    1.513420] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.513442] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.513483] xHCI xhci_add_endpoint called for root hub
[    1.513484] xHCI xhci_check_bandwidth called for root hub
[    1.513496] hub 4-0:1.0: USB hub found
[    1.513501] hub 4-0:1.0: 4 ports detected
[    1.548989] xhci_hcd 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.549009] xhci_hcd 0000:07:00.0: setting latency timer to 64
[    1.549012] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    1.549041] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 5
[    1.610052] xhci_hcd 0000:07:00.0: irq 19, io mem 0xf7100000
[    1.610100] xhci_hcd 0000:07:00.0: irq 48 for MSI/MSI-X
[    1.610102] xhci_hcd 0000:07:00.0: irq 49 for MSI/MSI-X
[    1.610104] xhci_hcd 0000:07:00.0: irq 50 for MSI/MSI-X
[    1.610107] xhci_hcd 0000:07:00.0: irq 51 for MSI/MSI-X
[    1.610109] xhci_hcd 0000:07:00.0: irq 52 for MSI/MSI-X
[    1.610111] xhci_hcd 0000:07:00.0: irq 53 for MSI/MSI-X
[    1.610113] xhci_hcd 0000:07:00.0: irq 54 for MSI/MSI-X
[    1.610115] xhci_hcd 0000:07:00.0: irq 55 for MSI/MSI-X
[    1.610246] xHCI xhci_add_endpoint called for root hub
[    1.610247] xHCI xhci_check_bandwidth called for root hub
[    1.610261] hub 5-0:1.0: USB hub found
[    1.610266] hub 5-0:1.0: 2 ports detected
[    1.610298] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    1.610323] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 6
[    1.610377] xHCI xhci_add_endpoint called for root hub
[    1.610378] xHCI xhci_check_bandwidth called for root hub
[    1.610390] hub 6-0:1.0: USB hub found
[    1.610395] hub 6-0:1.0: 2 ports detected
[    1.644819] usbcore: registered new interface driver libusual
[    1.644839] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.647098] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.647101] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.647164] mousedev: PS/2 mouse device common for all mice
[    1.647238] rtc_cmos 00:06: RTC can wake from S4
[    1.647318] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.647342] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.647377] device-mapper: uevent: version 1.0.3
[    1.647412] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.647416] cpuidle: using governor ladder
[    1.647417] cpuidle: using governor menu
[    1.647418] EFI Variables Facility v0.08 2004-May-17
[    1.715567] TCP cubic registered
[    1.715614] NET: Registered protocol family 10
[    1.715827] NET: Registered protocol family 17
[    1.715829] Registering the dns_resolver key type
[    1.715908] PM: Hibernation image not present or could not be loaded.
[    1.715919] registered taskstats version 1
[    1.719599]   Magic number: 12:647:474
[    1.719673] rtc_cmos 00:06: setting system clock to 2012-09-10 09:27:50 UTC (1347269270)
[    1.719832] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.719833] EDD information not available.
[    1.796519] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.796532] ata7: SATA link down (SStatus 0 SControl 300)
[    1.796549] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.796564] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.802104] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.802107] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT3._GTF] (Node ffff8804044b35c8), AE_NOT_FOUND (20110623/psparse-536)
[    1.802192] ata4.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[    1.802194] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.802476] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.802479] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8804044b3460), AE_NOT_FOUND (20110623/psparse-536)
[    1.802568] ata1.00: ATA-8: SAMSUNG HD204UI, 1AQ10001, max UDMA/133
[    1.802569] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.807382] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.807384] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8804044b34d8), AE_NOT_FOUND (20110623/psparse-536)
[    1.807772] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.807774] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT3._GTF] (Node ffff8804044b35c8), AE_NOT_FOUND (20110623/psparse-536)
[    1.807791] ata2.00: ATA-8: Corsair Force GT, 1.3.3, max UDMA/133
[    1.807792] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.807855] ata4.00: configured for UDMA/133
[    1.808566] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.808569] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8804044b3460), AE_NOT_FOUND (20110623/psparse-536)
[    1.808667] ata1.00: configured for UDMA/133
[    1.808734] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD204UI  1AQ1 PQ: 0 ANSI: 5
[    1.808807] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.808809] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.808867] sd 0:0:0:0: [sda] Write Protect is off
[    1.808868] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.808891] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.817364] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.817367] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8804044b34d8), AE_NOT_FOUND (20110623/psparse-536)
[    1.817432]  sda: sda1
[    1.817559] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.818154] ata2.00: configured for UDMA/133
[    1.818193] scsi 1:0:0:0: Direct-Access     ATA      Corsair Force GT 1.3. PQ: 0 ANSI: 5
[    1.818253] sd 1:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.818265] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.818335] sd 1:0:0:0: [sdb] Write Protect is off
[    1.818336] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.818352] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.818354] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    1.818424] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.818432] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.818470] sd 3:0:0:0: [sdc] Write Protect is off
[    1.818472] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.818496] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.819170]  sdb: sdb1 sdb2 sdb3
[    1.819348] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.824439] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.829283]  sdc: sdc1
[    1.829401] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.956628] hub 1-1:1.0: USB hub found
[    1.956737] hub 1-1:1.0: 6 ports detected
[    2.067959] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.135848] ata8: SATA link down (SStatus 0 SControl 300)
[    2.136723] Freeing unused kernel memory: 920k freed
[    2.136792] Write protecting the kernel read-only data: 12288k
[    2.139657] Freeing unused kernel memory: 1616k freed
[    2.141831] Freeing unused kernel memory: 1200k freed
[    2.150167] udevd[139]: starting version 175
[    2.166196] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.166198] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.166225] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.166234] e1000e 0000:00:19.0: setting latency timer to 64
[    2.166334] e1000e 0000:00:19.0: irq 56 for MSI/MSI-X
[    2.196804] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    2.200154] hub 2-1:1.0: USB hub found
[    2.200259] hub 2-1:1.0: 8 ports detected
[    2.235653] Refined TSC clocksource calibration: 3500.023 MHz.
[    2.235656] Switching to clocksource tsc
[    2.367374] usb 5-2: new low-speed USB device number 2 using xhci_hcd
[    2.394724] usb 5-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.394726] usb 5-2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.474088] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) c8:60:00:e2:26:c1
[    2.474090] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.474122] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    2.479217] usb 1-1.5: new low-speed USB device number 3 using ehci_hcd
[    2.646888] usb 1-1.6: new full-speed USB device number 4 using ehci_hcd
[    2.743046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.745796] udevd[373]: starting version 175
[    2.751687] Adding 16730108k swap on /dev/sdb3.  Priority:-1 extents:1 across:16730108k SS
[    2.752590] lp: driver loaded but no devices found
[    2.762134] wmi: Mapper loaded
[    2.778215] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    2.778433] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.778437] mei 0000:00:16.0: setting latency timer to 64
[    2.778483] mei 0000:00:16.0: irq 57 for MSI/MSI-X
[    2.785298] cfg80211: Calling CRDA to update world regulatory domain
[    2.816707] input: Cypress Cypress USB Keyboard / PS2 Mouse as /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb5/5-2/5-2:1.0/input/input2
[    2.816779] generic-usb 0003:04B4:0101.0001: input,hidraw0: USB HID v1.00 Keyboard [Cypress Cypress USB Keyboard / PS2 Mouse] on usb-0000:07:00.0-2/input0
[    2.823744] input: Cypress Cypress USB Keyboard / PS2 Mouse as /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb5/5-2/5-2:1.1/input/input3
[    2.823840] generic-usb 0003:04B4:0101.0002: input,hidraw1: USB HID v1.00 Mouse [Cypress Cypress USB Keyboard / PS2 Mouse] on usb-0000:07:00.0-2/input1
[    2.825859] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
[    2.825928] generic-usb 0003:045E:0039.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.0-1.5/input0
[    2.828067] input: Logitech Logitech G35 Headset as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.3/input/input5
[    2.828121] generic-usb 0003:046D:0A15.0004: input,hidraw3: USB HID v1.00 Device [Logitech Logitech G35 Headset] on usb-0000:00:1a.0-1.6/input3
[    2.828132] usbcore: registered new interface driver usbhid
[    2.828133] usbhid: USB HID core driver
[    2.834387] nvidia: module license 'NVIDIA' taints kernel.
[    2.834389] Disabling lock debugging due to kernel taint
[    2.837008] cfg80211: World regulatory domain updated:
[    2.837011] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    2.837012] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.837014] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.837015] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.837016] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.837018] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.841294] asus_wmi: ASUS WMI generic driver loaded
[    2.841763] asus_wmi: Initialization: 0x0
[    2.841785] asus_wmi: BIOS WMI version: 0.9
[    2.841826] asus_wmi: SFUN value: 0x0
[    2.842101] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input6
[    2.843980] type=1400 audit(1347269271.623:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=521 comm="apparmor_parser"
[    2.844252] type=1400 audit(1347269271.623:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=521 comm="apparmor_parser"
[    2.844413] type=1400 audit(1347269271.623:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=521 comm="apparmor_parser"
[    2.847097] ath9k 0000:06:00.0: enabling device (0000 -> 0002)
[    2.847104] ath9k 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.847116] ath9k 0000:06:00.0: setting latency timer to 64
[    2.855596] ath: EEPROM regdomain: 0x60
[    2.855598] ath: EEPROM indicates we should expect a direct regpair map
[    2.855600] ath: Country alpha2 being used: 00
[    2.855601] ath: Regpair used: 0x60
[    2.855604] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    2.855606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855607] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    2.855610] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855611] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    2.855613] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855615] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    2.855616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855618] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    2.855620] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855621] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    2.855623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855625] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    2.855627] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855629] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    2.855631] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855632] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    2.855634] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855636] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    2.855638] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855639] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    2.855641] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855643] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    2.855644] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855646] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    2.855647] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.855649] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    2.855650] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    2.856340] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    2.858547] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    2.858948] Registered led device: ath9k-phy0
[    2.858955] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc9000cb80000, irq=18
[    2.872765] usbcore: registered new interface driver snd-usb-audio
[    2.877749] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.877755] nvidia 0000:01:00.0: setting latency timer to 64
[    2.877758] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    2.877821] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.43  Sun Aug 19 20:14:03 PDT 2012
[    2.899801] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    2.899811] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.899853] snd_hda_intel 0000:00:1b.0: irq 58 for MSI/MSI-X
[    2.899872] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    2.947585] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    2.947628] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    2.947661] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    2.947692] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    2.947724] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    2.947757] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    2.947788] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    2.947821] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    2.947946] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    2.947955] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.947956] hda_intel: Disabling MSI
[    2.947988] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[    3.026438] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[    3.055498] init: failsafe main process (866) killed by TERM signal
[    3.076815] ppdev: user-space parallel port driver
[    3.085432] Bluetooth: Core ver 2.16
[    3.085447] NET: Registered protocol family 31
[    3.085448] Bluetooth: HCI device and connection manager initialized
[    3.085450] Bluetooth: HCI socket layer initialized
[    3.085451] Bluetooth: L2CAP socket layer initialized
[    3.085455] Bluetooth: SCO socket layer initialized
[    3.086707] Bluetooth: RFCOMM TTY layer initialized
[    3.086711] Bluetooth: RFCOMM socket layer initialized
[    3.086712] Bluetooth: RFCOMM ver 1.11
[    3.087319] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.087321] Bluetooth: BNEP filters: protocol multicast
[    3.087742] type=1400 audit(1347269271.867:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=942 comm="apparmor_parser"
[    3.088035] type=1400 audit(1347269271.867:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=942 comm="apparmor_parser"
[    3.093773] type=1400 audit(1347269271.871:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=971 comm="apparmor_parser"
[    3.093899] type=1400 audit(1347269271.871:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=972 comm="apparmor_parser"
[    3.093942] type=1400 audit(1347269271.871:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=978 comm="apparmor_parser"
[    3.094136] type=1400 audit(1347269271.875:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=972 comm="apparmor_parser"
[    3.261784] e1000e 0000:00:19.0: irq 56 for MSI/MSI-X
[    3.317552] e1000e 0000:00:19.0: irq 56 for MSI/MSI-X
[    3.318285] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.318543] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.352354] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.352455] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.521122] HDMI status: Codec=0 Pin=4 Presence_Detect=0 ELD_Valid=0
[    3.529103] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[    3.537087] HDMI status: Codec=0 Pin=6 Presence_Detect=0 ELD_Valid=0
[    3.545071] HDMI status: Codec=0 Pin=7 Presence_Detect=0 ELD_Valid=0
[    3.545122] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input15
[    3.545171] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input16
[    3.545209] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input17
[    3.545244] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input18
[    3.567068] ------------[ cut here ]------------
[    3.567073] WARNING: at /build/buildd/linux-3.2.0/arch/x86/mm/ioremap.c:102 __ioremap_caller+0x312/0x390()
[    3.567074] Hardware name: System Product Name
[    3.567075] Modules linked in: snd_hda_codec_hdmi bnep rfcomm bluetooth parport_pc ppdev nls_iso8859_1 nls_cp437 vfat fat snd_hda_codec_realtek snd_hda_intel snd_hda_codec nvidia(P) snd_usb_audio snd_pcm snd_hwdep snd_usbmidi_lib snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq arc4 snd_timer snd_seq_device joydev snd ath9k mac80211 eeepc_wmi asus_wmi ath9k_common soundcore sparse_keymap mxm_wmi usbhid hid psmouse serio_raw ath9k_hw ath cfg80211 mei(C) snd_page_alloc video wmi mac_hid lp parport e1000e
[    3.567098] Pid: 1096, comm: Xorg Tainted: P         C O 3.2.0-30-generic #48-Ubuntu
[    3.567099] Call Trace:
[    3.567102]  [<ffffffff81066d7f>] warn_slowpath_common+0x7f/0xc0
[    3.567104]  [<ffffffff81066dda>] warn_slowpath_null+0x1a/0x20
[    3.567106]  [<ffffffff810410d2>] __ioremap_caller+0x312/0x390
[    3.567159]  [<ffffffffa0806565>] ? os_map_kernel_space+0x85/0xf0 [nvidia]
[    3.567162]  [<ffffffff81041184>] ioremap_cache+0x14/0x20
[    3.567203]  [<ffffffffa0806565>] os_map_kernel_space+0x85/0xf0 [nvidia]
[    3.567247]  [<ffffffffa07d1e68>] _nv014894rm+0x76/0x92 [nvidia]
[    3.567282]  [<ffffffffa01ffa5e>] ? _nv009687rm+0x89/0x142 [nvidia]
[    3.567316]  [<ffffffffa01ffbcf>] ? _nv014465rm+0xb8/0x102 [nvidia]
[    3.567350]  [<ffffffffa0200082>] ? _nv014503rm+0x58/0x9e [nvidia]
[    3.567384]  [<ffffffffa01fbae8>] ? _nv014475rm+0xbe/0x2f0 [nvidia]
[    3.567417]  [<ffffffffa01fbdc5>] ? _nv014508rm+0xab/0x174 [nvidia]
[    3.567451]  [<ffffffffa01fbede>] ? _nv014474rm+0x50/0x5d [nvidia]
[    3.567485]  [<ffffffffa02020b2>] ? _nv014449rm+0x82d/0x96b [nvidia]
[    3.567528]  [<ffffffffa07e21af>] ? _nv012675rm+0x174/0x573 [nvidia]
[    3.567569]  [<ffffffffa07e212d>] ? _nv012675rm+0xf2/0x573 [nvidia]
[    3.567614]  [<ffffffffa024c361>] ? _nv004023rm+0x1bb/0x19e9 [nvidia]
[    3.567705]  [<ffffffffa05a4b89>] ? _nv004048rm+0x8670/0xae5b [nvidia]
[    3.567794]  [<ffffffffa05a354b>] ? _nv004048rm+0x7032/0xae5b [nvidia]
[    3.567825]  [<ffffffffa01d4d4c>] ? _nv009994rm+0x25/0x40 [nvidia]
[    3.567867]  [<ffffffffa07e1ec1>] ? _nv014949rm+0x7c9/0x943 [nvidia]
[    3.567908]  [<ffffffffa07e2e6f>] ? _nv001096rm+0x42a/0x6b4 [nvidia]
[    3.567950]  [<ffffffffa07db444>] ? rm_init_adapter+0xac/0x146 [nvidia]
[    3.567990]  [<ffffffffa07fb8bc>] ? nv_kern_open+0x46c/0x820 [nvidia]
[    3.567993]  [<ffffffff8117ba40>] ? mount_fs+0x1b0/0x1b0
[    3.567995]  [<ffffffff8117c48a>] ? chrdev_open+0xda/0x230
[    3.567996]  [<ffffffff81175bd0>] ? __dentry_open+0x290/0x360
[    3.567998]  [<ffffffff8117c3b0>] ? cdev_put+0x30/0x30
[    3.568001]  [<ffffffff8129cdbc>] ? security_inode_permission+0x1c/0x30
[    3.568003]  [<ffffffff8118389a>] ? inode_permission+0x4a/0x110
[    3.568004]  [<ffffffff8117624d>] ? vfs_open+0x3d/0x40
[    3.568006]  [<ffffffff81177130>] ? nameidata_to_filp+0x40/0x50
[    3.568007]  [<ffffffff811860d8>] ? do_last+0x3f8/0x730
[    3.568009]  [<ffffffff811877b1>] ? path_openat+0xd1/0x3f0
[    3.568012]  [<ffffffff8165a41e>] ? _raw_spin_lock+0xe/0x20
[    3.568014]  [<ffffffff8112ede0>] ? shmem_xattr_get.isra.24+0x80/0xd0
[    3.568016]  [<ffffffff81187bf2>] ? do_filp_open+0x42/0xa0
[    3.568019]  [<ffffffff81319321>] ? strncpy_from_user+0x31/0x40
[    3.568020]  [<ffffffff81182f3a>] ? do_getname+0x10a/0x180
[    3.568022]  [<ffffffff8165a41e>] ? _raw_spin_lock+0xe/0x20
[    3.568024]  [<ffffffff81194eb7>] ? alloc_fd+0xf7/0x150
[    3.568025]  [<ffffffff8117722d>] ? do_sys_open+0xed/0x220
[    3.568027]  [<ffffffff8119759f>] ? mntput+0x1f/0x30
[    3.568029]  [<ffffffff81177380>] ? sys_open+0x20/0x30
[    3.568031]  [<ffffffff81662a02>] ? system_call_fastpath+0x16/0x1b
[    3.568032] ---[ end trace 87c3efba963d165c ]---
[    3.999363] NVRM: GPU at 0000:01:00: GPU-562ff012-0787-233b-c262-c76149871dba
[    3.999393] NVRM: Your system is not currently configured to drive a VGA console
[    3.999395] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[    3.999396] NVRM: requires the use of a text-mode VGA console. Use of other console
[    3.999397] NVRM: drivers including, but not limited to, vesafb, may result in
[    3.999398] NVRM: corruption and stability problems, and is not supported.
[    4.980400] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[    6.208958] wlan0: authenticate with 00:13:49:80:14:4a (try 1)
[    6.210617] wlan0: authenticated
[    6.234324] wlan0: associate with 00:13:49:80:14:4a (try 1)
[    6.236265] wlan0: RX AssocResp from 00:13:49:80:14:4a (capab=0x11 status=0 aid=1)
[    6.236266] wlan0: associated
[    6.237027] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.324084] wlan0: no IPv6 routers present


 
**6 ) Network configuration**
     Code:
     $ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: c8:60:00:e2:26:c1
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:56 memory:f7400000-f741ffff memory:f7439000-f7439fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 94:db:c9:41:02:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-30-generic firmware=N/A ip=10.0.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7200000-f727ffff memory:f7280000-f728ffff


**7 ) Scan for networks:**
     Code:
     $ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:49:80:14:4A
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"privat0455alv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c61bc2623c
                    Extra: Last beacon: 100132ms ago
                    IE: Unknown: 000D70726976617430343535616C76
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010D
                    IE: Unknown: 32080C1218243048606C

eth0      Interface doesn't support scanning.


**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d
Description:    Ubuntu 12.04.1 LTS


**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     $ uname -mr
3.2.0-30-generic x86_64


**10 ) Restarting the network:**
     Code:
     $ sudo /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                                                                  [ OK ]

---

