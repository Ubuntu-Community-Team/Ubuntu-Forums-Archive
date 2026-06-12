---
title: "Ubuntu 10.10 Acer Aspire one D250 wireless problem"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by ubun22 on 2011-06-29
My Acer Aspire one D250 laptop running Ubuntu 10.10 wireless does not work.

I dual boot with Windows XP BUT windows XP wireless works fine.

here are some details you might need.

Please Help me.

[COLOR=Red]**lspci**[/COLOR]
```
ubun2@ubun2-Aspire-one:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
ubun2@ubun2-Aspire-one:~$ 


```[COLOR=Red][B]lsmod
[/B][/COLOR]```
ubun2@ubun2-Aspire-one:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40204  1 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
joydev                  8767  0 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
i915                  295435  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168060  3 i915,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
videodev               43098  1 uvcvideo
intel_agp              26566  2 i915
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
led_class               2633  0 
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21728  1 ahci
ssb                    39320  0 
atl1c                  2994

```[COLOR=Red]**lspci -nn**[/COLOR]
```
ubun2@ubun2-Aspire-one:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
ubun2@ubun2-Aspire-one:~$

```[COLOR=Red]**lsusb**[/COLOR]
```
ubun2@ubun2-Aspire-one:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubun2@ubun2-Aspire-one:~$ 

```**[COLOR=Red]ifconfig[/COLOR]**
```
ubun2@ubun2-Aspire-one:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:29:b2:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ubun2@ubun2-Aspire-one:~$ 

```**[COLOR=Red]iwconfig[/COLOR]**
```
ubun2@ubun2-Aspire-one:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubun2@ubun2-Aspire-one:~$ 


```[COLOR=Red]**lsb_release -d**[/COLOR]
```
ubun2@ubun2-Aspire-one:~$ lsb_release -d
Description:    Ubuntu 10.10
ubun2@ubun2-Aspire-one:~$ 

```[COLOR=Red]**uname -mr**[/COLOR]
```
ubun2@ubun2-Aspire-one:~$ uname -mr
2.6.35-28-generic i686
ubun2@ubun2-Aspire-one:~$

```[COLOR=Red]**dmesg**[/COLOR]
```
[    0.394321] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.394688] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.395032] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.395378] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.395717] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.395901] HEST: Table is not found!
[    0.396191] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.396223] vgaarb: loaded
[    0.396772] SCSI subsystem initialized
[    0.397012] libata version 3.00 loaded.
[    0.397223] usbcore: registered new interface driver usbfs
[    0.397271] usbcore: registered new interface driver hub
[    0.397364] usbcore: registered new device driver usb
[    0.399096] ACPI: WMI: Mapper loaded
[    0.399105] PCI: Using ACPI for IRQ routing
[    0.399114] PCI: pci_cache_line_size set to 64 bytes
[    0.399347] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.399356] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.399366] reserve RAM buffer: 000000003f576000 - 000000003fffffff 
[    0.399376] reserve RAM buffer: 000000003f66d000 - 000000003fffffff 
[    0.399385] reserve RAM buffer: 000000003f6ee000 - 000000003fffffff 
[    0.399394] reserve RAM buffer: 000000003f700000 - 000000003fffffff 
[    0.399710] NetLabel: Initializing
[    0.399718] NetLabel:  domain hash size = 128
[    0.399723] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.399759] NetLabel:  unlabeled traffic allowed by default
[    0.399874] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.399889] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.399905] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.408097] Switching to clocksource tsc
[    0.436406] AppArmor: AppArmor Filesystem Enabled
[    0.436452] pnp: PnP ACPI init
[    0.436499] ACPI: bus type pnp registered
[    0.500483] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
[    0.503279] pnp: PnP ACPI: found 9 devices
[    0.503288] ACPI: ACPI bus type pnp unregistered
[    0.503315] PnPBIOS: Disabled by ACPI PNP
[    0.503351] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.503363] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.503372] system 00:01: [io  0x0610] has been reserved
[    0.503381] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.503390] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.503399] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.503409] system 00:01: [io  0xff2c-0xff2f] has been reserved
[    0.503422] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.503432] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.503442] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.503452] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.503462] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.503473] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.503483] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.543851] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.543867] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.543880] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
[    0.543893] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.543908] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.543917] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.543929] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
[    0.543941] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.543956] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.543965] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
[    0.543978] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
[    0.543990] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.544004] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.544014] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.544026] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
[    0.544038] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
[    0.544053] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.544059] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.544070] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.544080] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.544123]   alloc irq_desc for 16 on node -1
[    0.544130]   alloc kstat_irqs on node -1
[    0.544147] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.544160] pci 0000:00:1c.0: setting latency timer to 64
[    0.544180] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.544190]   alloc irq_desc for 17 on node -1
[    0.544196]   alloc kstat_irqs on node -1
[    0.544208] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.544221] pci 0000:00:1c.1: setting latency timer to 64
[    0.544241]   alloc irq_desc for 18 on node -1
[    0.544246]   alloc kstat_irqs on node -1
[    0.544258] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.544269] pci 0000:00:1c.2: setting latency timer to 64
[    0.544287] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.544297]   alloc irq_desc for 19 on node -1
[    0.544303]   alloc kstat_irqs on node -1
[    0.544314] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.544327] pci 0000:00:1c.3: setting latency timer to 64
[    0.544344] pci 0000:00:1e.0: setting latency timer to 64
[    0.544355] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.544363] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
[    0.544372] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.544381] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.544390] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.544398] pci_bus 0000:01: resource 1 [mem 0x57100000-0x581fffff]
[    0.544407] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.544416] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.544424] pci_bus 0000:02: resource 1 [mem 0x56100000-0x570fffff]
[    0.544434] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.544442] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
[    0.544450] pci_bus 0000:03: resource 1 [mem 0x55000000-0x560fffff]
[    0.544458] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
[    0.544467] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.544475] pci_bus 0000:04: resource 1 [mem 0x54000000-0x54ffffff]
[    0.544484] pci_bus 0000:04: resource 2 [mem 0x53000000-0x53ffffff 64bit pref]
[    0.544493] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.544502] pci_bus 0000:05: resource 5 [io  0x0d00-0xefff]
[    0.544511] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.544520] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
[    0.544634] NET: Registered protocol family 2
[    0.544810] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.545622] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.546729] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.547338] TCP: Hash tables configured (established 131072 bind 65536)
[    0.547348] TCP reno registered
[    0.547365] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.547389] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.547675] NET: Registered protocol family 1
[    0.547734] pci 0000:00:02.0: Boot video device
[    0.548071] PCI: CLS 0 bytes, default 64
[    0.548142] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.548149] Simple Boot Flag at 0x44 set to 0x1
[    0.548733] cpufreq-nforce2: No nForce2 chipset.
[    0.548836] Scanning for low memory corruption every 60 seconds
[    0.549268] audit: initializing netlink socket (disabled)
[    0.549297] type=2000 audit(1309362837.544:1): initialized
[    0.572722] highmem bounce pool size: 64 pages
[    0.572740] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.577927] VFS: Disk quotas dquot_6.5.2
[    0.578131] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.580267] fuse init (API version 7.14)
[    0.580620] msgmni has been set to 1709
[    0.734933] Freeing initrd memory: 10524k freed
[    0.750129] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.750137] io scheduler noop registered
[    0.750142] io scheduler deadline registered
[    0.750186] io scheduler cfq registered (default)
[    0.750417] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.750475]   alloc irq_desc for 40 on node -1
[    0.750480]   alloc kstat_irqs on node -1
[    0.750499] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.750679] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.750733]   alloc irq_desc for 41 on node -1
[    0.750737]   alloc kstat_irqs on node -1
[    0.750751] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.750922] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.750975]   alloc irq_desc for 42 on node -1
[    0.750979]   alloc kstat_irqs on node -1
[    0.750993] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.751161] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.751214]   alloc irq_desc for 43 on node -1
[    0.751218]   alloc kstat_irqs on node -1
[    0.751234] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.751492] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.751723] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.751738] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.752008] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.752022] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.752278] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.752291] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.752545] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.752559] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.752858] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.752871] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.753127] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.753141] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.753398] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.753412] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.753668] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.753681] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7021a68), AE_ALREADY_EXISTS
[    0.753778] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.753990] intel_idle: MWAIT substates: 0x20220
[    0.753995] intel_idle: v0.4 model 0x1C
[    0.753998] intel_idle: lapic_timer_reliable_states 0x2
[    0.754010] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.754116] Switching to clocksource hpet
[    0.816185] ACPI: AC Adapter [AC] (off-line)
[    0.816378] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.816390] ACPI: Power Button [PWRB]
[    0.816491] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.816582] ACPI: Lid Switch [LID0]
[    0.816686] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.816696] ACPI: Sleep Button [SLPB]
[    0.816825] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.816834] ACPI: Power Button [PWRF]
[    0.817152] ACPI: Fan [FAN] (on)
[    0.817710] ACPI: acpi_idle yielding to intel_idle
[    0.884048] thermal LNXTHERM:01: registered as thermal_zone0
[    0.884067] ACPI: Thermal Zone [THRM] (27 C)
[    0.884271] ERST: Table is not found!
[    0.884462] isapnp: Scanning for PnP cards...
[    0.885084] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.889399] brd: module loaded
[    0.891159] loop: module loaded
[    0.892948] Fixed MDIO Bus: probed
[    0.893075] PPP generic driver version 2.4.2
[    0.893210] tun: Universal TUN/TAP device driver, 1.6
[    0.893216] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.893446] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.893501] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.893540] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.893549] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.893651] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.893702] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.893722] ehci_hcd 0000:00:1d.7: debug port 1
[    0.897623] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.897665] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    0.912032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.912381] hub 1-0:1.0: USB hub found
[    0.912397] hub 1-0:1.0: 8 ports detected
[    0.912590] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.912637] uhci_hcd: USB Universal Host Controller Interface driver
[    0.912707] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.912724] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.912734] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.912851] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.912898] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    0.913252] hub 2-0:1.0: USB hub found
[    0.913266] hub 2-0:1.0: 2 ports detected
[    0.913418] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.913434] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.913442] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.913550] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.913614] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    0.913965] hub 3-0:1.0: USB hub found
[    0.913978] hub 3-0:1.0: 2 ports detected
[    0.914121] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.914137] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.914145] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.914245] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.914306] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    0.914662] hub 4-0:1.0: USB hub found
[    0.914675] hub 4-0:1.0: 2 ports detected
[    0.914818] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.914834] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.914842] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.914951] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.915013] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    0.915363] hub 5-0:1.0: USB hub found
[    0.915376] hub 5-0:1.0: 2 ports detected
[    0.915673] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.935728] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.935748] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.935967] mice: PS/2 mouse device common for all mice
[    0.936438] rtc_cmos 00:03: RTC can wake from S4
[    0.936554] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.936605] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.936957] device-mapper: uevent: version 1.0.3
[    0.937297] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.937499] device-mapper: multipath: version 1.1.1 loaded
[    0.937507] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.937870] EISA: Probing bus 0 at eisa.0
[    0.937878] EISA: Cannot allocate resource for mainboard
[    0.937886] Cannot allocate resource for EISA slot 1
[    0.937894] Cannot allocate resource for EISA slot 2
[    0.937901] Cannot allocate resource for EISA slot 3
[    0.937909] Cannot allocate resource for EISA slot 4
[    0.937916] Cannot allocate resource for EISA slot 5
[    0.937924] Cannot allocate resource for EISA slot 6
[    0.937931] Cannot allocate resource for EISA slot 7
[    0.937939] Cannot allocate resource for EISA slot 8
[    0.937944] EISA: Detected 0 cards.
[    0.938382] cpuidle: using governor ladder
[    0.938768] cpuidle: using governor menu
[    0.939554] TCP cubic registered
[    0.939980] NET: Registered protocol family 10
[    0.940979] lo: Disabled Privacy Extensions
[    0.941571] NET: Registered protocol family 17
[    0.943689] Using IPI No-Shortcut mode
[    0.943990] PM: Resume from disk failed.
[    0.944052] registered taskstats version 1
[    0.944637]   Magic number: 15:110:893
[    0.944789] rtc_cmos 00:03: setting system clock to 2011-06-29 15:53:58 UTC (1309362838)
[    0.944798] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.944803] EDD information not available.
[    0.963250] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.236048] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.239537] isapnp: No Plug & Play device found
[    1.239610] Freeing unused kernel memory: 688k freed
[    1.240288] Write protecting the kernel text: 4940k
[    1.240361] Write protecting the kernel read-only data: 1976k
[    1.279787] udev[76]: starting version 163
[    1.536424] ACPI: Battery Slot [BAT0] (battery present)
[    2.094707] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.094734] atl1c 0000:03:00.0: setting latency timer to 64
[    2.135527] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.135558] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[    2.152316] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.152345] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.152371] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.152397] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.153784] ahci 0000:00:1f.2: version 3.0
[    2.153824] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.153905]   alloc irq_desc for 44 on node -1
[    2.153912]   alloc kstat_irqs on node -1
[    2.153936] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    2.154021] ahci: SSS flag set, parallel bus scan disabled
[    2.154082] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    2.154093] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    2.154106] ahci 0000:00:1f.2: setting latency timer to 64
[    2.154811] scsi0 : ahci
[    2.155213] scsi1 : ahci
[    2.155475] scsi2 : ahci
[    2.155716] scsi3 : ahci
[    2.156577] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 44
[    2.156588] ata2: DUMMY
[    2.156597] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 44
[    2.156604] ata4: DUMMY
[    2.193333] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[    2.197740] atl1c 0000:03:00.0: version 1.0.0.2-NAPI
[    2.476141] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.477460] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.477840] ata1.00: ATA-8: Hitachi HTS545016B9A300, PBBOC60F, max UDMA/133
[    2.477853] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.479509] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.479926] ata1.00: configured for UDMA/133
[    2.492472] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54501 PBBO PQ: 0 ANSI: 5
[    2.492999] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.493311] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.493520] sd 0:0:0:0: [sda] Write Protect is off
[    2.493528] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.493595] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.494251]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.550502] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.812136] ata3: SATA link down (SStatus 0 SControl 300)
[    3.547977] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   16.897106] Adding 520188k swap on /dev/sda6.  Priority:-1 extents:1 across:520188k 
[   16.973954] udev[351]: starting version 163
[   17.073968] lp: driver loaded but no devices found
[   17.237721] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   17.521279] acpi device:24: registered as cooling_device3
[   17.521798] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   17.521950] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   17.692187] intel_rng: FWH not detected
[   17.933292] Linux agpgart interface v0.103
[   17.944622] leds_ss4200: no LED devices found
[   18.257179] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   18.257916] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   18.260752] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   18.358249] Linux video capture interface: v2.00
[   18.503238] uvcvideo: Found UVC 1.00 device WebCam (064e:d101)
[   18.523523] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input6
[   18.523974] usbcore: registered new interface driver uvcvideo
[   18.523983] USB Video Class driver (v0.1.0)
[   18.627623] [drm] Initialized drm 1.1.0 20060810
[   18.758698] type=1400 audit(1309323256.307:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=709 comm="apparmor_parser"
[   18.760382] type=1400 audit(1309323256.311:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=709 comm="apparmor_parser"
[   18.760871] type=1400 audit(1309323256.311:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=709 comm="apparmor_parser"
[   18.767558] type=1400 audit(1309323256.315:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=714 comm="apparmor_parser"
[   18.769209] type=1400 audit(1309323256.319:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=714 comm="apparmor_parser"
[   18.769717] type=1400 audit(1309323256.319:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=714 comm="apparmor_parser"
[   18.958318] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.958333] i915 0000:00:02.0: setting latency timer to 64
[   19.047034]   alloc irq_desc for 45 on node -1
[   19.047044]   alloc kstat_irqs on node -1
[   19.047076] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[   19.048416] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.255003] [drm] set up 7M of stolen space
[   19.364563] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   19.365239] [drm] initialized overlay support
[   19.486048] type=1400 audit(1309323257.035:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=853 comm="apparmor_parser"
[   19.492650] type=1400 audit(1309323257.043:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=854 comm="apparmor_parser"
[   19.503140] type=1400 audit(1309323257.051:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=854 comm="apparmor_parser"
[   19.503551] type=1400 audit(1309323257.051:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=854 comm="apparmor_parser"
[   19.677090] Skipping EDID probe due to cached edid
[   19.898751] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000/0xa0000
[   19.984292] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   20.095902] Console: switching to colour frame buffer device 128x37
[   20.102639] fb0: inteldrmfb frame buffer device
[   20.102644] drm: registered panic notifier
[   20.102656] Slow work thread pool: Starting up
[   20.102992] Slow work thread pool: Ready
[   20.103020] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.103128] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.103230]   alloc irq_desc for 46 on node -1
[   20.103238]   alloc kstat_irqs on node -1
[   20.103265] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   20.103328] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.205983] hda_codec: ALC272X: BIOS auto-probing.
[   20.273128] Skipping EDID probe due to cached edid
[   20.501821] ppdev: user-space parallel port driver
[   20.973342] Skipping EDID probe due to cached edid
[   21.104253] Skipping EDID probe due to cached edid
[   21.645984] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   22.220171] Skipping EDID probe due to cached edid
[   22.260171] Skipping EDID probe due to cached edid
[   22.360174] Skipping EDID probe due to cached edid
[   22.396074] Skipping EDID probe due to cached edid
[   24.668162] Skipping EDID probe due to cached edid
[   25.256841] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   30.464138] Skipping EDID probe due to cached edid
[   30.501230] Skipping EDID probe due to cached edid
[   30.536182] Skipping EDID probe due to cached edid
[   30.568181] Skipping EDID probe due to cached edid
[   30.808203] Skipping EDID probe due to cached edid
[   36.068131] Skipping EDID probe due to cached edid
[   50.052136] usb 1-1: new high speed USB device using ehci_hcd and address 3
[   50.264702] Initializing USB Mass Storage driver...
[   50.265070] scsi4 : usb-storage 1-1:1.0
[   50.265638] usbcore: registered new interface driver usb-storage
[   50.265647] USB Mass Storage support registered.
[   51.265061] scsi 4:0:0:0: Direct-Access              USB FLASH DRIVE  PMAP PQ: 0 ANSI: 0 CCS
[   51.266390] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   52.739246] sd 4:0:0:0: [sdb] 2015232 512-byte logical blocks: (1.03 GB/984 MiB)
[   52.739841] sd 4:0:0:0: [sdb] Write Protect is off
[   52.739849] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   52.739855] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   52.745845] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   52.745876]  sdb: sdb1
[   52.748653] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   52.748668] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  136.820366] usb 1-1: USB disconnect, address 3
[  139.624158] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  139.760236] scsi5 : usb-storage 1-1:1.0
[  140.761196] scsi 5:0:0:0: Direct-Access              USB FLASH DRIVE  PMAP PQ: 0 ANSI: 0 CCS
[  140.763277] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  140.929283] sd 5:0:0:0: [sdb] 2015232 512-byte logical blocks: (1.03 GB/984 MiB)
[  140.929877] sd 5:0:0:0: [sdb] Write Protect is off
[  140.929890] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  140.929900] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  140.935396] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  140.935445]  sdb: sdb1
[  140.941264] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  140.941280] sd 5:0:0:0: [sdb] Attached SCSI removable disk
ubun2@ubun2-Aspire-one:~$ 


```

