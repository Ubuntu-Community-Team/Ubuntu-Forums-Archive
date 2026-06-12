---
title: "Cannot get Broadcom Corporation BCM4312 802.11b/g to connect w/ Ubuntu 9.10."
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Maxximiliann on 2009-12-15
Hi!
 

 This is my 2nd day working with Ubuntu 9.10. I can't get my wireless connection to access the net. Any help would be greatly appreciated!
 

 **1 ) Machine Brand and Model (PC/Laptop)**:
  Dell Studio 1735 Laptop
  

  **2 ) ** 
 $ lspci Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
 $ lsusb Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 002 Device 004: ID 05ca:18a1 Ricoh Co., Ltd  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  Bus 003 Device 005: ID 413c:8156 Dell Computer Corp.  Bus 003 Device 004: ID 413c:8158 Dell Computer Corp.  Bus 003 Device 003: ID 413c:8157 Dell Computer Corp.  Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp.  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  

  

  **3 ) check interface:**
  Code:
 $ ifconfig eth0      Link encap:Ethernet  HWaddr 00:21:70:71:55:25             inet6 addr: fe80::221:70ff:fe71:5525/64 Scope:Link            UP BROADCAST MULTICAST  MTU:1500  Metric:1            RX packets:14234 errors:0 dropped:0 overruns:0 frame:0            TX packets:12922 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:1000            RX bytes:14606625 (14.6 MB)  TX bytes:1788337 (1.7 MB)            Interrupt:17   eth2      Link encap:Ethernet  HWaddr 00:22:5f:06:e9:7b             inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0            inet6 addr: fe80::222:5fff:fe06:e97b/64 Scope:Link            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1            RX packets:8364 errors:0 dropped:0 overruns:0 frame:233207            TX packets:967 errors:34 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:1000            RX bytes:633985 (633.9 KB)  TX bytes:67095 (67.0 KB)            Interrupt:17 Base address:0xc000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0            inet6 addr: ::1/128 Scope:Host            UP LOOPBACK RUNNING  MTU:16436  Metric:1            RX packets:1545 errors:0 dropped:0 overruns:0 frame:0            TX packets:1545 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:0            RX bytes:147925 (147.9 KB)  TX bytes:147925 (147.9 KB)   $ iwconfig lo        no wireless extensions.   eth0      no wireless extensions.   pan0      no wireless extensions.   eth2      IEEE 802.11  Nickname:""            Access Point: Not-Associated    

  **4 ) Check for modules:**
  Code:
 $ lsmod ufs                    75524  0  qnx4                    8576  0  hfsplus                73568  0  hfs                    43232  0  minix                  27588  0  ntfs                   98240  0  vfat                   10716  0  msdos                   7836  0  fat                    51452  2 vfat,msdos  jfs                   177380  0  xfs                   512064  0  exportfs                4412  1 xfs  reiserfs              229288  0  wl                   1276032  0  michael_mic             2204  8  arc4                    1660  4  ecb                     2524  4  binfmt_misc             8356  1  ppdev                   6688  0  uvcvideo               59080  0  videodev               36736  1 uvcvideo  v4l1_compat            14496  2 uvcvideo,videodev  usblp                  12636  0  bridge                 47952  0  stp                     2272  1 bridge  bnep                   12060  2  snd_hda_codec_intelhdmi    12860  1  snd_hda_codec_idt      59844  1  snd_hda_intel          26920  2  snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel  snd_hwdep               7200  1 snd_hda_codec  lib80211_crypt_tkip     8636  0  sdhci_pci               7100  0  snd_pcm_oss            37920  0  snd_mixer_oss          16028  1 snd_pcm_oss  sdhci                  17472  1 sdhci_pci  snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  snd_seq_dummy           2656  0  snd_seq_oss            28576  0  joydev                 10272  0  snd_seq_midi            6432  0  snd_rawmidi            22208  1 snd_seq_midi  snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  snd_timer              22276  2 snd_pcm,snd_seq  snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device  soundcore               7264  1 snd  snd_page_alloc          9156  2 snd_hda_intel,snd_pcm  lib80211                6432  2 wl,lib80211_crypt_tkip  led_class               4096  1 sdhci  dell_wmi                2564  0  iptable_filter          3100  0  dell_laptop             8128  0  psmouse                56500  0  lp                      8964  0  ip_tables              11692  1 iptable_filter  parport                35340  2 ppdev,lp  dcdbas                  7292  1 dell_laptop  serio_raw               5280  0  btusb                  11856  2  x_tables               16544  1 ip_tables  fbcon                  36640  72  tileblit                2460  1 fbcon  font                    8124  1 fbcon  bitblit                 5372  1 fbcon  softcursor              1756  1 bitblit  usbhid                 38208  0  i915                  221064  3  usb_storage            52576  0  drm                   159584  3 i915  i2c_algo_bit            5760  1 i915  tg3                   109600  0  ohci1394               29900  0  ieee1394               86596  1 ohci1394  video                  19380  1 i915  output                  2780  1 video  intel_agp              27484  2 i915  agpgart                34988  2 drm,intel_agp 

  **5 ) Kernel boot messages**
  Code:
 $ dmesg [    0.372136] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling  [    0.372237] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling  [    0.372241] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling  [    0.372244] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling  [    0.372248] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling  [    0.394561] pnp: PnP ACPI: found 13 devices  [    0.394564] ACPI: ACPI bus type pnp unregistered  [    0.394568] PnPBIOS: Disabled by ACPI PNP  [    0.394583] system 00:06: ioport range 0xc80-0xcff could not be reserved  [    0.394592] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved  [    0.394598] system 00:0a: ioport range 0x900-0x97f has been reserved  [    0.394601] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved  [    0.394608] system 00:0b: ioport range 0xf400-0xf4fe has been reserved  [    0.394611] system 00:0b: ioport range 0x1080-0x10bf has been reserved  [    0.394614] system 00:0b: ioport range 0x10c0-0x10df has been reserved  [    0.394617] system 00:0b: ioport range 0x809-0x809 has been reserved  [    0.394624] system 00:0c: iomem range 0x0-0x9efff could not be reserved  [    0.394627] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved  [    0.394630] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved  [    0.394633] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved  [    0.394637] system 00:0c: iomem range 0x100000-0x7f65c7ff could not be reserved  [    0.394640] system 00:0c: iomem range 0x7f65c800-0x7f6fffff has been reserved  [    0.394643] system 00:0c: iomem range 0x7f700000-0x7f7fffff has been reserved  [    0.394646] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved  [    0.394649] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved  [    0.394653] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved  [    0.394656] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved  [    0.394659] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved  [    0.394662] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved  [    0.394666] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved  [    0.394669] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved  [    0.394672] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved  [    0.394676] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved  [    0.394679] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved  [    0.429378] AppArmor: AppArmor Filesystem Enabled  [    0.429461] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b  [    0.429463] pci 0000:00:1c.0:   IO window: disabled  [    0.429470] pci 0000:00:1c.0:   MEM window: disabled  [    0.429475] pci 0000:00:1c.0:   PREFETCH window: disabled  [    0.429481] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c  [    0.429484] pci 0000:00:1c.1:   IO window: disabled  [    0.429491] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff  [    0.429497] pci 0000:00:1c.1:   PREFETCH window: disabled  [    0.429503] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d  [    0.429507] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff  [    0.429514] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6bfffff  [    0.429521] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff  [    0.429530] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09  [    0.429532] pci 0000:00:1c.5:   IO window: disabled  [    0.429539] pci 0000:00:1c.5:   MEM window: 0xf6900000-0xf69fffff  [    0.429545] pci 0000:00:1c.5:   PREFETCH window: disabled  [    0.429551] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03  [    0.429553] pci 0000:00:1e.0:   IO window: disabled  [    0.429560] pci 0000:00:1e.0:   MEM window: 0xf6800000-0xf68fffff  [    0.429566] pci 0000:00:1e.0:   PREFETCH window: disabled  [    0.429584]   alloc irq_desc for 16 on node -1  [    0.429586]   alloc kstat_irqs on node -1  [    0.429593] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  [    0.429600] pci 0000:00:1c.0: setting latency timer to 64  [    0.429610]   alloc irq_desc for 17 on node -1  [    0.429612]   alloc kstat_irqs on node -1  [    0.429616] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17  [    0.429622] pci 0000:00:1c.1: setting latency timer to 64  [    0.429635]   alloc irq_desc for 19 on node -1  [    0.429636]   alloc kstat_irqs on node -1  [    0.429640] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19  [    0.429646] pci 0000:00:1c.3: setting latency timer to 64  [    0.429656] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17  [    0.429662] pci 0000:00:1c.5: setting latency timer to 64  [    0.429672] pci 0000:00:1e.0: setting latency timer to 64  [    0.429677] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]  [    0.429680] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]  [    0.429683] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]  [    0.429686] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]  [    0.429688] pci_bus 0000:0d: resource 1 mem: [0xf6a00000-0xf6bfffff]  [    0.429691] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]  [    0.429694] pci_bus 0000:09: resource 1 mem: [0xf6900000-0xf69fffff]  [    0.429697] pci_bus 0000:03: resource 1 mem: [0xf6800000-0xf68fffff]  [    0.429699] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]  [    0.429702] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]  [    0.429743] NET: Registered protocol family 2  [    0.429851] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  [    0.430207] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  [    0.430733] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  [    0.431090] TCP: Hash tables configured (established 131072 bind 65536)  [    0.431093] TCP reno registered  [    0.431216] NET: Registered protocol family 1  [    0.431303] Trying to unpack rootfs image as initramfs...  [    0.501513] Switched to high resolution mode on CPU 1  [    0.503992] Switched to high resolution mode on CPU 0  [    0.635216] Freeing initrd memory: 7465k freed  [    0.640626] Simple Boot Flag at 0x79 set to 0x1  [    0.640827] cpufreq-nforce2: No nForce2 chipset.  [    0.640858] Scanning for low memory corruption every 60 seconds  [    0.640975] audit: initializing netlink socket (disabled)  [    0.640995] type=2000 audit(1260834890.640:1): initialized  [    0.650214] highmem bounce pool size: 64 pages  [    0.650220] HugeTLB registered 4 MB page size, pre-allocated 0 pages  [    0.651806] VFS: Disk quotas dquot_6.5.2  [    0.651876] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  [    0.652467] fuse init (API version 7.12)  [    0.652557] msgmni has been set to 1706  [    0.652782] alg: No test for stdrng (krng)  [    0.652798] io scheduler noop registered  [    0.652800] io scheduler anticipatory registered  [    0.652802] io scheduler deadline registered  [    0.652847] io scheduler cfq registered (default)  [    0.652862] pci 0000:00:02.0: Boot video device  [    0.653183]   alloc irq_desc for 24 on node -1  [    0.653186]   alloc kstat_irqs on node -1  [    0.653200] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X  [    0.653214] pcieport-driver 0000:00:1c.0: setting latency timer to 64  [    0.653399]   alloc irq_desc for 25 on node -1  [    0.653401]   alloc kstat_irqs on node -1  [    0.653411] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X  [    0.653424] pcieport-driver 0000:00:1c.1: setting latency timer to 64  [    0.653602]   alloc irq_desc for 26 on node -1  [    0.653604]   alloc kstat_irqs on node -1  [    0.653614] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X  [    0.653626] pcieport-driver 0000:00:1c.3: setting latency timer to 64  [    0.653807]   alloc irq_desc for 27 on node -1  [    0.653809]   alloc kstat_irqs on node -1  [    0.653819] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X  [    0.653832] pcieport-driver 0000:00:1c.5: setting latency timer to 64  [    0.653950] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  [    0.654078] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  [    0.654252] ACPI: AC Adapter [AC] (on-line)  [    0.654334] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0  [    0.658852] ACPI: Lid Switch [LID]  [    0.658903] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1  [    0.658910] ACPI: Power Button [PBTN]  [    0.658957] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2  [    0.658960] ACPI: Sleep Button [SBTN]  [    0.659668] ACPI: SSDT 7f65d4f6 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)  [    0.660215] ACPI: SSDT 7f65ce8c 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)  [    0.660609] Monitor-Mwait will be used to enter C-1 state  [    0.660638] Monitor-Mwait will be used to enter C-2 state  [    0.660663] Monitor-Mwait will be used to enter C-3 state  [    0.660671] Marking TSC unstable due to TSC halts in idle  [    0.660693] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])  [    0.660721] processor LNXCPU:00: registered as cooling_device0  [    0.660725] ACPI: Processor [CPU0] (supports 8 throttling states)  [    0.661092] ACPI: SSDT 7f65d77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)  [    0.661429] ACPI: SSDT 7f65d471 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)  [    0.661935] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])  [    0.661962] processor LNXCPU:01: registered as cooling_device1  [    0.661967] ACPI: Processor [CPU1] (supports 8 throttling states)  [    0.674972] thermal LNXTHERM:01: registered as thermal_zone0  [    0.674981] ACPI: Thermal Zone [THM] (60 C)  [    0.675056] isapnp: Scanning for PnP cards...  [    0.756701] ACPI: Battery Slot [BAT0] (battery present)  [    1.031939] isapnp: No Plug & Play device found  [    1.033160] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled  [    1.034614] brd: module loaded  [    1.035094] loop: module loaded  [    1.035172] input: Macintosh mouse button emulation as /devices/virtual/input/input3  [    1.035261] ahci 0000:00:1f.2: version 3.0  [    1.035279] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  [    1.035320]   alloc irq_desc for 28 on node -1  [    1.035323]   alloc kstat_irqs on node -1  [    1.035337] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X  [    1.035419] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode  [    1.035423] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems  [    1.035429] ahci 0000:00:1f.2: setting latency timer to 64  [    1.048099] scsi0 : ahci  [    1.048216] scsi1 : ahci  [    1.048282] scsi2 : ahci  [    1.048529] ata1: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 28  [    1.048534] ata2: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb980 irq 28  [    1.048538] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 28  [    1.049581] Fixed MDIO Bus: probed  [    1.049621] PPP generic driver version 2.4.2  [    1.049736] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  [    1.049760]   alloc irq_desc for 22 on node -1  [    1.049763]   alloc kstat_irqs on node -1  [    1.049769] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22  [    1.049787] ehci_hcd 0000:00:1a.7: setting latency timer to 64  [    1.049791] ehci_hcd 0000:00:1a.7: EHCI Host Controller  [    1.049845] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1  [    1.053764] ehci_hcd 0000:00:1a.7: debug port 1  [    1.053772] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported  [    1.053810] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400  [    1.068019] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00  [    1.068109] usb usb1: configuration #1 chosen from 1 choice  [    1.068140] hub 1-0:1.0: USB hub found  [    1.068149] hub 1-0:1.0: 4 ports detected  [    1.068213]   alloc irq_desc for 20 on node -1  [    1.068215]   alloc kstat_irqs on node -1  [    1.068220] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20  [    1.068233] ehci_hcd 0000:00:1d.7: setting latency timer to 64  [    1.068237] ehci_hcd 0000:00:1d.7: EHCI Host Controller  [    1.068271] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2  [    1.072191] ehci_hcd 0000:00:1d.7: debug port 1  [    1.072199] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported  [    1.072213] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000  [    1.084019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  [    1.084087] usb usb2: configuration #1 chosen from 1 choice  [    1.084116] hub 2-0:1.0: USB hub found  [    1.084122] hub 2-0:1.0: 6 ports detected  [    1.084194] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  [    1.084214] uhci_hcd: USB Universal Host Controller Interface driver  [    1.084248] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  [    1.084257] uhci_hcd 0000:00:1a.0: setting latency timer to 64  [    1.084260] uhci_hcd 0000:00:1a.0: UHCI Host Controller  [    1.084301] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3  [    1.084331] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60  [    1.084416] usb usb3: configuration #1 chosen from 1 choice  [    1.084443] hub 3-0:1.0: USB hub found  [    1.084450] hub 3-0:1.0: 2 ports detected  [    1.084506]   alloc irq_desc for 21 on node -1  [    1.084508]   alloc kstat_irqs on node -1  [    1.084514] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  [    1.084521] uhci_hcd 0000:00:1a.1: setting latency timer to 64  [    1.084525] uhci_hcd 0000:00:1a.1: UHCI Host Controller  [    1.084556] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4  [    1.084594] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80  [    1.084677] usb usb4: configuration #1 chosen from 1 choice  [    1.084707] hub 4-0:1.0: USB hub found  [    1.084714] hub 4-0:1.0: 2 ports detected  [    1.084767] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  [    1.084775] uhci_hcd 0000:00:1d.0: setting latency timer to 64  [    1.084779] uhci_hcd 0000:00:1d.0: UHCI Host Controller  [    1.084811] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5  [    1.084841] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00  [    1.084924] usb usb5: configuration #1 chosen from 1 choice  [    1.084955] hub 5-0:1.0: USB hub found  [    1.084962] hub 5-0:1.0: 2 ports detected  [    1.085025] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  [    1.085032] uhci_hcd 0000:00:1d.1: setting latency timer to 64  [    1.085036] uhci_hcd 0000:00:1d.1: UHCI Host Controller  [    1.085067] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6  [    1.085098] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20  [    1.085188] usb usb6: configuration #1 chosen from 1 choice  [    1.085215] hub 6-0:1.0: USB hub found  [    1.085222] hub 6-0:1.0: 2 ports detected  [    1.085273] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22  [    1.085280] uhci_hcd 0000:00:1d.2: setting latency timer to 64  [    1.085284] uhci_hcd 0000:00:1d.2: UHCI Host Controller  [    1.085318] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7  [    1.085347] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40  [    1.085441] usb usb7: configuration #1 chosen from 1 choice  [    1.085470] hub 7-0:1.0: USB hub found  [    1.085477] hub 7-0:1.0: 2 ports detected  [    1.085595] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12  [    1.092811] serio: i8042 KBD port at 0x60,0x64 irq 1  [    1.092818] serio: i8042 AUX port at 0x60,0x64 irq 12  [    1.092895] mice: PS/2 mouse device common for all mice  [    1.093025] rtc_cmos 00:04: RTC can wake from S4  [    1.093062] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0  [    1.093097] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs  [    1.093214] device-mapper: uevent: version 1.0.3  [    1.093309] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  [    1.093375] device-mapper: multipath: version 1.1.0 loaded  [    1.093378] device-mapper: multipath round-robin: version 1.0.0 loaded  [    1.093512] EISA: Probing bus 0 at eisa.0  [    1.093520] Cannot allocate resource for EISA slot 1  [    1.093552] EISA: Detected 0 cards.  [    1.093702] cpuidle: using governor ladder  [    1.093832] cpuidle: using governor menu  [    1.094382] TCP cubic registered  [    1.094546] NET: Registered protocol family 10  [    1.095053] lo: Disabled Privacy Extensions  [    1.095411] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4  [    1.095429] NET: Registered protocol family 17  [    1.095453] Bluetooth: L2CAP ver 2.13  [    1.095455] Bluetooth: L2CAP socket layer initialized  [    1.095462] Bluetooth: SCO (Voice Link) ver 0.6  [    1.095463] Bluetooth: SCO socket layer initialized  [    1.095494] Bluetooth: RFCOMM TTY layer initialized  [    1.095497] Bluetooth: RFCOMM socket layer initialized  [    1.095499] Bluetooth: RFCOMM ver 1.11  [    1.096154] Using IPI No-Shortcut mode  [    1.096220] PM: Resume from disk failed.  [    1.096234] registered taskstats version 1  [    1.096372]   Magic number: 5:421:959  [    1.096483] rtc_cmos 00:04: setting system clock to 2009-12-14 23:54:52 UTC (1260834892)  [    1.096486] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  [    1.096488] EDD information not available.  [    1.368080] ata3: SATA link down (SStatus 0 SControl 300)  [    1.372081] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  [    1.372119] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  [    1.373911] ata1.00: ATA-8: ST9250320AS, DE04, max UDMA/133  [    1.373914] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)  [    1.376111] ata1.00: configured for UDMA/133  [    1.384890] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, D300, max UDMA/100  [    1.384905] ata2.00: applying bridge limits  [    1.392247] scsi 0:0:0:0: Direct-Access     ATA      ST9250320AS      DE04 PQ: 0 ANSI: 5  [    1.392383] sd 0:0:0:0: Attached scsi generic sg0 type 0  [    1.392423] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)  [    1.392472] sd 0:0:0:0: [sda] Write Protect is off  [    1.392476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  [    1.392501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  [    1.392634]  sda:  [    1.398760] ata2.00: configured for UDMA/100  [    1.404003]  sda1 sda2 <  [    1.412070] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4  [    1.412073] ata2: irq_stat 0x40000001  [    1.412078] ata2: hard resetting link  [    1.450293]  sda5 >  [    1.450582] sd 0:0:0:0: [sda] Attached SCSI disk  [    1.492080] usb 2-1: new high speed USB device using ehci_hcd and address 2  [    1.500040] Clocksource tsc unstable (delta = -305294766 ns)  [    1.625595] usb 2-1: configuration #1 chosen from 1 choice  [    1.736066] usb 2-2: new high speed USB device using ehci_hcd and address 3  [    1.869828] usb 2-2: configuration #1 chosen from 1 choice  [    1.980074] usb 2-5: new high speed USB device using ehci_hcd and address 4  [    2.119329] usb 2-5: configuration #1 chosen from 1 choice  [    2.136077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  [    2.162821] ata2.00: configured for UDMA/100  [    2.163571] ata2: EH complete  [    2.164837] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D300 PQ: 0 ANSI: 5  [    2.171392] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray  [    2.171396] Uniform CD-ROM driver Revision: 3.20  [    2.171486] sr 1:0:0:0: Attached scsi CD-ROM sr0  [    2.171535] sr 1:0:0:0: Attached scsi generic sg1 type 5  [    2.171579] Freeing unused kernel memory: 540k freed  [    2.171967] Write protecting the kernel text: 4568k  [    2.172053] Write protecting the kernel read-only data: 1836k  [    2.318779] Linux agpgart interface v0.103  [    2.351521] agpgart-intel 0000:00:00.0: Intel 965GM Chipset  [    2.351885] agpgart-intel 0000:00:00.0: detected 7676K stolen memory  [    2.355353] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000  [    2.394047] usb 3-1: new full speed USB device using uhci_hcd and address 2  [    2.402825] ohci1394 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  [    2.411021] tg3.c:v3.99 (April 20, 2009)  [    2.411050] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  [    2.411065] tg3 0000:09:00.0: setting latency timer to 64  [    2.417371] tg3 0000:09:00.0: PME# disabled  [    2.452679] [drm] Initialized drm 1.1.0 20060810  [    2.457335] Initializing USB Mass Storage driver...  [    2.461129] scsi3 : SCSI emulation for USB Mass Storage devices  [    2.461276] usbcore: registered new interface driver usb-storage  [    2.461280] USB Mass Storage support registered.  [    2.461287] usb-storage: device found at 3  [    2.461289] usb-storage: waiting for device to settle before scanning  [    2.463463] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f68ff800-f68fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]  [    2.473026] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  [    2.473033] i915 0000:00:02.0: setting latency timer to 64  [    2.476047]   alloc irq_desc for 29 on node -1  [    2.476051]   alloc kstat_irqs on node -1  [    2.476061] i915 0000:00:02.0: irq 29 for MSI/MSI-X  [    2.641477] usb 3-1: configuration #1 chosen from 1 choice  [    2.643446] hub 3-1:1.0: USB hub found  [    2.645385] hub 3-1:1.0: 3 ports detected  [    2.926386] usb 3-1.1: new full speed USB device using uhci_hcd and address 3  [    2.953563] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:21:70:71:55:25  [    2.953567] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])  [    2.953571] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]  [    2.953573] eth0: dma_rwctrl[76180000] dma_mask[64-bit]  [    3.046468] usb 3-1.1: configuration #1 chosen from 1 choice  [    3.054010] usbcore: registered new interface driver hiddev  [    3.056663] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5  [    3.056737] generic-usb 0003:413C:8157.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0  [    3.056754] usbcore: registered new interface driver usbhid  [    3.056757] usbhid: v2.6:USB HID core driver  [    3.073356] [drm] fb0: inteldrmfb frame buffer device  [    3.074167] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/input/input6  [    3.074207] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)  [    3.074269] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434  [    3.074350] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/input/input7  [    3.074381] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)  [    3.074409] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0  [    3.381580] [drm] LVDS-8: set mode 1440x900 c  [    3.478392] usb 3-1.2: new full speed USB device using uhci_hcd and address 4  [    3.602484] usb 3-1.2: configuration #1 chosen from 1 choice  [    3.609752] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input8  [    3.609845] generic-usb 0003:413C:8158.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0  [    3.749138] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[7f4fc0008e739ce3]  [    4.019530] Console: switching to colour frame buffer device 180x56  [    4.353940] PM: Starting manual resume from disk  [    4.353945] PM: Resume from partition 8:5  [    4.353948] PM: Checking hibernation image.  [    4.354205] PM: Resume from disk failed.  [    4.407221] EXT4-fs (sda1): barriers enabled  [    4.437001] kjournald2 starting: pid 415, dev sda1:8, commit interval 5 seconds  [    4.437032] EXT4-fs (sda1): delayed allocation enabled  [    4.437036] EXT4-fs: file extents enabled  [    4.458279] EXT4-fs: mballoc enabled  [    4.458297] EXT4-fs (sda1): mounted filesystem with ordered data mode  [    5.320803] type=1505 audit(1260834896.720:2): operation="profile_load" pid=438 name=/usr/share/gdm/guest-session/Xsession  [    5.324176] type=1505 audit(1260834896.724:3): operation="profile_load" pid=439 name=/sbin/dhclient3  [    5.324965] type=1505 audit(1260834896.724:4): operation="profile_load" pid=439 name=/usr/lib/NetworkManager/nm-dhcp-client.action  [    5.325406] type=1505 audit(1260834896.728:5): operation="profile_load" pid=439 name=/usr/lib/connman/scripts/dhclient-script  [    5.378185] type=1505 audit(1260834896.779:6): operation="profile_load" pid=440 name=/usr/bin/evince  [    5.391032] type=1505 audit(1260834896.792:7): operation="profile_load" pid=440 name=/usr/bin/evince-previewer  [    5.398610] type=1505 audit(1260834896.800:8): operation="profile_load" pid=440 name=/usr/bin/evince-thumbnailer  [    5.420598] type=1505 audit(1260834896.820:9): operation="profile_load" pid=442 name=/usr/lib/cups/backend/cups-pdf  [    5.421533] type=1505 audit(1260834896.824:10): operation="profile_load" pid=442 name=/usr/sbin/cupsd  [    6.679748] Adding 6016300k swap on /dev/sda5.  Priority:-1 extents:1 across:6016300k  [    7.044086] EXT4-fs (sda1): internal journal on sda1:8  [    7.461423] usb-storage: device scan complete  [    7.462183] scsi 3:0:0:0: Direct-Access     IC35L040 AVVN07-0         AF1A PQ: 0 ANSI: 2 CCS  [    7.462637] sd 3:0:0:0: Attached scsi generic sg2 type 0  [    7.463413] sd 3:0:0:0: [sdb] 78156288 512-byte logical blocks: (40.0 GB/37.2 GiB)  [    7.464173] sd 3:0:0:0: [sdb] Write Protect is off  [    7.464176] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00  [    7.464179] sd 3:0:0:0: [sdb] Assuming drive cache: write through  [    7.465671] sd 3:0:0:0: [sdb] Assuming drive cache: write through  [    7.465676]  sdb: sdb1  [    7.482781] sd 3:0:0:0: [sdb] Assuming drive cache: write through  [    7.482786] sd 3:0:0:0: [sdb] Attached SCSI disk  [    7.661306] udev: starting version 147  [    8.649404] usb 3-1.3: new full speed USB device using uhci_hcd and address 5  [    8.782515] usb 3-1.3: configuration #1 chosen from 1 choice  [    8.960997] Bluetooth: Generic Bluetooth USB driver ver 0.5  [    8.961141] usbcore: registered new interface driver btusb  [    9.001410] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)  [    9.168252] ip_tables: (C) 2000-2006 Netfilter Core Team  [    9.218255] lp: driver loaded but no devices found  [    9.271938] input: Dell WMI hotkeys as /devices/virtual/input/input9  [    9.334405] lib80211: common routines for IEEE802.11 drivers  [    9.334408] lib80211_crypt: registered algorithm 'NULL'  [    9.535275] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10  [    9.552520] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11  [   10.021695] wl: module license 'MIXED/Proprietary' taints kernel.  [   10.021700] Disabling lock debugging due to kernel taint  [   10.024037] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  [   10.024053] wl 0000:0c:00.0: setting latency timer to 64  [   10.025638] sdhci: Secure Digital Host Controller Interface driver  [   10.025641] sdhci: Copyright(c) Pierre Ossman  [   10.056201] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)  [   10.056221]   alloc irq_desc for 18 on node -1  [   10.056223]   alloc kstat_irqs on node -1  [   10.056231] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18  [   10.058298] Registered led device: mmc0::  [   10.059331] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA  [   10.067463] lib80211_crypt: registered algorithm 'TKIP'  [   10.067855] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9  [   10.074866] udev: renamed network interface eth1 to eth2  [   10.223350] __ratelimit: 3 callbacks suppressed  [   10.223354] type=1505 audit(1260834901.624:12): operation="profile_replace" pid=821 name=/usr/share/gdm/guest-session/Xsession  [   10.225583] type=1505 audit(1260834901.628:13): operation="profile_replace" pid=822 name=/sbin/dhclient3  [   10.226375] type=1505 audit(1260834901.628:14): operation="profile_replace" pid=822 name=/usr/lib/NetworkManager/nm-dhcp-client.action  [   10.226806] type=1505 audit(1260834901.628:15): operation="profile_replace" pid=822 name=/usr/lib/connman/scripts/dhclient-script  [   10.232011] type=1505 audit(1260834901.632:16): operation="profile_replace" pid=823 name=/usr/bin/evince  [   10.244981] type=1505 audit(1260834901.644:17): operation="profile_replace" pid=823 name=/usr/bin/evince-previewer  [   10.252673] type=1505 audit(1260834901.652:18): operation="profile_replace" pid=823 name=/usr/bin/evince-thumbnailer  [   10.263350] type=1505 audit(1260834901.664:19): operation="profile_replace" pid=825 name=/usr/lib/cups/backend/cups-pdf  [   10.264314] type=1505 audit(1260834901.664:20): operation="profile_replace" pid=825 name=/usr/sbin/cupsd  [   10.267398] type=1505 audit(1260834901.668:21): operation="profile_replace" pid=826 name=/usr/sbin/tcpdump  [   10.271152] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21  [   10.271195] HDA Intel 0000:00:1b.0: setting latency timer to 64  [   10.365908] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12  [   10.881444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  [   10.881448] Bluetooth: BNEP filters: protocol multicast  [   11.050946] Bridge firewalling registered  [   11.516011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x001f1500  [   11.525443] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13  [   11.525541] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14  [   11.525610] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15  [   13.963532] tg3 0000:09:00.0: PME# disabled  [   13.963905]   alloc irq_desc for 30 on node -1  [   13.963907]   alloc kstat_irqs on node -1  [   13.963932] tg3 0000:09:00.0: irq 30 for MSI/MSI-X  [   14.102948] ADDRCONF(NETDEV_UP): eth0: link is not ready  [   16.000987] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x413C pid 0x5302  [   16.001073] usbcore: registered new interface driver usblp  [   16.032461] Linux video capture interface: v2.00  [   16.103549] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a1)  [   16.105054] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input16  [   16.105124] usbcore: registered new interface driver uvcvideo  [   16.105128] USB Video Class driver (v0.1.0)  [   17.296361] ppdev: user-space parallel port driver  [   19.563534] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1  [   24.372033] eth2: no IPv6 routers present  [  302.536566] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1  [  325.576071] eth2: no IPv6 routers present  [  391.212125] CE: hpet increasing min_delta_ns to 15000 nsec  [  890.164129] CE: hpet increasing min_delta_ns to 22500 nsec  [ 7049.349984] usb 2-1: USB disconnect, address 2  [ 7049.350221] usblp0: removed  [ 7050.435757] usb 2-2: USB disconnect, address 3  [ 7552.303778] tg3: eth0: Link is up at 100 Mbps, full duplex.  [ 7552.303786] tg3: eth0: Flow control is off for TX and off for RX.  [ 7552.304244] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  [ 7562.312074] eth0: no IPv6 routers present  [ 7758.554570] tg3: eth0: Link is down.  [ 8118.347601] tg3: eth0: Link is up at 100 Mbps, full duplex.  [ 8118.347605] tg3: eth0: Flow control is off for TX and off for RX.  [ 8611.985960] tg3: eth0: Link is down.  [ 9835.171591] tg3: eth0: Link is up at 100 Mbps, full duplex.  [ 9835.171599] tg3: eth0: Flow control is off for TX and off for RX.  [10068.223872] tg3: eth0: Link is down.  [11912.772072] eth2: no IPv6 routers present  [14042.591089] tg3: eth0: Link is up at 100 Mbps, full duplex.  [14042.591093] tg3: eth0: Flow control is off for TX and off for RX.  [15275.793226] wl 0000:0c:00.0: PCI INT A disabled  [16536.802822] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  [16536.802842] wl 0000:0c:00.0: setting latency timer to 64  [16536.820255] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9  [16536.856982] udev: renamed network interface eth1 to eth2  [16547.793036] eth2: no IPv6 routers present  [16562.149920] tg3: eth0: Link is down.  [16756.573028] eth2: no IPv6 routers present  [16815.430362] tg3: eth0: Link is up at 100 Mbps, full duplex.  [16815.430365] tg3: eth0: Flow control is off for TX and off for RX.  [18799.581132] tg3: eth0: Link is down.  [18868.462005] tg3: eth0: Link is up at 100 Mbps, full duplex.  [18868.462010] tg3: eth0: Flow control is off for TX and off for RX.  [19330.264437] tg3: eth0: Link is down.  [19951.061576] tg3: eth0: Link is up at 100 Mbps, full duplex.  [19951.061580] tg3: eth0: Flow control is off for TX and off for RX.  [20179.778765] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled  [20179.792240] SGI XFS Quota Management subsystem  [20179.817788] JFS: nTxBlock = 8192, nTxLock = 65536  [20179.912248] NTFS driver 2.1.29 [Flags: R/O MODULE].  [20179.990662] QNX4 filesystem 0.2.3 registered.  [20186.495471] tg3: eth0: Link is down.  [20327.543154] tg3: eth0: Link is up at 100 Mbps, full duplex.  [20327.543158] tg3: eth0: Flow control is off for TX and off for RX.  [20958.894854] tg3: eth0: Link is down.  

