---
title: "Compaq Presario CQ60-417DX / Atheros AR5001"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by groggin on 2013-03-05
helloo good ppl, sorry to bother y'all w/such a common problem, but i've been trying for days ;)

    (pls note: upon fresh install, (Vista wireless working) wireless not working in ubuntu. i mucked about for a bit and got it working! but then i proceeded to download some 800+ updates, plus a new kernel, thereafter i am unable to connect. also, i've re-installed, cannot reproduce what i did, and will have to update again)

  
Operating system: ArtistX 1.0 r2 (ubuntu 10.4 LTS) dual booting w/ms Vista
                                 (don't want to upgrade because subsequent releases use gnome3)

machine make and model: **Compaq Presario CQ60-417DX Notebook PC**


**2 ) Wireless Brand, Model and Wireless Chipset:**

      ```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

 $ lspci -nn | grep 'Wireless Brand'
$: command not found

```

**3 ) check interface:**

       ```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:de:81:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162679 (162.6 KB)  TX bytes:162679 (162.6 KB)
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ iwconfig wlan0
wlan0     No such device
```


**4 ) Check for modules**

     ```
  $ lsmod
Module                  Size  Used by
udf                    78785  1 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_conexant    22641  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sbp2                   19448  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee1394               81181  1 sbp2
joydev                  8740  0 
psmouse                63245  0 
serio_raw               3978  0 
snd                    54180  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           184677  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287458  2 
drm_kms_helper         29329  1 i915
usbhid                 36110  0 
hid                    67064  1 usbhid
drm                   162409  3 i915,drm_kms_helper
intel_agp              24375  2 i915
ahci                   32200  7 
r8169                  34108  0 
mii                     4381  1 r8169
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap

(input:lsmod | grep "wlan_module_name"-->yeilds0results)
```
[B]
5 ) Kernel boot messages[/B]

