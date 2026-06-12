---
title: "wifi not working dell inspiron n5010 and broadcom 4313"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by topbayder on 2010-12-24
ok basically i have a new dell inspiron n5010 with a broadcom 4313 wifi card. it doesnt work with ubuntu studio 10.10. I have the drivers all installed and it works on ethernet with the broadcom STA proprietry driver. if i disable this driver the eth doesnt work. but the driver shows its working (screenshot-1).

There is no pop up or anything in the task bar for detected wifi. i open the network settings and it shows up with a wifi option but i have to go into properties and manually type in what i have "the_den_meribel". which didn't work. (screenshot-2).

i have tried the other driver broadcom-sta-common and that doesnt make it work either. screenshot-3. i did try to install the "lp-pphhy" or whatever it is (seacrh for firmware-b43 in synaptic).

i have a list of results from what i have typed into the terminal:
dell inspiron n5010

```
sam@drytopubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

```
sam@drytopubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:b1:75:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 1c:65:9d:a1:9e:86  
          inet6 addr: fe80::1e65:9dff:fea1:9e86/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:608
          TX packets:72 errors:26 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8136 (8.1 KB)  TX bytes:10440 (10.4 KB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr f0:4d:a2:b1:75:3b  
          inet addr:169.254.7.160  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:44 Base address:0x4000 

eth1:avahi Link encap:Ethernet  HWaddr 1c:65:9d:a1:9e:86  
          inet addr:169.254.9.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2596 (2.5 KB)  TX bytes:2596 (2.5 KB)

```


sam@drytopubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:206  Noise level:164
          Rx invalid nwid:0  invalid crypt:190  invalid misc:0


```
sam@drytopubuntu:~$ lsmod
Module                  Size  Used by
sha256_generic         11267  2 
aes_i586                7280  61 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  1 
binfmt_misc             6599  1 
joydev                  8767  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7736  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
wl                   1959533  0 
dell_wmi                2852  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
dell_wmi_aio            1733  0 
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
lib80211                5058  2 lib80211_crypt_tkip,wl
intel_ips              11101  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
i915                  294989  8 
drm_kms_helper         30200  1 i915
drm                   168092  3 i915,drm_kms_helper
r8169                  36489  0 
mii                     4425  1 r8169
ahci                   19198  2 
intel_agp              26694  2 i915
libahci                21664  1 ahci
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp



it pref]
[    0.622221] pci 0000:00:1c.1: BAR 15: assigned [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.622224] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.622226] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.622228] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[    0.622232] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.622238] pci 0000:00:1c.0:   bridge window [mem 0xbc000000-0xbc1fffff]
[    0.622243] pci 0000:00:1c.0:   bridge window [mem 0xbc200000-0xbc3fffff 64bit pref]
[    0.622251] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[    0.622254] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.622260] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.622265] pci 0000:00:1c.1:   bridge window [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.622272] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[    0.622275] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.622281] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.622286] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.622293] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[    0.622296] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.622303] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.622307] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.622315] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    0.622316] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.622322] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.622326] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.622349]   alloc irq_desc for 17 on node -1
[    0.622351]   alloc kstat_irqs on node -1
[    0.622358] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.622363] pci 0000:00:1c.0: setting latency timer to 64
[    0.622374]   alloc irq_desc for 16 on node -1
[    0.622375]   alloc kstat_irqs on node -1
[    0.622378] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.622383] pci 0000:00:1c.1: setting latency timer to 64
[    0.622393]   alloc irq_desc for 18 on node -1
[    0.622395]   alloc kstat_irqs on node -1
[    0.622398] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.622402] pci 0000:00:1c.2: setting latency timer to 64
[    0.622413] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.622417] pci 0000:00:1c.4: setting latency timer to 64
[    0.622425] pci 0000:00:1e.0: setting latency timer to 64
[    0.622430] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.622431] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.622433] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.622435] pci_bus 0000:00: resource 7 [mem 0xbc000000-0xffffffff]
[    0.622437] pci_bus 0000:11: resource 0 [io  0x2000-0x2fff]
[    0.622439] pci_bus 0000:11: resource 1 [mem 0xbc000000-0xbc1fffff]
[    0.622441] pci_bus 0000:11: resource 2 [mem 0xbc200000-0xbc3fffff 64bit pref]
[    0.622443] pci_bus 0000:12: resource 0 [io  0x3000-0x3fff]
[    0.622445] pci_bus 0000:12: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.622447] pci_bus 0000:12: resource 2 [mem 0xbc400000-0xbc5fffff 64bit pref]
[    0.622450] pci_bus 0000:13: resource 0 [io  0xe000-0xefff]
[    0.622452] pci_bus 0000:13: resource 1 [mem 0xfb200000-0xfbbfffff]
[    0.622455] pci_bus 0000:13: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.622457] pci_bus 0000:15: resource 0 [io  0xd000-0xdfff]
[    0.622458] pci_bus 0000:15: resource 1 [mem 0xfa800000-0xfb1fffff]
[    0.622460] pci_bus 0000:15: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.622462] pci_bus 0000:20: resource 4 [io  0x0000-0x0cf7]
[    0.622464] pci_bus 0000:20: resource 5 [io  0x0d00-0xffff]
[    0.622466] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[    0.622467] pci_bus 0000:20: resource 7 [mem 0xbc000000-0xffffffff]
[    0.622502] NET: Registered protocol family 2
[    0.622557] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.622721] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.622995] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.623118] TCP: Hash tables configured (established 131072 bind 65536)
[    0.623120] TCP reno registered
[    0.623123] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.623130] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.623199] NET: Registered protocol family 1
[    0.623212] pci 0000:00:02.0: Boot video device
[    0.878190] PCI: CLS 64 bytes, default 64
[    0.878440] cpufreq-nforce2: No nForce2 chipset.
[    0.878462] Scanning for low memory corruption every 60 seconds
[    0.878575] audit: initializing netlink socket (disabled)
[    0.878586] type=2000 audit(1293231360.712:1): initialized
[    0.888584] highmem bounce pool size: 64 pages
[    0.888589] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.889735] VFS: Disk quotas dquot_6.5.2
[    0.889785] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.890255] fuse init (API version 7.14)
[    0.890325] msgmni has been set to 1650
[    0.890704] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.890707] io scheduler noop registered
[    0.890708] io scheduler deadline registered
[    0.890718] io scheduler cfq registered (default)
[    0.890804] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.890852]   alloc irq_desc for 40 on node -1
[    0.890853]   alloc kstat_irqs on node -1
[    0.890865] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.890948] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.890990]   alloc irq_desc for 41 on node -1
[    0.890991]   alloc kstat_irqs on node -1
[    0.890999] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.891081] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.891123]   alloc irq_desc for 42 on node -1
[    0.891124]   alloc kstat_irqs on node -1
[    0.891132] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.891210] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.891252]   alloc irq_desc for 43 on node -1
[    0.891253]   alloc kstat_irqs on node -1
[    0.891261] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.891349] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.891722] pciehp: Using ACPI for slot detection.
[    0.891903] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[    0.891941] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.891947] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.892010] intel_idle: MWAIT substates: 0x1120
[    0.892012] intel_idle: v0.4 model 0x25
[    0.892013] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.892134] ACPI: AC Adapter [AC] (off-line)
[    0.892189] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.892194] ACPI: Power Button [PWRB]
[    0.892226] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.893890] ACPI: Lid Switch [LID0]
[    0.893926] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.893929] ACPI: Sleep Button [SBTN]
[    0.893958] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.893961] ACPI: Power Button [PWRF]
[    0.894321] ACPI: acpi_idle yielding to intel_idle
[    0.909656] thermal LNXTHERM:01: registered as thermal_zone0
[    0.909665] ACPI: Thermal Zone [THM] (54 C)
[    0.909751] ERST: Table is not found!
[    0.909785] isapnp: Scanning for PnP cards...
[    0.910182] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.911840] brd: module loaded
[    0.912459] loop: module loaded
[    0.912989] Fixed MDIO Bus: probed
[    0.913027] PPP generic driver version 2.4.2
[    0.913065] tun: Universal TUN/TAP device driver, 1.6
[    0.913067] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.913147] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.913177] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913192] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.913197] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.913234] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.913264] ehci_hcd 0000:00:1a.0: debug port 2
[    0.917220] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.917243] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbd08000
[    0.930072] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.930211] hub 1-0:1.0: USB hub found
[    0.930218] hub 1-0:1.0: 2 ports detected
[    0.930337]   alloc irq_desc for 23 on node -1
[    0.930340]   alloc kstat_irqs on node -1
[    0.930348] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.930366] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.930373] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.930415] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.930445] ehci_hcd 0000:00:1d.0: debug port 2
[    0.934415] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.934434] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbd07000
[    0.938996] ACPI: Battery Slot [BAT0] (battery present)
[    0.950042] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.950181] hub 2-0:1.0: USB hub found
[    0.950188] hub 2-0:1.0: 2 ports detected
[    0.950260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.950276] uhci_hcd: USB Universal Host Controller Interface driver
[    0.950382] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    0.973367] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.973379] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.973477] mice: PS/2 mouse device common for all mice
[    0.973658] rtc_cmos 00:03: RTC can wake from S4
[    0.973705] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.973740] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.973879] device-mapper: uevent: version 1.0.3
[    0.974421] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.974517] device-mapper: multipath: version 1.1.1 loaded
[    0.974520] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.974653] EISA: Probing bus 0 at eisa.0
[    0.974656] EISA: Cannot allocate resource for mainboard
[    0.974659] Cannot allocate resource for EISA slot 1
[    0.974662] Cannot allocate resource for EISA slot 2
[    0.974664] Cannot allocate resource for EISA slot 3
[    0.974667] Cannot allocate resource for EISA slot 4
[    0.974669] Cannot allocate resource for EISA slot 5
[    0.974671] Cannot allocate resource for EISA slot 6
[    0.974674] Cannot allocate resource for EISA slot 7
[    0.974676] Cannot allocate resource for EISA slot 8
[    0.974678] EISA: Detected 0 cards.
[    0.974946] cpuidle: using governor ladder
[    0.975164] cpuidle: using governor menu
[    0.975516] TCP cubic registered
[    0.975675] NET: Registered protocol family 10
[    0.976081] lo: Disabled Privacy Extensions
[    0.976333] NET: Registered protocol family 17
[    0.978076] Using IPI No-Shortcut mode
[    0.978161] PM: Resume from disk failed.
[    0.978173] registered taskstats version 1
[    0.978597]   Magic number: 6:68:958
[    0.978635] mem oldmem: hash matches
[    0.978698] rtc_cmos 00:03: setting system clock to 2010-12-24 22:56:01 UTC (1293231361)
[    0.978702] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.978704] EDD information not available.
[    1.004235] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.139754] Freeing initrd memory: 15572k freed
[    1.241468] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.277671] isapnp: No Plug & Play device found
[    1.277689] Freeing unused kernel memory: 688k freed
[    1.277965] Write protecting the kernel text: 4932k
[    1.278001] Write protecting the kernel read-only data: 1980k
[    1.293865] udev[103]: starting version 163
[    1.325209] Linux agpgart interface v0.103
[    1.344032] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.345448] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    1.373925] hub 1-1:1.0: USB hub found
[    1.374008] hub 1-1:1.0: 6 ports detected
[    1.382395] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.382440] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.382541] r8169 0000:13:00.0: setting latency timer to 64
[    1.382697]   alloc irq_desc for 44 on node -1
[    1.382700]   alloc kstat_irqs on node -1
[    1.382754] r8169 0000:13:00.0: irq 44 for MSI/MSI-X
[    1.383326] r8169 0000:13:00.0: eth0: RTL8102e at 0xf8054000, f0:4d:a2:b1:75:3b, XID 04e00000 IRQ 44
[    1.415870] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.415891] ahci 0000:00:1f.2: version 3.0
[    1.415912]   alloc irq_desc for 19 on node -1
[    1.415915]   alloc kstat_irqs on node -1
[    1.415923] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.415961]   alloc irq_desc for 45 on node -1
[    1.415963]   alloc kstat_irqs on node -1
[    1.415973] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.416061] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.416066] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.416072] ahci 0000:00:1f.2: setting latency timer to 64
[    1.432478] scsi0 : ahci
[    1.432640] scsi1 : ahci
[    1.432714] scsi2 : ahci
[    1.432802] scsi3 : ahci
[    1.432878] scsi4 : ahci
[    1.432943] scsi5 : ahci
[    1.433118] ata1: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06100 irq 45
[    1.433122] ata2: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06180 irq 45
[    1.433123] ata3: DUMMY
[    1.433124] ata4: DUMMY
[    1.433127] ata5: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06300 irq 45
[    1.433128] ata6: DUMMY
[    1.441329] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.464468] [drm] Initialized drm 1.1.0 20060810
[    1.572367] hub 2-1:1.0: USB hub found
[    1.572450] hub 2-1:1.0: 8 ports detected
[    1.643670] usb 1-1.6: new high speed USB device using ehci_hcd and address 3
[    1.751356] ata5: SATA link down (SStatus 0 SControl 300)
[    1.751364] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.751396] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.752697] ata1.00: ATA-8: WDC WD3200BEVT-75A23T0, 01.01A01, max UDMA/133
[    1.752702] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.754243] ata1.00: configured for UDMA/133
[    1.754380] ata2.00: ATAPI: PLDS DVD+/-RW DS-8A5SH, XD12, max UDMA/100
[    1.755758] ata2.00: configured for UDMA/100
[    1.767448] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-7 01.0 PQ: 0 ANSI: 5
[    1.767602] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.767606] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.767673] sd 0:0:0:0: [sda] Write Protect is off
[    1.767676] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.767692] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.767801]  sda:
[    1.775883] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A5SH XD12 PQ: 0 ANSI: 5
[    1.785711] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.785716] Uniform CD-ROM driver Revision: 3.20
[    1.785854] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.785916] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.799559]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.836530] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.847808] usb 2-1.6: new full speed USB device using ehci_hcd and address 3
[    1.857013] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.857017] i915 0000:00:02.0: setting latency timer to 64
[    1.875730] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[    1.875733] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    1.875956]   alloc irq_desc for 46 on node -1
[    1.875961]   alloc kstat_irqs on node -1
[    1.875975] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    1.875989] [drm] set up 31M of stolen space
[    1.945278] hub 2-1.6:1.0: USB hub found
[    1.945485] hub 2-1.6:1.0: 3 ports detected
[    1.992678] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.222714] usb 2-1.6.1: new full speed USB device using ehci_hcd and address 4
[    2.332005] usbcore: registered new interface driver hiddev
[    2.333422] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input5
[    2.333519] generic-usb 0003:413C:8161.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[    2.333536] usbcore: registered new interface driver usbhid
[    2.333538] usbhid: USB HID core driver
[    2.361797] Skipping EDID probe due to cached edid
[    2.390497] usb 2-1.6.2: new full speed USB device using ehci_hcd and address 5
[    2.488341] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input6
[    2.488430] generic-usb 0003:413C:8162.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[    2.876193] Console: switching to colour frame buffer device 170x48
[    2.879694] fb0: inteldrmfb frame buffer device
[    2.879696] drm: registered panic notifier
[    2.879699] Slow work thread pool: Starting up
[    2.879983] Slow work thread pool: Ready
[    2.893453] acpi device:2d: registered as cooling_device4
[    2.894017] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:02/input/input7
[    2.894052] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.894067] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.199525] Skipping EDID probe due to cached edid
[    8.365367] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    8.365372] EXT4-fs (sda5): write access will be enabled during recovery
[    8.658784] EXT4-fs (sda5): orphan cleanup on readonly fs
[    8.658794] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 4980814
[    8.658851] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 4980813
[    8.658862] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 4719769
[    8.658882] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 4719508
[    8.658905] EXT4-fs (sda5): 4 orphan inodes deleted
[    8.658907] EXT4-fs (sda5): recovery complete
[    9.987849] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   20.028732] udev[459]: starting version 163
[   20.054398] lp: driver loaded but no devices found
[   20.121838] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   20.121864] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   20.143299] lib80211: common routines for IEEE802.11 drivers
[   20.143304] lib80211_crypt: registered algorithm 'NULL'
[   20.149757] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.193146] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.193151] Disabling lock debugging due to kernel taint
[   20.216943] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   20.217043] dell-wmi-aio: No known WMI GUID found
[   20.240509] Linux video capture interface: v2.00
[   20.241427] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   20.247328] wl 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.247339] wl 0000:12:00.0: setting latency timer to 64
[   20.266879] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
[   20.283797] lib80211_crypt: registered algorithm 'TKIP'
[   20.283897] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   20.289741] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input9
[   20.289819] usbcore: registered new interface driver uvcvideo
[   20.289822] USB Video Class driver (v0.1.0)
[   20.312553] r8169 0000:13:00.0: eth0: link down
[   20.312745] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.345719]   alloc irq_desc for 22 on node -1
[   20.345722]   alloc kstat_irqs on node -1
[   20.345730] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.345789]   alloc irq_desc for 47 on node -1
[   20.345791]   alloc kstat_irqs on node -1
[   20.345804] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   20.345838] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.370168] type=1400 audit(1293231380.914:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=759 comm="apparmor_parser"
[   20.370641] type=1400 audit(1293231380.914:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=759 comm="apparmor_parser"
[   20.370901] type=1400 audit(1293231380.914:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=759 comm="apparmor_parser"
[   20.409594] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.409671] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.063473] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   21.174706] type=1400 audit(1293231381.722:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1024 comm="apparmor_parser"
[   21.175748] type=1400 audit(1293231381.726:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1025 comm="apparmor_parser"
[   21.176223] type=1400 audit(1293231381.726:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1025 comm="apparmor_parser"
[   21.176483] type=1400 audit(1293231381.726:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1025 comm="apparmor_parser"
[   21.177152] type=1400 audit(1293231381.726:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1091 comm="apparmor_parser"
[   21.179133] type=1400 audit(1293231381.726:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1060 comm="apparmor_parser"
[   21.179832] type=1400 audit(1293231381.730:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1060 comm="apparmor_parser"
[   21.210454] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
[   21.283183] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   21.283578] apm: BIOS not found.
[   21.427420] Skipping EDID probe due to cached edid
[   21.454740] Skipping EDID probe due to cached edid
[   22.571455] Skipping EDID probe due to cached edid
[   22.860928] Skipping EDID probe due to cached edid
[   23.056020] ppdev: user-space parallel port driver
[   23.088511] Skipping EDID probe due to cached edid
[   23.116907] Skipping EDID probe due to cached edid
[   23.907040] padlock: VIA PadLock not detected.
[   23.932429] padlock: VIA PadLock Hash Engine not detected.
[   24.640575] Adding 4183036k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4183036k 
[   24.894332] Skipping EDID probe due to cached edid
[   25.311396] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   25.391707] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   30.384181] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   31.526442] eth1: no IPv6 routers present
[   35.376620] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   40.369126] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   45.361606] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   50.354032] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   55.346545] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   60.338986] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   60.869360] Skipping EDID probe due to cached edid
[   60.898430] Skipping EDID probe due to cached edid
[   60.932567] Skipping EDID probe due to cached edid
[   60.966418] Skipping EDID probe due to cached edid
[   61.022502] Skipping EDID probe due to cached edid
[   65.331490] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   66.365480] Skipping EDID probe due to cached edid
[   70.323899] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   70.464231] usb 2-1.6: USB disconnect, address 3
[   70.464238] usb 2-1.6.1: USB disconnect, address 4
[   70.544870] usb 2-1.6.2: USB disconnect, address 5
[   75.316354] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   77.784920] usb 2-1.6: new full speed USB device using ehci_hcd and address 6
[   77.879658] hub 2-1.6:1.0: USB hub found
[   77.879813] hub 2-1.6:1.0: 3 ports detected
[   78.152483] usb 2-1.6.1: new full speed USB device using ehci_hcd and address 7
[   78.249865] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input13
[   78.249942] generic-usb 0003:413C:8161.0003: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[   78.324581] usb 2-1.6.2: new full speed USB device using ehci_hcd and address 8
[   78.422736] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input14
[   78.422858] generic-usb 0003:413C:8162.0004: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[   80.308856] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   85.301332] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   90.293815] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   95.286254] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  100.280221] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  105.271281] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  110.263654] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  115.256184] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  120.250103] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  125.241139] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  130.233624] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  135.226071] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  140.218546] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  145.210990] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  150.203509] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  155.196002] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  160.188402] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  165.180904] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  170.173369] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  175.165834] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  180.158304] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  185.150841] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  190.143302] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  195.135754] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  200.128287] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  205.120646] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  210.113130] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  215.105634] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  220.098113] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  225.090647] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  230.083089] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  235.075510] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  240.067995] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  245.060496] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  250.055527] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  255.045388] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  260.037869] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  265.030340] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded



sam@drytopubuntu:~$ sudo lshw -c network
[sudo] password for sam: 
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:a1:9e:86
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbc00000-fbc03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: f0:4d:a2:b1:75:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:e000(size=256) memory:d0b10000-d0b10fff memory:d0b00000-d0b0ffff memory:fb200000-fb21ffff


sam@drytopubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.


sam@drytopubuntu:~$ lsb_release -d
Description:	Ubuntu 10.10


sam@drytopubuntu:~$ uname -mr
2.6.35-24-generic i686



sam@drytopubuntu:~$ sudo /etc/init.d/network restart
sudo: /etc/init.d/network: command not found
sam@drytopubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1967
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/f0:4d:a2:b1:75:3b
Sending on   LPF/eth0/f0:4d:a2:b1:75:3b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 2029
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/1c:65:9d:a1:9e:86
Sending on   LPF/eth1/1c:65:9d:a1:9e:86
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/f0:4d:a2:b1:75:3b
Sending on   LPF/eth0/f0:4d:a2:b1:75:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/1c:65:9d:a1:9e:86
Sending on   LPF/eth1/1c:65:9d:a1:9e:86
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

if anyone has any ideas i would really appreciate the help.

thanks in advance

sam

---

### Post by topbayder on 2010-12-26
still struggling with this to get it working. I have noticed that the driver available in the synaptic package manager is version 5.60.48.36 and when checking the broadcom website it says the version available there is 5.100.57.13