**6 ) Network configuration**
  Code:
 $ sudo lshw -C network  *-network                       description: Wireless interface         product: BCM4312 802.11b/g         vendor: Broadcom Corporation         physical id: 0         bus info: pci@0000:0c:00.0         logical name: eth2         version: 01         serial: 00:22:5f:06:e9:7b         width: 64 bits         clock: 33MHz         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless         configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bg         resources: irq:17 memory:f6cfc000-f6cfffff    *-network         description: Ethernet interface         product: NetLink BCM5784M Gigabit Ethernet PCIe         vendor: Broadcom Corporation         physical id: 0         bus info: pci@0000:09:00.0         logical name: eth0         version: 10         serial: 00:21:70:71:55:25         size: 100MB/s         capacity: 1GB/s         width: 64 bits         clock: 33MHz         capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation         configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s         resources: irq:30 memory:f69f0000-f69fffff  

  **7 )**
 $ iwlist scan lo        Interface doesn't support scanning.   eth0      Interface doesn't support scanning.   pan0      Interface doesn't support scanning.   eth2      Interface doesn't support scanning.  

  **8 ) ** 
 $ lsb_release -d Description:    Ubuntu 9.10  **9 ) ** 
 $ uname -mr 2.6.31-16-generic i686 **10 )**
 $ sudo /etc/init.d/networking restart * Reconfiguring network interfaces...                                                                                                                                           Ignoring unknown interface eth2=eth2.