```
[    0.174055]   alloc kstat_irqs on node -1
[    0.174058] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.174062] pci 0000:00:1c.1: setting latency timer to 64
[    0.174071] pci 0000:00:1e.0: setting latency timer to 64
[    0.174075] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.174077] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.174079] pci_bus 0000:01: resource 0 io:  [0x3000-0x4fff]
[    0.174081] pci_bus 0000:01: resource 1 mem: [0xd3700000-0xd46fffff]
[    0.174084] pci_bus 0000:01: resource 2 pref mem [0xd0400000-0xd14fffff]
[    0.174086] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.174088] pci_bus 0000:02: resource 1 mem: [0xd2600000-0xd36fffff]
[    0.174090] pci_bus 0000:02: resource 2 pref mem [0xd1500000-0xd24fffff]
[    0.174093] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.174095] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.174123] NET: Registered protocol family 2
[    0.174205] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.174459] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.174841] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.175094] TCP: Hash tables configured (established 131072 bind 65536)
[    0.175096] TCP reno registered
[    0.175194] NET: Registered protocol family 1
[    0.175213] pci 0000:00:02.0: Boot video device
[    0.175637] Simple Boot Flag value 0x89 read from CMOS RAM was invalid
[    0.175639] Simple Boot Flag at 0x44 set to 0x1
[    0.175738] cpufreq-nforce2: No nForce2 chipset.
[    0.175763] Scanning for low memory corruption every 60 seconds
[    0.175853] audit: initializing netlink socket (disabled)
[    0.175863] type=2000 audit(1362468234.171:1): initialized
[    0.184906] Trying to unpack rootfs image as initramfs...
[    0.196283] highmem bounce pool size: 64 pages
[    0.196288] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.197512] VFS: Disk quotas dquot_6.5.2
[    0.197558] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.204314] fuse init (API version 7.13)
[    0.204410] msgmni has been set to 1655
[    0.204600] alg: No test for stdrng (krng)
[    0.204645] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.204648] io scheduler noop registered
[    0.204650] io scheduler anticipatory registered
[    0.204652] io scheduler deadline registered
[    0.204687] io scheduler cfq registered (default)
[    0.204827]   alloc irq_desc for 24 on node -1
[    0.204829]   alloc kstat_irqs on node -1
[    0.204840] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.204851] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.204995]   alloc irq_desc for 25 on node -1
[    0.204997]   alloc kstat_irqs on node -1
[    0.205005] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.205015] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.205101] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.205457] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 2940 ss_vid 0 ss_did 0
[    0.205495] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.205517] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 2942 ss_vid 0 ss_did 0
[    0.205548] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.205555] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.207165] ACPI: AC Adapter [ADP1] (on-line)
[    0.207224] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.208958] ACPI: Lid Switch [LID0]
[    0.209003] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.209010] ACPI: Sleep Button [SLPB]
[    0.209052] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.209054] ACPI: Power Button [PWRF]
[    0.215973] Monitor-Mwait will be used to enter C-1 state
[    0.216021] Monitor-Mwait will be used to enter C-2 state
[    0.216027] Marking TSC unstable due to TSC halts in idle
[    0.216088] processor LNXCPU:00: registered as cooling_device0
[    0.217818] Switching to clocksource hpet
[    0.235433] thermal LNXTHERM:01: registered as thermal_zone0
[    0.235443] ACPI: Thermal Zone [TZS0] (76 C)
[    0.242154] thermal LNXTHERM:02: registered as thermal_zone1
[    0.242163] ACPI: Thermal Zone [TZS1] (76 C)
[    0.243465] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.244566] brd: module loaded
[    0.244926] loop: module loaded
[    0.244994] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.245326] Fixed MDIO Bus: probed
[    0.245355] PPP generic driver version 2.4.2
[    0.245383] tun: Universal TUN/TAP device driver, 1.6
[    0.245385] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.245444] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.245465]   alloc irq_desc for 18 on node -1
[    0.245469]   alloc kstat_irqs on node -1
[    0.245476] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[    0.245490] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.245493] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.245522] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.245549] ehci_hcd 0000:00:1a.7: debug port 1
[    0.249434] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.252398] isapnp: Scanning for PnP cards...
[    0.260228] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd4705c00
[    0.320144] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.320243] usb usb1: configuration #1 chosen from 1 choice
[    0.320267] hub 1-0:1.0: USB hub found
[    0.320276] hub 1-0:1.0: 6 ports detected
[    0.320336] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.320354] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.320358] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.320390] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.320417] ehci_hcd 0000:00:1d.7: debug port 1
[    0.324295] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.328276] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd4705800
[    0.348266] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.348387] usb usb2: configuration #1 chosen from 1 choice
[    0.348411] hub 2-0:1.0: USB hub found
[    0.348419] hub 2-0:1.0: 6 ports detected
[    0.348475] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.348489] uhci_hcd: USB Universal Host Controller Interface driver
[    0.348529] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.348538] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.348541] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.348573] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.348600] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000050e0
[    0.348671] usb usb3: configuration #1 chosen from 1 choice
[    0.348690] hub 3-0:1.0: USB hub found
[    0.348696] hub 3-0:1.0: 2 ports detected
[    0.348736]   alloc irq_desc for 19 on node -1
[    0.348737]   alloc kstat_irqs on node -1
[    0.348743] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.348749] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.348753] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.348778] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.348812] uhci_hcd 0000:00:1a.1: irq 19, io base 0x000050c0
[    0.348884] usb usb4: configuration #1 chosen from 1 choice
[    0.348903] hub 4-0:1.0: USB hub found
[    0.348909] hub 4-0:1.0: 2 ports detected
[    0.348947]   alloc irq_desc for 17 on node -1
[    0.348949]   alloc kstat_irqs on node -1
[    0.348952] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.348958] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.348961] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.348986] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.349019] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000050a0
[    0.349088] usb usb5: configuration #1 chosen from 1 choice
[    0.349108] hub 5-0:1.0: USB hub found
[    0.349114] hub 5-0:1.0: 2 ports detected
[    0.349154] uhci_hcd 0000:00:1d.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.349160] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.349163] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.349188] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.349213] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00005080
[    0.349288] usb usb6: configuration #1 chosen from 1 choice
[    0.349308] hub 6-0:1.0: USB hub found
[    0.349313] hub 6-0:1.0: 2 ports detected
[    0.349351] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.349357] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.349360] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.349389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.349413] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060
[    0.349480] usb usb7: configuration #1 chosen from 1 choice
[    0.349501] hub 7-0:1.0: USB hub found
[    0.349508] hub 7-0:1.0: 2 ports detected
[    0.349543] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 17 (level, low) -> IRQ 17
[    0.349548] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.349552] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.349575] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.349600] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00005040
[    0.349667] usb usb8: configuration #1 chosen from 1 choice
[    0.349689] hub 8-0:1.0: USB hub found
[    0.349694] hub 8-0:1.0: 2 ports detected
[    0.349768] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.368699] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.448299] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.448306] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.448342] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.448363] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.448380] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.448491] mice: PS/2 mouse device common for all mice
[    0.448778] rtc_cmos 00:03: RTC can wake from S4
[    0.448812] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.448842] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.448941] device-mapper: uevent: version 1.0.3
[    0.449030] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.452296] device-mapper: multipath: version 1.1.0 loaded
[    0.452299] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.452450] EISA: Probing bus 0 at eisa.0
[    0.452461] Cannot allocate resource for EISA slot 2
[    0.452462] Cannot allocate resource for EISA slot 3
[    0.452464] Cannot allocate resource for EISA slot 4
[    0.452465] Cannot allocate resource for EISA slot 5
[    0.452479] EISA: Detected 0 cards.
[    0.454667] cpuidle: using governor ladder
[    0.454703] cpuidle: using governor menu
[    0.455016] TCP cubic registered
[    0.455140] NET: Registered protocol family 10
[    0.455498] lo: Disabled Privacy Extensions
[    0.455736] NET: Registered protocol family 17
[    0.455781] Using IPI No-Shortcut mode
[    0.455855] PM: Resume from disk failed.
[    0.455869] registered taskstats version 1
[    0.456349]   Magic number: 5:917:368
[    0.456430] rtc_cmos 00:03: setting system clock to 2013-03-05 07:23:54 UTC (1362468234)
[    0.456432] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.456434] EDD information not available.
[    0.472596] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.767817] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    0.873841] Freeing initrd memory: 13197k freed
[    0.967187] isapnp: No Plug & Play device found
[    0.967207] Freeing unused kernel memory: 660k freed
[    0.967584] Write protecting the kernel text: 4688k
[    0.967606] Write protecting the kernel read-only data: 1844k
[    0.980407] usb 2-3: configuration #1 chosen from 1 choice
[    0.980473] hub 2-3:1.0: USB hub found
[    0.980577] hub 2-3:1.0: 4 ports detected
[    0.986915] ramzswap: disk size set to 1513832 kB
[    0.993454] udev: starting version 151
[    1.037187] Adding 1513828k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1513828k SS
[    1.186200] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.186221]   alloc irq_desc for 16 on node -1
[    1.186223]   alloc kstat_irqs on node -1
[    1.186229] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.186271] r8169 0000:01:00.0: setting latency timer to 64
[    1.186325]   alloc irq_desc for 26 on node -1
[    1.186327]   alloc kstat_irqs on node -1
[    1.186340] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
[    1.186819] eth0: RTL8102e at 0xf848c000, 00:1f:16:de:81:de, XID 14a00000 IRQ 26
[    1.193000] Linux agpgart interface v0.103
[    1.193077] ahci 0000:00:1f.2: version 3.0
[    1.193091]   alloc irq_desc for 23 on node -1
[    1.193093]   alloc kstat_irqs on node -1
[    1.193098] ahci 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    1.193135]   alloc irq_desc for 27 on node -1
[    1.193137]   alloc kstat_irqs on node -1
[    1.193145] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.193193] ahci: SSS flag set, parallel bus scan disabled
[    1.193231] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.193234] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems sxs 
[    1.193240] ahci 0000:00:1f.2: setting latency timer to 64
[    1.216138] scsi0 : ahci
[    1.216285] scsi1 : ahci
[    1.216369] scsi2 : ahci
[    1.216452] scsi3 : ahci
[    1.216538] scsi4 : ahci
[    1.216619] scsi5 : ahci
[    1.216872] ata1: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705100 irq 27
[    1.216875] ata2: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705180 irq 27
[    1.216877] ata3: DUMMY
[    1.216879] ata4: DUMMY
[    1.216881] ata5: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705300 irq 27
[    1.216885] ata6: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705380 irq 27
[    1.217043] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    1.217341] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    1.243615] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.301592] [drm] Initialized drm 1.1.0 20060810
[    1.384033] usb 8-1: new full speed USB device using uhci_hcd and address 2
[    1.563720] usb 8-1: configuration #1 chosen from 1 choice
[    1.580163] usbcore: registered new interface driver hiddev
[    1.581887] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input5
[    1.582053] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1/input0
[    1.586765] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input6
[    1.587037] generic-usb 0003:046D:C52F.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1/input1
[    1.587059] usbcore: registered new interface driver usbhid
[    1.587133] usbhid: v2.6:USB HID core driver
[    1.656096] usb 2-3.1: new full speed USB device using ehci_hcd and address 4
[    1.724039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.725319] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.725506] ata1.00: ATA-8: Hitachi HTS545016B9A300, PBBOCA0G, max UDMA/100
[    1.725509] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.726917] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.727123] ata1.00: configured for UDMA/100
[    1.740174] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54501 PBBO PQ: 0 ANSI: 5
[    1.740338] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.740561] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.740599] sd 0:0:0:0: [sda] Write Protect is off
[    1.740602] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.740622] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.740801]  sda: sda1 sda2 sda3 <
[    1.767152] usb 2-3.1: configuration #1 chosen from 1 choice
[    1.768989] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1:1.0/input/input7
[    1.769080] generic-usb 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-3.1/input0
[    1.771877] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1:1.1/input/input8
[    1.772050] generic-usb 0003:046D:C52B.0004: input,hiddev97,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.1/input1
[    1.775038] generic-usb 0003:046D:C52B.0005: hiddev98,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.1/input2
[    1.781948]  sda5 sda6 sda7 sda8 sda9 >
[    1.829126] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.628036] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.633060] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.633065] ata2.00: ATAPI: HL-DT-ST DVDRAM GT20L, DC03, max UDMA/100
[    2.638891] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.638915] ata2.00: configured for UDMA/100
[    2.659281] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20L     DC03 PQ: 0 ANSI: 5
[    2.662967] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.662970] Uniform CD-ROM driver Revision: 3.20
[    2.663051] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.663100] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.980039] ata5: SATA link down (SStatus 0 SControl 300)
[    3.316041] ata6: SATA link down (SStatus 0 SControl 300)
[    3.363117] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.363122] i915 0000:00:02.0: setting latency timer to 64
[    3.368727]   alloc irq_desc for 28 on node -1
[    3.368730]   alloc kstat_irqs on node -1
[    3.368738] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    3.368744] [drm] set up 63M of stolen space
[    4.369751] fb0: inteldrmfb frame buffer device
[    4.369753] registered panic notifier
[    4.385613] acpi device:02: registered as cooling_device1
[    4.386070] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    4.386149] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    4.386259] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.390051] vga16fb: initializing
[    4.390055] vga16fb: mapped to 0xc00a0000
[    4.390060] vga16fb: not registering due to another framebuffer present
[    4.556054] Console: switching to colour frame buffer device 170x48
[    6.378502] EXT4-fs (sda9): mounted filesystem with ordered data mode
[   10.573812] ACPI: Battery Slot [BAT0] (battery present)
[   18.454039] Adding 6144820k swap on /dev/sda5.  Priority:-1 extents:1 across:6144820k 
[   18.522322] udev: starting version 151
[   18.833289] Disabling lock debugging due to kernel taint
[   18.924771] lp: driver loaded but no devices found
[   19.053868] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   19.641857] type=1505 audit(1362486253.683:2):  operation="profile_load" pid=1194 name="/sbin/dhclient3"
[   19.642511] type=1505 audit(1362486253.683:3):  operation="profile_load" pid=1194 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.642872] type=1505 audit(1362486253.683:4):  operation="profile_load" pid=1194 name="/usr/lib/connman/scripts/dhclient-script"
[   19.650956] type=1505 audit(1362486253.691:5):  operation="profile_load" pid=1216 name="/usr/sbin/ntpd"
[   19.687759] usbcore: registered new interface driver ndiswrapper
[   19.953672]   alloc irq_desc for 22 on node -1
[   19.953675]   alloc kstat_irqs on node -1
[   19.953681] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.953720] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.075220] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.075439] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   20.075630] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   20.341669] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000
[   20.403209] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input13
[   20.486910] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   21.794282] type=1505 audit(1362486255.835:6):  operation="profile_load" pid=1531 name="/usr/share/gdm/guest-session/Xsession"
[   21.803826] type=1505 audit(1362486255.843:7):  operation="profile_replace" pid=1534 name="/sbin/dhclient3"
[   21.807358] type=1505 audit(1362486255.847:8):  operation="profile_replace" pid=1534 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.807729] type=1505 audit(1362486255.847:9):  operation="profile_replace" pid=1534 name="/usr/lib/connman/scripts/dhclient-script"
[   21.843678] type=1505 audit(1362486255.883:10):  operation="profile_load" pid=1543 name="/usr/bin/evince"
[   21.909449] type=1505 audit(1362486255.951:11):  operation="profile_load" pid=1543 name="/usr/bin/evince-previewer"
[   21.917173] r8169: eth0: link down
[   21.917388] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.999508] ttyS0: LSR safety check engaged!
[   22.000738] ttyS0: LSR safety check engaged!
[   22.172553] apm: BIOS not found.
[   23.678526] ppdev: user-space parallel port driver
[  108.648583] ttyS0: LSR safety check engaged!
[  188.161506] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2013/03/03 11:18 (1ed4)
[  250.816038] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  250.816044] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 00 40 00 00 01 00
[  250.816055] ata2.00: cmd a0/01:00:00:00:08/00:00:00:00:00/a0 tag 0 dma 2048 out
[  250.816056]          res 40/00:03:00:00:01/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  250.816059] ata2.00: status: { DRDY }
[  250.816063] ata2: hard resetting link
[  251.300029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  251.304712] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[  251.310373] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[  251.310397] ata2.00: configured for UDMA/100
[  251.317501] ata2: EH complete
[  263.741740] sr 1:0:0:0: [sr0] Unhandled sense code
[  263.741743] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  263.741747] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  263.741751] sr 1:0:0:0: [sr0] Add. Sense: Write error
[  263.741756] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 00 40 00 00 01 00
[  263.741764] end_request: I/O error, dev sr0, sector 256
[  263.741769] __ratelimit: 24 callbacks suppressed
[  263.741772] Buffer I/O error on device sr0, logical block 64
[  263.741774] lost page write due to I/O error on sr0
[  263.747357] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  263.747361] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  263.747364] sr 1:0:0:0: [sr0] Add. Sense: Invalid address for write
[  263.747368] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 02 71 00 00 01 00
[  263.747375] end_request: I/O error, dev sr0, sector 2500
[  263.747377] Buffer I/O error on device sr0, logical block 625
[  263.747379] lost page write due to I/O error on sr0
[  335.178623] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  335.178628] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  335.178632] sr 1:0:0:0: [sr0] Add. Sense: Invalid address for write
[  335.178636] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 02 41 00 00 02 00
[  335.178644] end_request: I/O error, dev sr0, sector 2308
[  335.178649] Buffer I/O error on device sr0, logical block 577
[  335.178651] lost page write due to I/O error on sr0
[  335.178654] Buffer I/O error on device sr0, logical block 578
[  335.178656] lost page write due to I/O error on sr0
[  335.180930] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  335.180934] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  335.180937] sr 1:0:0:0: [sr0] Add. Sense: Invalid address for write
[  335.180942] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 02 84 00 00 02 00
[  335.180949] end_request: I/O error, dev sr0, sector 2576
[  335.180951] Buffer I/O error on device sr0, logical block 644
[  335.180953] lost page write due to I/O error on sr0
[  335.180955] Buffer I/O error on device sr0, logical block 645
[  335.180957] lost page write due to I/O error on sr0
[  335.183238] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  335.183241] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  335.183244] sr 1:0:0:0: [sr0] Add. Sense: Invalid address for write
[  335.183248] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 02 88 00 00 15 00
[  335.183254] end_request: I/O error, dev sr0, sector 2592
[  335.183256] Buffer I/O error on device sr0, logical block 648
[  335.183258] lost page write due to I/O error on sr0
[  335.183260] Buffer I/O error on device sr0, logical block 649
[  335.183261] lost page write due to I/O error on sr0
[  335.183264] Buffer I/O error on device sr0, logical block 650
[  335.183266] lost page write due to I/O error on sr0
[  335.183268] Buffer I/O error on device sr0, logical block 651
[  335.183270] lost page write due to I/O error on sr0
[  335.183272] Buffer I/O error on device sr0, logical block 652
[  335.183273] lost page write due to I/O error on sr0
[  335.183275] Buffer I/O error on device sr0, logical block 653
[  335.183277] lost page write due to I/O error on sr0
groggin@grogginNic:~$ 

```