PS I am a newbie I got these commands to get information from my laptop here [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by josephmills on 2011-06-29
could we see a```
 lspci -nn 
```thanks

---

### Post by ubun22 on 2011-07-01
> **josephmills said:**
> could we see a```
 lspci -nn 
```thanks

Here is the result for **[COLOR=Red]lspci -nn[/COLOR]**

ubun2@ubun2-Aspire-one:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
ubun2@ubun2-Aspire-one:~$

---

### Post by nm_geo on 2011-07-01
> **ubun22 said:**
> Here is the result for **[COLOR=Red]lspci -nn[/COLOR]**

ubun2@ubun2-Aspire-one:~$ lspci -nn

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
ubun2@ubun2-Aspire-one:~$

ubun22 you need the b43-fwcutter and the firmware-b43-lpphy-installer..
The firmware is for low power chip. You only need those two no others for your wireless.

---

### Post by MarcG on 2011-07-01
I solved it. The low-power drivers work. I just forgot to activate the STA driver in addition to the B43.

> **nm_geo said:**
> ubun22 you need the b43-fwcutter and the firmware-b43-lpphy-installer..
The firmware is for low power chip. You only need those two no others for your wireless.

Same problem on my eMachines E725. I installed cc and b43-fwcutter was already installed. I was then able to activate the driver, but wireless networks still don't show up.

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)

```

---

### Post by ubun22 on 2011-07-02
> **nm_geo said:**
> ubun22 you need the b43-fwcutter and the firmware-b43-lpphy-installer..
The firmware is for low power chip. You only need those two no others for your wireless.

Where should I get these installers ?

---

### Post by ubun22 on 2011-07-02
> **nm_geo said:**
> ubun22 you need the b43-fwcutter and the firmware-b43-lpphy-installer..
The firmware is for low power chip. You only need those two no others for your wireless.
Finally I found this

[https://launchpad.net/ubuntu/maverick/+package/firmware-b43-lpphy-installer](https://launchpad.net/ubuntu/maverick/+package/firmware-b43-lpphy-installer)

But which one specifically should i download and install ?

[[IMG]http://img215.imageshack.us/img215/8723/b43l.png[/IMG]]("http://imageshack.us/photo/my-images/215/b43l.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by dcommini on 2011-12-26
Has this problem been resolved yet? As in not a problem in the latest version (10.10.##)? I only ask as I am deployed to Kuwait right now and if I upgrade I have no way of logging on to the internet with out wireless capabilities. Obviously if I want to keep in touch back home I will need something that will work once I click the "Upgrade" button.

---