---

### Post by bkratz on 2009-12-15
It is really hard to read the layout of the posting, but see if this helps.

[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)

---

### Post by Maxximiliann on 2009-12-15
My apologies:

1 ) Machine Brand and Model (PC/Laptop):
Dell Studio 1735 Laptop

2 ) $ lspci
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 004: ID 05ca:18a1 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 



3 ) $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:71:55:25  
          inet6 addr: fe80::221:70ff:fe71:5525/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:14234 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12922 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:14606625 (14.6 MB)  TX bytes:1788337 (1.7 MB) 
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:22:5f:06:e9:7b  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::222:5fff:fe06:e97b/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:8364 errors:0 dropped:0 overruns:0 frame:233207 
          TX packets:967 errors:34 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:633985 (633.9 KB)  TX bytes:67095 (67.0 KB) 
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1545 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1545 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:147925 (147.9 KB)  TX bytes:147925 (147.9 KB) 

$ iwconfig
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

eth2      IEEE 802.11  Nickname:"" 
          Access Point: Not-Associated   

4 ) $ lsmod
ufs                    75524  0 
qnx4                    8576  0 
hfsplus                73568  0 
hfs                    43232  0 
minix                  27588  0 
ntfs                   98240  0 
vfat                   10716  0 
msdos                   7836  0 
fat                    51452  2 vfat,msdos 
jfs                   177380  0 
xfs                   512064  0 
exportfs                4412  1 xfs 
reiserfs              229288  0 
wl                   1276032  0 
michael_mic             2204  8 
arc4                    1660  4 
ecb                     2524  4 
binfmt_misc             8356  1 
ppdev                   6688  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo 
v4l1_compat            14496  2 uvcvideo,videodev 
usblp                  12636  0 
bridge                 47952  0 
stp                     2272  1 bridge 
bnep                   12060  2 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               7200  1 snd_hda_codec 
lib80211_crypt_tkip     8636  0 
sdhci_pci               7100  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
sdhci                  17472  1 sdhci_pci 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
joydev                 10272  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              22276  2 snd_pcm,snd_seq 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7264  1 snd 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm 
lib80211                6432  2 wl,lib80211_crypt_tkip 
led_class               4096  1 sdhci 
dell_wmi                2564  0 
iptable_filter          3100  0 
dell_laptop             8128  0 
psmouse                56500  0 
lp                      8964  0 
ip_tables              11692  1 iptable_filter 
parport                35340  2 ppdev,lp 
dcdbas                  7292  1 dell_laptop 
serio_raw               5280  0 
btusb                  11856  2 
x_tables               16544  1 ip_tables 
fbcon                  36640  72 
tileblit                2460  1 fbcon 
font                    8124  1 fbcon 
bitblit                 5372  1 fbcon 
softcursor              1756  1 bitblit 
usbhid                 38208  0 
i915                  221064  3 
usb_storage            52576  0 
drm                   159584  3 i915 
i2c_algo_bit            5760  1 i915 
tg3                   109600  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394 
video                  19380  1 i915 
output                  2780  1 video 
intel_agp              27484  2 i915 
agpgart                34988  2 drm,intel_agp