5.100.57.13 is a newer driver right? so i am trying to install it. but i dont know how to do this using the console. i have been trying all day and i just dont get it. i have copied and pasted lines from the readme that comes with the driver.tar but just says cant find directory. i have exhausted the different variations i could think of and have now resorted to looking around for a precompiled .deb but there are none out there.

if anyone has compiled this succesfully please make the .deb available for download. it would really help me and i am sure a lot of other people out.

---

### Post by ddryden on 2010-12-26
Out of interest did the default b43 driver work before you started playing with the STA driver?

A really help full guide is here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by topbayder on 2010-12-26
No I have never had the b43 driver working. After fresh installation of ubuntu studio 10.10 the driver that showed up in additional drivErs was the broadcom sta driver which has a green light when activated but doesn't actually do anything even when entering all the network info into network manager like I was trying to connect to a hidden network. The b43 driver has never showed up in the additional drivers list and my network card 4313 isn't on the supported devices list in the b43 driver description. 

I really think my best bet is trying to upgrade the sta driver to the new release available on the broadcom website. But I have downloaded the file for 64 bit os and tried to build the driver... Which is way over my head and I don't get past the third line of script you have to enter into the shell to compile it. Lol

---

### Post by bkratz on 2010-12-27
> **topbayder said:**
> 