[B]6 ) Network configuration
[/B]
```
$ sudo lshw -C network
[sudo] password for groggin: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:de:81:de
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:d2600000-d260ffff
```
[B]
7 ) Scan for networks:[/B]

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

**8 ) Ubuntu Version: **

```
$ lsb_release -d
Description:	Ubuntu 10.04.2 LTS

```

**9 ) Kernel/architecture (including 32 vs. 64 bit): **

```
$ uname -mr
2.6.32-28-generic i686

```

**10 ) Restarting the network:**
```

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                             
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

A big pre thankyou :popcorn:

---

### Post by groggin on 2013-03-06
*bump*
  someone?
from the looks of things, i might try starting over again  :icon_frown:

---

### Post by roadrash on 2013-03-06
For the time being until you find an answer, you can boot using the previous kernel.  You can do this by selecting the "Avanced Options" in the Grub boot menu screen.  This will have a list of all your kernels with the latest at the top so pick one below this.

---

### Post by chili555 on 2013-03-06
I doubt that ndiswrapper is best for your device. Let's try to fix it. First:> $ lspci -nn | grep 'Wireless Brand'What is meant here is to look for the brand of your wireless interface, in your case Atheros:> 02:00.0 Ethernet controller:[COLOR="#FF0000"] Atheros[/COLOR] Communications Inc. AR5001 [COLOR="#FF0000"]Wireless Network Adapter[/COLOR] (rev 01)So what we'd like to see is:```
lspci -nn | grep Atheros
```I am actually pretty sure the appropriate driver is ath5k. On a hunch, let's try it:```
sudo modprobe -r ndiswrapper
sudo modprobe ath5k
```Did your wireless come to life?```
iwconfig
```Any errors or warnings?```
dmesg | grep ath
```If that does it, we'll edit a couple of files and make it permanent.

---

### Post by groggin on 2013-03-06
@**roadrash**
doH! i should have thought of that.  ty

@**chili555's **

  > Did your wireless come to life?

  no but feels great to be movin' in the right direction for a change  :)

  > groggin@~~~~~:~$ lspci -nn | grep Atheros     
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
groggin@~~~~~:~$ sudo modprobe -r ndiswrapper      
[sudo] password for groggin: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
groggin@~~~~~:~$ sudo modprobe ath5k       
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
groggin@~~~~~:~$ iwconfig
lo        [COLOR="#FF0000"][B]no wireless extensions.
[/B][/COLOR]
eth0      [COLOR="#FF0000"][B]no wireless extensions.
[/B][/COLOR]
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
groggin@~~~~~:~$ dmesg | grep ath      
[    0.432339] device-mapper: multipath: version 1.1.0 loaded
[    0.432342] device-mapper: multipath round-robin: version 1.0.0 loaded
[  329.408455] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  329.408468] ath5k 0000:02:00.0: setting latency timer to 64
[  329.408602] ath5k 0000:02:00.0: registered as 'phy0'
[  329.914776] ath: EEPROM regdomain: 0x64
[  329.914779] ath: EEPROM indicates we should expect a direct regpair map
[  329.914783] ath: Country alpha2 being used: 00
[  329.914784] ath: Regpair used: 0x64
[  329.934728] Registered led device: ath5k-phy0::rx
[  329.934744] Registered led device: ath5k-phy0::tx
[  329.934747] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
groggin@~~~~~:~$ 

---

### Post by chili555 on 2013-03-06
Yes, it's an ath5k device. Let's keep digging:```
rfkill list all
```I suggest we wait until we get ath5k working before we remove ndiswrapper.

---

### Post by groggin on 2013-03-06
> **chili555 said:**
> Yes, it's an ath5k device. Let's keep digging:```
rfkill list all
```I suggest we wait until we get ath5k working before we remove ndiswrapper.

like that; i gather win drivers are 'limited'?

i'm re-typing this output, rather than copy-paste-save to flash, PnP, etc... :rolleyes:

~$ rfkill list all
0: phy0 wireless LAN
          soft blocked: no
          hard blocked: no
:KS

---

### Post by chili555 on 2013-03-06
Ndiswrapper is a pretty neat hack to use the Windows XP driver in Linux. It works pretty well but is generally inferior to a native Linux driver. As the years go by, we'll start to see newer devices released without those old-fashioned XP drivers. Ndiswrapper will have some work to do.

ath5k is usually pretty reliable. Let's dig a bit deeper:```
sudo iwlist wlan0 scan
```We don't need to see all the scan results, just 'yes, I see my network, woo hoo' or any messages if it won't scan. If it scans, we can probably connect and we'll remove ndiswrapper and reboot.> i'm re-typing this output, rather than copy-paste-save to flash, PnP, etc...Perfectly valid approach. Any way we can see the data is a good thing.

---

### Post by groggin on 2013-03-06
copy-paste

```
groggin@~~~~~:~$ sudo iwlist wlan0 scan       
[sudo] password for groggin: 
wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:FD:9F:3C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"7SIH7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c706e16a3f
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 00053753494837
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:18:01:F8:DA:51
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"W2AO4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c7073e6317
                    Extra: Last beacon: 512ms ago
                    IE: Unknown: 00055732414F34
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
```

---

### Post by chili555 on 2013-03-06
Alrighty then! Let me just remove my shiny scalpel from the autoclave. First, we need to verify that these results are generated by ath5k and not ndiswrapper:```
lsmod | grep -e ath5k -e ndis
```I hope we are seeing ath5k and not seeing ndiswrapper. If so, please proceed.```
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/blacklist
sudo rm -rf /etc/ndiswrapper/*
gksudo gedit /etc/modules
```If ndiswrapper is in the file, remove it. Add, at the end of the file:```
ath5k
```Proofread, save and close gedit. Reboot and let us have your report.

---

### Post by groggin on 2013-03-06
well **chili555** now you've done it...

    [SIZE=5]**[COLOR="#FF0000"]typing from my lappie[/COLOR]**[/SIZE]            **[SIZE=6][B][COLOR="#008000"]HOORAY[/COLOR]**[/SIZE][/B]!

if yer ever near boston, i'd like to buy yall a tall beer   :guitar:):P:popcorn:

thanks dude
~g

[edit]
now installing updates, hopefully i'll still be connected after the reboot. **chili**, did i remember something about making this change permanent?

---

### Post by chili555 on 2013-03-06
Awesome! Glad it's working! Please use thread tools at the top to mark Solved.

I do love a tall beer!

---

### Post by groggin on 2013-03-06
ummm - i want to install about 800 updates and a new kernel, but i remember something about permanence?

---

### Post by chili555 on 2013-03-06
> **groggin said:**
> ummm - i want to install about 800 updates and a new kernel, but i remember something about permanence?
Everything we did it permanent. Rock on!

---

### Post by groggin on 2013-03-06
right dude, thanks again  :KS

---