5 )$ dmesg
[    0.372136] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling 
[    0.372237] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling 
[    0.372241] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling 
[    0.372244] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling 
[    0.372248] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling 
[    0.394561] pnp: PnP ACPI: found 13 devices 
[    0.394564] ACPI: ACPI bus type pnp unregistered 
[    0.394568] PnPBIOS: Disabled by ACPI PNP 
[    0.394583] system 00:06: ioport range 0xc80-0xcff could not be reserved 
[    0.394592] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved 
[    0.394598] system 00:0a: ioport range 0x900-0x97f has been reserved 
[    0.394601] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved 
[    0.394608] system 00:0b: ioport range 0xf400-0xf4fe has been reserved 
[    0.394611] system 00:0b: ioport range 0x1080-0x10bf has been reserved 
[    0.394614] system 00:0b: ioport range 0x10c0-0x10df has been reserved 
[    0.394617] system 00:0b: ioport range 0x809-0x809 has been reserved 
[    0.394624] system 00:0c: iomem range 0x0-0x9efff could not be reserved 
[    0.394627] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved 
[    0.394630] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved 
[    0.394633] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved 
[    0.394637] system 00:0c: iomem range 0x100000-0x7f65c7ff could not be reserved 
[    0.394640] system 00:0c: iomem range 0x7f65c800-0x7f6fffff has been reserved 
[    0.394643] system 00:0c: iomem range 0x7f700000-0x7f7fffff has been reserved 
[    0.394646] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved 
[    0.394649] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved 
[    0.394653] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved 
[    0.394656] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved 
[    0.394659] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved 
[    0.394662] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved 
[    0.394666] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved 
[    0.394669] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved 
[    0.394672] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved 
[    0.394676] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved 
[    0.394679] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved 
[    0.429378] AppArmor: AppArmor Filesystem Enabled 
[    0.429461] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b 
[    0.429463] pci 0000:00:1c.0:   IO window: disabled 
[    0.429470] pci 0000:00:1c.0:   MEM window: disabled 
[    0.429475] pci 0000:00:1c.0:   PREFETCH window: disabled 
[    0.429481] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c 
[    0.429484] pci 0000:00:1c.1:   IO window: disabled 
[    0.429491] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff 
[    0.429497] pci 0000:00:1c.1:   PREFETCH window: disabled 
[    0.429503] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d 
[    0.429507] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff 
[    0.429514] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6bfffff 
[    0.429521] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff 
[    0.429530] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09 
[    0.429532] pci 0000:00:1c.5:   IO window: disabled 
[    0.429539] pci 0000:00:1c.5:   MEM window: 0xf6900000-0xf69fffff 
[    0.429545] pci 0000:00:1c.5:   PREFETCH window: disabled 
[    0.429551] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03 
[    0.429553] pci 0000:00:1e.0:   IO window: disabled 
[    0.429560] pci 0000:00:1e.0:   MEM window: 0xf6800000-0xf68fffff 
[    0.429566] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.429584]   alloc irq_desc for 16 on node -1 
[    0.429586]   alloc kstat_irqs on node -1 
[    0.429593] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.429600] pci 0000:00:1c.0: setting latency timer to 64 
[    0.429610]   alloc irq_desc for 17 on node -1 
[    0.429612]   alloc kstat_irqs on node -1 
[    0.429616] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.429622] pci 0000:00:1c.1: setting latency timer to 64 
[    0.429635]   alloc irq_desc for 19 on node -1 
[    0.429636]   alloc kstat_irqs on node -1 
[    0.429640] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    0.429646] pci 0000:00:1c.3: setting latency timer to 64 
[    0.429656] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.429662] pci 0000:00:1c.5: setting latency timer to 64 
[    0.429672] pci 0000:00:1e.0: setting latency timer to 64 
[    0.429677] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.429680] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff] 
[    0.429683] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff] 
[    0.429686] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff] 
[    0.429688] pci_bus 0000:0d: resource 1 mem: [0xf6a00000-0xf6bfffff] 
[    0.429691] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff] 
[    0.429694] pci_bus 0000:09: resource 1 mem: [0xf6900000-0xf69fffff] 
[    0.429697] pci_bus 0000:03: resource 1 mem: [0xf6800000-0xf68fffff] 
[    0.429699] pci_bus 0000:03: resource 3 io:  [0x00-0xffff] 
[    0.429702] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff] 
[    0.429743] NET: Registered protocol family 2 
[    0.429851] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.430207] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.430733] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.431090] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.431093] TCP reno registered 
[    0.431216] NET: Registered protocol family 1 
[    0.431303] Trying to unpack rootfs image as initramfs... 
[    0.501513] Switched to high resolution mode on CPU 1 
[    0.503992] Switched to high resolution mode on CPU 0 
[    0.635216] Freeing initrd memory: 7465k freed 
[    0.640626] Simple Boot Flag at 0x79 set to 0x1 
[    0.640827] cpufreq-nforce2: No nForce2 chipset. 
[    0.640858] Scanning for low memory corruption every 60 seconds 
[    0.640975] audit: initializing netlink socket (disabled) 
[    0.640995] type=2000 audit(1260834890.640:1): initialized 
[    0.650214] highmem bounce pool size: 64 pages 
[    0.650220] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    0.651806] VFS: Disk quotas dquot_6.5.2 
[    0.651876] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    0.652467] fuse init (API version 7.12) 
[    0.652557] msgmni has been set to 1706 
[    0.652782] alg: No test for stdrng (krng) 
[    0.652798] io scheduler noop registered 
[    0.652800] io scheduler anticipatory registered 
[    0.652802] io scheduler deadline registered 
[    0.652847] io scheduler cfq registered (default) 
[    0.652862] pci 0000:00:02.0: Boot video device 
[    0.653183]   alloc irq_desc for 24 on node -1 
[    0.653186]   alloc kstat_irqs on node -1 
[    0.653200] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X 
[    0.653214] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[    0.653399]   alloc irq_desc for 25 on node -1 
[    0.653401]   alloc kstat_irqs on node -1 
[    0.653411] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X 
[    0.653424] pcieport-driver 0000:00:1c.1: setting latency timer to 64 
[    0.653602]   alloc irq_desc for 26 on node -1 
[    0.653604]   alloc kstat_irqs on node -1 
[    0.653614] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X 
[    0.653626] pcieport-driver 0000:00:1c.3: setting latency timer to 64 
[    0.653807]   alloc irq_desc for 27 on node -1 
[    0.653809]   alloc kstat_irqs on node -1 
[    0.653819] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X 
[    0.653832] pcieport-driver 0000:00:1c.5: setting latency timer to 64 
[    0.653950] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.654078] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.654252] ACPI: AC Adapter [AC] (on-line) 
[    0.654334] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0 
[    0.658852] ACPI: Lid Switch [LID] 
[    0.658903] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1 
[    0.658910] ACPI: Power Button [PBTN] 
[    0.658957] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2 
[    0.658960] ACPI: Sleep Button [SBTN] 
[    0.659668] ACPI: SSDT 7f65d4f6 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624) 
[    0.660215] ACPI: SSDT 7f65ce8c 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624) 
[    0.660609] Monitor-Mwait will be used to enter C-1 state 
[    0.660638] Monitor-Mwait will be used to enter C-2 state 
[    0.660663] Monitor-Mwait will be used to enter C-3 state 
[    0.660671] Marking TSC unstable due to TSC halts in idle 
[    0.660693] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[    0.660721] processor LNXCPU:00: registered as cooling_device0 
[    0.660725] ACPI: Processor [CPU0] (supports 8 throttling states) 
[    0.661092] ACPI: SSDT 7f65d77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624) 
[    0.661429] ACPI: SSDT 7f65d471 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624) 
[    0.661935] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3]) 
[    0.661962] processor LNXCPU:01: registered as cooling_device1 
[    0.661967] ACPI: Processor [CPU1] (supports 8 throttling states) 
[    0.674972] thermal LNXTHERM:01: registered as thermal_zone0 
[    0.674981] ACPI: Thermal Zone [THM] (60 C) 
[    0.675056] isapnp: Scanning for PnP cards... 
[    0.756701] ACPI: Battery Slot [BAT0] (battery present) 
[    1.031939] isapnp: No Plug & Play device found 
[    1.033160] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    1.034614] brd: module loaded 
[    1.035094] loop: module loaded 
[    1.035172] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[    1.035261] ahci 0000:00:1f.2: version 3.0 
[    1.035279] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    1.035320]   alloc irq_desc for 28 on node -1 
[    1.035323]   alloc kstat_irqs on node -1 
[    1.035337] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X 
[    1.035419] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode 
[    1.035423] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    1.035429] ahci 0000:00:1f.2: setting latency timer to 64 
[    1.048099] scsi0 : ahci 
[    1.048216] scsi1 : ahci 
[    1.048282] scsi2 : ahci 
[    1.048529] ata1: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 28 
[    1.048534] ata2: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb980 irq 28 
[    1.048538] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 28 
[    1.049581] Fixed MDIO Bus: probed 
[    1.049621] PPP generic driver version 2.4.2 
[    1.049736] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    1.049760]   alloc irq_desc for 22 on node -1 
[    1.049763]   alloc kstat_irqs on node -1 
[    1.049769] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[    1.049787] ehci_hcd 0000:00:1a.7: setting latency timer to 64 
[    1.049791] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
[    1.049845] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1 
[    1.053764] ehci_hcd 0000:00:1a.7: debug port 1 
[    1.053772] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported 
[    1.053810] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400 
[    1.068019] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00 
[    1.068109] usb usb1: configuration #1 chosen from 1 choice 
[    1.068140] hub 1-0:1.0: USB hub found 
[    1.068149] hub 1-0:1.0: 4 ports detected 
[    1.068213]   alloc irq_desc for 20 on node -1 
[    1.068215]   alloc kstat_irqs on node -1 
[    1.068220] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    1.068233] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    1.068237] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    1.068271] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2 
[    1.072191] ehci_hcd 0000:00:1d.7: debug port 1 
[    1.072199] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    1.072213] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000 
[    1.084019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    1.084087] usb usb2: configuration #1 chosen from 1 choice 
[    1.084116] hub 2-0:1.0: USB hub found 
[    1.084122] hub 2-0:1.0: 6 ports detected 
[    1.084194] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    1.084214] uhci_hcd: USB Universal Host Controller Interface driver 
[    1.084248] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    1.084257] uhci_hcd 0000:00:1a.0: setting latency timer to 64 
[    1.084260] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
[    1.084301] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3 
[    1.084331] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60 
[    1.084416] usb usb3: configuration #1 chosen from 1 choice 
[    1.084443] hub 3-0:1.0: USB hub found 
[    1.084450] hub 3-0:1.0: 2 ports detected 
[    1.084506]   alloc irq_desc for 21 on node -1 
[    1.084508]   alloc kstat_irqs on node -1 
[    1.084514] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    1.084521] uhci_hcd 0000:00:1a.1: setting latency timer to 64 
[    1.084525] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
[    1.084556] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4 
[    1.084594] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80 
[    1.084677] usb usb4: configuration #1 chosen from 1 choice 
[    1.084707] hub 4-0:1.0: USB hub found 
[    1.084714] hub 4-0:1.0: 2 ports detected 
[    1.084767] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    1.084775] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    1.084779] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    1.084811] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5 
[    1.084841] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00 
[    1.084924] usb usb5: configuration #1 chosen from 1 choice 
[    1.084955] hub 5-0:1.0: USB hub found 
[    1.084962] hub 5-0:1.0: 2 ports detected 
[    1.085025] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    1.085032] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    1.085036] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    1.085067] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6 
[    1.085098] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20 
[    1.085188] usb usb6: configuration #1 chosen from 1 choice 
[    1.085215] hub 6-0:1.0: USB hub found 
[    1.085222] hub 6-0:1.0: 2 ports detected 
[    1.085273] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[    1.085280] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    1.085284] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    1.085318] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7 
[    1.085347] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40 
[    1.085441] usb usb7: configuration #1 chosen from 1 choice 
[    1.085470] hub 7-0:1.0: USB hub found 
[    1.085477] hub 7-0:1.0: 2 ports detected 
[    1.085595] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    1.092811] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    1.092818] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    1.092895] mice: PS/2 mouse device common for all mice 
[    1.093025] rtc_cmos 00:04: RTC can wake from S4 
[    1.093062] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0 
[    1.093097] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs 
[    1.093214] device-mapper: uevent: version 1.0.3 
[    1.093309] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL] 
[    1.093375] device-mapper: multipath: version 1.1.0 loaded 
[    1.093378] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    1.093512] EISA: Probing bus 0 at eisa.0 
[    1.093520] Cannot allocate resource for EISA slot 1 
[    1.093552] EISA: Detected 0 cards. 
[    1.093702] cpuidle: using governor ladder 
[    1.093832] cpuidle: using governor menu 
[    1.094382] TCP cubic registered 
[    1.094546] NET: Registered protocol family 10 
[    1.095053] lo: Disabled Privacy Extensions 
[    1.095411] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    1.095429] NET: Registered protocol family 17 
[    1.095453] Bluetooth: L2CAP ver 2.13 
[    1.095455] Bluetooth: L2CAP socket layer initialized 
[    1.095462] Bluetooth: SCO (Voice Link) ver 0.6 
[    1.095463] Bluetooth: SCO socket layer initialized 
[    1.095494] Bluetooth: RFCOMM TTY layer initialized 
[    1.095497] Bluetooth: RFCOMM socket layer initialized 
[    1.095499] Bluetooth: RFCOMM ver 1.11 
[    1.096154] Using IPI No-Shortcut mode 
[    1.096220] PM: Resume from disk failed. 
[    1.096234] registered taskstats version 1 
[    1.096372]   Magic number: 5:421:959 
[    1.096483] rtc_cmos 00:04: setting system clock to 2009-12-14 23:54:52 UTC (1260834892) 
[    1.096486] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.096488] EDD information not available. 
[    1.368080] ata3: SATA link down (SStatus 0 SControl 300) 
[    1.372081] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.372119] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.373911] ata1.00: ATA-8: ST9250320AS, DE04, max UDMA/133 
[    1.373914] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32) 
[    1.376111] ata1.00: configured for UDMA/133 
[    1.384890] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, D300, max UDMA/100 
[    1.384905] ata2.00: applying bridge limits 
[    1.392247] scsi 0:0:0:0: Direct-Access     ATA      ST9250320AS      DE04 PQ: 0 ANSI: 5 
[    1.392383] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    1.392423] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB) 
[    1.392472] sd 0:0:0:0: [sda] Write Protect is off 
[    1.392476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.392501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.392634]  sda: 
[    1.398760] ata2.00: configured for UDMA/100 
[    1.404003]  sda1 sda2 < 
[    1.412070] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4 
[    1.412073] ata2: irq_stat 0x40000001 
[    1.412078] ata2: hard resetting link 
[    1.450293]  sda5 > 
[    1.450582] sd 0:0:0:0: [sda] Attached SCSI disk 
[    1.492080] usb 2-1: new high speed USB device using ehci_hcd and address 2 
[    1.500040] Clocksource tsc unstable (delta = -305294766 ns) 
[    1.625595] usb 2-1: configuration #1 chosen from 1 choice 
[    1.736066] usb 2-2: new high speed USB device using ehci_hcd and address 3 
[    1.869828] usb 2-2: configuration #1 chosen from 1 choice 
[    1.980074] usb 2-5: new high speed USB device using ehci_hcd and address 4 
[    2.119329] usb 2-5: configuration #1 chosen from 1 choice 
[    2.136077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    2.162821] ata2.00: configured for UDMA/100 
[    2.163571] ata2: EH complete 
[    2.164837] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D300 PQ: 0 ANSI: 5 
[    2.171392] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray 
[    2.171396] Uniform CD-ROM driver Revision: 3.20 
[    2.171486] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    2.171535] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[    2.171579] Freeing unused kernel memory: 540k freed 
[    2.171967] Write protecting the kernel text: 4568k 
[    2.172053] Write protecting the kernel read-only data: 1836k 
[    2.318779] Linux agpgart interface v0.103 
[    2.351521] agpgart-intel 0000:00:00.0: Intel 965GM Chipset 
[    2.351885] agpgart-intel 0000:00:00.0: detected 7676K stolen memory 
[    2.355353] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000 
[    2.394047] usb 3-1: new full speed USB device using uhci_hcd and address 2 
[    2.402825] ohci1394 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    2.411021] tg3.c:v3.99 (April 20, 2009) 
[    2.411050] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    2.411065] tg3 0000:09:00.0: setting latency timer to 64 
[    2.417371] tg3 0000:09:00.0: PME# disabled 
[    2.452679] [drm] Initialized drm 1.1.0 20060810 
[    2.457335] Initializing USB Mass Storage driver... 
[    2.461129] scsi3 : SCSI emulation for USB Mass Storage devices 
[    2.461276] usbcore: registered new interface driver usb-storage 
[    2.461280] USB Mass Storage support registered. 
[    2.461287] usb-storage: device found at 3 
[    2.461289] usb-storage: waiting for device to settle before scanning 
[    2.463463] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f68ff800-f68fffff]  Max Packet=[2048]  IR/IT contexts=[4/4] 
[    2.473026] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    2.473033] i915 0000:00:02.0: setting latency timer to 64 
[    2.476047]   alloc irq_desc for 29 on node -1 
[    2.476051]   alloc kstat_irqs on node -1 
[    2.476061] i915 0000:00:02.0: irq 29 for MSI/MSI-X 
[    2.641477] usb 3-1: configuration #1 chosen from 1 choice 
[    2.643446] hub 3-1:1.0: USB hub found 
[    2.645385] hub 3-1:1.0: 3 ports detected 
[    2.926386] usb 3-1.1: new full speed USB device using uhci_hcd and address 3 
[    2.953563] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:21:70:71:55:25 
[    2.953567] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1]) 
[    2.953571] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1] 
[    2.953573] eth0: dma_rwctrl[76180000] dma_mask[64-bit] 
[    3.046468] usb 3-1.1: configuration #1 chosen from 1 choice 
[    3.054010] usbcore: registered new interface driver hiddev 
[    3.056663] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5 
[    3.056737] generic-usb 0003:413C:8157.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0 
[    3.056754] usbcore: registered new interface driver usbhid 
[    3.056757] usbhid: v2.6:USB HID core driver 
[    3.073356] [drm] fb0: inteldrmfb frame buffer device 
[    3.074167] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/input/input6 
[    3.074207] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no) 
[    3.074269] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434 
[    3.074350] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/input/input7 
[    3.074381] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no) 
[    3.074409] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[    3.381580] [drm] LVDS-8: set mode 1440x900 c 
[    3.478392] usb 3-1.2: new full speed USB device using uhci_hcd and address 4 
[    3.602484] usb 3-1.2: configuration #1 chosen from 1 choice 
[    3.609752] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input8 
[    3.609845] generic-usb 0003:413C:8158.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0 
[    3.749138] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[7f4fc0008e739ce3] 
[    4.019530] Console: switching to colour frame buffer device 180x56 
[    4.353940] PM: Starting manual resume from disk 
[    4.353945] PM: Resume from partition 8:5 
[    4.353948] PM: Checking hibernation image. 
[    4.354205] PM: Resume from disk failed. 
[    4.407221] EXT4-fs (sda1): barriers enabled 
[    4.437001] kjournald2 starting: pid 415, dev sda1:8, commit interval 5 seconds 
[    4.437032] EXT4-fs (sda1): delayed allocation enabled 
[    4.437036] EXT4-fs: file extents enabled 
[    4.458279] EXT4-fs: mballoc enabled 
[    4.458297] EXT4-fs (sda1): mounted filesystem with ordered data mode 
[    5.320803] type=1505 audit(1260834896.720:2): operation="profile_load" pid=438 name=/usr/share/gdm/guest-session/Xsession 
[    5.324176] type=1505 audit(1260834896.724:3): operation="profile_load" pid=439 name=/sbin/dhclient3 
[    5.324965] type=1505 audit(1260834896.724:4): operation="profile_load" pid=439 name=/usr/lib/NetworkManager/nm-dhcp-client.action 
[    5.325406] type=1505 audit(1260834896.728:5): operation="profile_load" pid=439 name=/usr/lib/connman/scripts/dhclient-script 
[    5.378185] type=1505 audit(1260834896.779:6): operation="profile_load" pid=440 name=/usr/bin/evince 
[    5.391032] type=1505 audit(1260834896.792:7): operation="profile_load" pid=440 name=/usr/bin/evince-previewer 
[    5.398610] type=1505 audit(1260834896.800:8): operation="profile_load" pid=440 name=/usr/bin/evince-thumbnailer 
[    5.420598] type=1505 audit(1260834896.820:9): operation="profile_load" pid=442 name=/usr/lib/cups/backend/cups-pdf 
[    5.421533] type=1505 audit(1260834896.824:10): operation="profile_load" pid=442 name=/usr/sbin/cupsd 
[    6.679748] Adding 6016300k swap on /dev/sda5.  Priority:-1 extents:1 across:6016300k 
[    7.044086] EXT4-fs (sda1): internal journal on sda1:8 
[    7.461423] usb-storage: device scan complete 
[    7.462183] scsi 3:0:0:0: Direct-Access     IC35L040 AVVN07-0         AF1A PQ: 0 ANSI: 2 CCS 
[    7.462637] sd 3:0:0:0: Attached scsi generic sg2 type 0 
[    7.463413] sd 3:0:0:0: [sdb] 78156288 512-byte logical blocks: (40.0 GB/37.2 GiB) 
[    7.464173] sd 3:0:0:0: [sdb] Write Protect is off 
[    7.464176] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00 
[    7.464179] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
[    7.465671] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
[    7.465676]  sdb: sdb1 
[    7.482781] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
[    7.482786] sd 3:0:0:0: [sdb] Attached SCSI disk 
[    7.661306] udev: starting version 147 
[    8.649404] usb 3-1.3: new full speed USB device using uhci_hcd and address 5 
[    8.782515] usb 3-1.3: configuration #1 chosen from 1 choice 
[    8.960997] Bluetooth: Generic Bluetooth USB driver ver 0.5 
[    8.961141] usbcore: registered new interface driver btusb 
[    9.001410] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
[    9.168252] ip_tables: (C) 2000-2006 Netfilter Core Team 
[    9.218255] lp: driver loaded but no devices found 
[    9.271938] input: Dell WMI hotkeys as /devices/virtual/input/input9 
[    9.334405] lib80211: common routines for IEEE802.11 drivers 
[    9.334408] lib80211_crypt: registered algorithm 'NULL' 
[    9.535275] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10 
[    9.552520] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11 
[   10.021695] wl: module license 'MIXED/Proprietary' taints kernel. 
[   10.021700] Disabling lock debugging due to kernel taint 
[   10.024037] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   10.024053] wl 0000:0c:00.0: setting latency timer to 64 
[   10.025638] sdhci: Secure Digital Host Controller Interface driver 
[   10.025641] sdhci: Copyright(c) Pierre Ossman 
[   10.056201] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22) 
[   10.056221]   alloc irq_desc for 18 on node -1 
[   10.056223]   alloc kstat_irqs on node -1 
[   10.056231] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
[   10.058298] Registered led device: mmc0:: 
[   10.059331] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA 
[   10.067463] lib80211_crypt: registered algorithm 'TKIP' 
[   10.067855] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9 
[   10.074866] udev: renamed network interface eth1 to eth2 
[   10.223350] __ratelimit: 3 callbacks suppressed 
[   10.223354] type=1505 audit(1260834901.624:12): operation="profile_replace" pid=821 name=/usr/share/gdm/guest-session/Xsession 
[   10.225583] type=1505 audit(1260834901.628:13): operation="profile_replace" pid=822 name=/sbin/dhclient3 
[   10.226375] type=1505 audit(1260834901.628:14): operation="profile_replace" pid=822 name=/usr/lib/NetworkManager/nm-dhcp-client.action 
[   10.226806] type=1505 audit(1260834901.628:15): operation="profile_replace" pid=822 name=/usr/lib/connman/scripts/dhclient-script 
[   10.232011] type=1505 audit(1260834901.632:16): operation="profile_replace" pid=823 name=/usr/bin/evince 
[   10.244981] type=1505 audit(1260834901.644:17): operation="profile_replace" pid=823 name=/usr/bin/evince-previewer 
[   10.252673] type=1505 audit(1260834901.652:18): operation="profile_replace" pid=823 name=/usr/bin/evince-thumbnailer 
[   10.263350] type=1505 audit(1260834901.664:19): operation="profile_replace" pid=825 name=/usr/lib/cups/backend/cups-pdf 
[   10.264314] type=1505 audit(1260834901.664:20): operation="profile_replace" pid=825 name=/usr/sbin/cupsd 
[   10.267398] type=1505 audit(1260834901.668:21): operation="profile_replace" pid=826 name=/usr/sbin/tcpdump 
[   10.271152] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[   10.271195] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   10.365908] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12 
[   10.881444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   10.881448] Bluetooth: BNEP filters: protocol multicast 
[   11.050946] Bridge firewalling registered 
[   11.516011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x001f1500 
[   11.525443] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13 
[   11.525541] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14 
[   11.525610] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15 
[   13.963532] tg3 0000:09:00.0: PME# disabled 
[   13.963905]   alloc irq_desc for 30 on node -1 
[   13.963907]   alloc kstat_irqs on node -1 
[   13.963932] tg3 0000:09:00.0: irq 30 for MSI/MSI-X 
[   14.102948] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   16.000987] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x413C pid 0x5302 
[   16.001073] usbcore: registered new interface driver usblp 
[   16.032461] Linux video capture interface: v2.00 
[   16.103549] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a1) 
[   16.105054] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input16 
[   16.105124] usbcore: registered new interface driver uvcvideo 
[   16.105128] USB Video Class driver (v0.1.0) 
[   17.296361] ppdev: user-space parallel port driver 
[   19.563534] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1 
[   24.372033] eth2: no IPv6 routers present 
[  302.536566] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1 
[  325.576071] eth2: no IPv6 routers present 
[  391.212125] CE: hpet increasing min_delta_ns to 15000 nsec 
[  890.164129] CE: hpet increasing min_delta_ns to 22500 nsec 
[ 7049.349984] usb 2-1: USB disconnect, address 2 
[ 7049.350221] usblp0: removed 
[ 7050.435757] usb 2-2: USB disconnect, address 3 
[ 7552.303778] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[ 7552.303786] tg3: eth0: Flow control is off for TX and off for RX. 
[ 7552.304244] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[ 7562.312074] eth0: no IPv6 routers present 
[ 7758.554570] tg3: eth0: Link is down. 
[ 8118.347601] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[ 8118.347605] tg3: eth0: Flow control is off for TX and off for RX. 
[ 8611.985960] tg3: eth0: Link is down. 
[ 9835.171591] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[ 9835.171599] tg3: eth0: Flow control is off for TX and off for RX. 
[10068.223872] tg3: eth0: Link is down. 
[11912.772072] eth2: no IPv6 routers present 
[14042.591089] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[14042.591093] tg3: eth0: Flow control is off for TX and off for RX. 
[15275.793226] wl 0000:0c:00.0: PCI INT A disabled 
[16536.802822] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[16536.802842] wl 0000:0c:00.0: setting latency timer to 64 
[16536.820255] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9 
[16536.856982] udev: renamed network interface eth1 to eth2 
[16547.793036] eth2: no IPv6 routers present 
[16562.149920] tg3: eth0: Link is down. 
[16756.573028] eth2: no IPv6 routers present 
[16815.430362] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[16815.430365] tg3: eth0: Flow control is off for TX and off for RX. 
[18799.581132] tg3: eth0: Link is down. 
[18868.462005] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[18868.462010] tg3: eth0: Flow control is off for TX and off for RX. 
[19330.264437] tg3: eth0: Link is down. 
[19951.061576] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[19951.061580] tg3: eth0: Flow control is off for TX and off for RX. 
[20179.778765] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled 
[20179.792240] SGI XFS Quota Management subsystem 
[20179.817788] JFS: nTxBlock = 8192, nTxLock = 65536 
[20179.912248] NTFS driver 2.1.29 [Flags: R/O MODULE]. 
[20179.990662] QNX4 filesystem 0.2.3 registered. 
[20186.495471] tg3: eth0: Link is down. 
[20327.543154] tg3: eth0: Link is up at 100 Mbps, full duplex. 
[20327.543158] tg3: eth0: Flow control is off for TX and off for RX. 
[20958.894854] tg3: eth0: Link is down. 