I really think my best bet is trying to upgrade the sta driver to the new release available on the broadcom website. But I have downloaded the file for 64 bit os and tried to build the driver... Which is way over my head and I don't get past the third line of script you have to enter into the shell to compile it. Lol

Can you be a little more specific on exactly where you are having problems with the compile?  Where is the "third line" of scripts in the readme? There aren't any numbered steps.

---

### Post by grahammechanical on 2010-12-27
The first thing we have to remember here is that Ubuntu Studio is not designed to be networked. There is apparently some kind of  conflict. 

Second, Network Manager is not installed. Therefore you will not find any icon in the top panel.

I am using Ubuntu Studio on a test partition. I have not be able to set up wired networking. I have managed, somehow, to get wireless working. The first indication I got that I had connected to the router/modem was when Update Manager loaded with a message that updates were available.

To get some indication that I am connected I have installed in the top panel using Add to Panel something called Network Monitor. (I think that is what it is called. It is not present in standard Ubuntu which is what I am using just now).

To get wireless working I think I typed in a terminal ifconfig wlan0 up. Then I rebooted. I have found that sometimes wireless is not activated when I boot into Ubuntu Studio. I will take 2 or 3 reboots to get it activated.

Regards.

---

### Post by topbayder on 2010-12-27
ok so basically just get the standard ubuntu and it should work then? simple enough :) I can always just install some of the music production stuff on there anyway right?