6 ) $ sudo lshw -C network
 *-network               
       description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth2 
       version: 01 
       serial: 00:22:5f:06:e9:7b 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:17 memory:f6cfc000-f6cfffff 
  *-network 
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:21:70:71:55:25 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s 
       resources: irq:30 memory:f69f0000-f69fffff 

7 ) $ iwlist scan
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

pan0      Interface doesn't support scanning. 

eth2      Interface doesn't support scanning. 

8 ) $ lsb_release -d
Description:    Ubuntu 9.10 

9 ) $ uname -mr
2.6.31-16-generic i686

10) $ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...                                                                                                                                           Ignoring unknown interface eth2=eth2.

---

### Post by go2dell on 2010-03-01
Did you ever get this working?

If not, you need to install the package b43-fwcutter.  It rarely works graphically for me, so use apt-get or aptitude at the command line to install it.  The package will automatically download and install the firmware you need to get your Broadcom wireless working.

You should try a few speed tests after installing the firmware, because some people have Broadcom implementations that are distressingly slow.  For instance, with the kernel firmware installed, my Internet connection is much faster than my wireless.  Switching to ndiswrapper and using the manufacturer's Windows driver solved the problem... although it's still not as fast as advertised -- but at least it matches the speed under MS.

To install ndiswrapper, first install package *ndiswrapper-utils-1.9* (which will pull in other packages you need).  Then add your card's driver by using *ndiswrapper -i*.

Now you need to blacklist the b43 kernel modules so that they won't load.  Create a file */etc/modprobe.d/blacklist-b43.conf*(using sudo):
```
blacklist b43
blacklist b43legacy
blacklist ssb
```

This file will ensure the kernel modules don't load at boot, because they will grab control before ndiswrapper gets a chance to take over.

Now make sure that ndiswrapper gets loaded on boot by editing */etc/modules* and adding at the bottom of that file:
```
ndiswrapper
```

Now the very final step:  you need to recreate your initramfs because ssb will be loaded by it.  The previous step blacklisting ssb will be noticed when you regenerate initramfs, and the change will be included.
```
sudo update-initramfs -k all -u
```

This will update every initramfs on your system, including those for older kernel revisions.

Now reboot and you're done.  You can leave the b43 firmware as is; you don't even need to uninstall b43-fwcutter.

To undo these changes, just
[LIST=1]
[*]delete blacklist-b43.conf
[*]remove ndiswrapper from /etc/modules
[*]regenerate initramfs
[*]reboot
[/LIST]

---