@bkratz - sorry dude i am in my windows partition and i think i am going to just try installing just Ubuntu. rather then ubuntu studio. the file i was referring to was in the tar that can be downloaded from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) its the only reedme in the tar. litterally i am refferring to the first few lines that it says you need to type into the shell. i think i managed to create the "wireless" folder and then was in that folder and thats as far as i got.

@grahammechanical - thanks for the heads up, i didnt realise it wasn't made for wireless. i have rebooted so many times i cant take anymore lol. im going to try the easy way out and install Ubuntu 10.10

---

### Post by bkratz on 2010-12-27
> **topbayder said:**
> 

@bkratz - sorry dude i am in my windows partition and i think i am going to just try installing just Ubuntu. rather then ubuntu studio. the file i was referring to was in the tar that can be downloaded from here: 

@grahammechanical - thanks for the heads up, i didnt realise it wasn't made for wireless. i have rebooted so many times i cant take anymore lol. im going to try the easy way out and install Ubuntu 10.10

If you want to explore it further here is the best description of building that driver I have seen. Starting with posts 19 and 20. You would have to substitute the name of the newest driver from the site. Good education if nothing else.

[http://newyork.ubuntuforums.org/showthread.php?t=1480671&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1480671&page=2)

---

### Post by topbayder on 2010-12-28
installed ubuntu 10.10 and got rid of ubuntu studio. works great. wifi straight out the box!! :) cheers people

---

