---
title: "Can't connect wirelessly anymore"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by Green Zubat on 2012-07-19
Hi, new user here. So, I recently switched from Windows Vista to Ubuntu (11.10/"Oneiric Ocelot"), and it's great and everything, but it won't connect wirelessly anymore. Can anyone help me fix it? 

I'm using a 32-bit Dell Inspiron 1501. I've included some other outputs below, if it helps:
[B]
Network configuration:[/B]

```
~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 02
       serial: 00:19:b9:53:2a:03
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.64 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:c0300000-c0301fff

```

**Wireless Brand, Model and Wireless Chipset:**

lspci:

```
~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
```

lsusb:

```

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


**Interface checks:**

```
~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:b9:53:2a:03  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe53:2a03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24548964 (24.5 MB)  TX bytes:2098333 (2.0 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66200 (66.2 KB)  TX bytes:66200 (66.2 KB)


```

```
~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.
```

**Rfkill:**


```
~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```


**Module check:**

```
~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
bluetooth             148869  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  2 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
dell_laptop            13519  0 
snd_seq_midi           13132  0 
radeon                933705  3 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
b44                    31443  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ssb                    50682  1 b44
ttm                    65224  1 radeon
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
wl                   2646601  0 
psmouse                73673  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
k8temp                 12905  0 
binfmt_misc            17292  1 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
i2c_piix4              13093  0 
shpchp                 32356  0 
lib80211               14570  1 wl
ati_agp                13242  0 
wmi                    18744  1 dell_wmi
video                  19069  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
pata_atiixp            12967  0 
ahci                   21634  2 
libahci                25727  1 ahci

```


**Kernal boot messages/dmesg:**


```
[    0.119325] system 00:08: [io  0x0c14] has been reserved
[    0.119329] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.119332] system 00:08: [io  0x0c6c] has been reserved
[    0.119336] system 00:08: [io  0x0c6f] has been reserved
[    0.119339] system 00:08: [io  0x0cd0-0x0cd3] has been reserved
[    0.119343] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.119346] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.119350] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.119354] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.119358] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.119361] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.119365] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.119369] system 00:08: [io  0x087f] has been reserved
[    0.119373] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.119439] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.119442] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.119448] pnp 00:09: [mem 0xc0004800-0xc0004bff]
[    0.119451] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.119454] pnp 00:09: [mem 0x00000000-0x00000fff]
[    0.119475] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.119519] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.119524] system 00:09: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.119527] system 00:09: [mem 0xc0004800-0xc0004bff] has been reserved
[    0.119531] system 00:09: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.119535] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.120035] pnp: PnP ACPI: found 10 devices
[    0.120037] ACPI: ACPI bus type pnp unregistered
[    0.120041] PnPBIOS: Disabled by ACPI PNP
[    0.156612] Switching to clocksource acpi_pm
[    0.156639] PCI: max bus depth: 1 pci_try_num: 2
[    0.156669] pci 0000:00:06.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
[    0.156675] pci 0000:00:06.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.156679] pci 0000:00:05.0: BAR 14: assigned [mem 0x40200000-0x403fffff]
[    0.156683] pci 0000:00:05.0: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[    0.156688] pci 0000:00:05.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.156693] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
[    0.156698] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.156701] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.156707] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.156711] pci 0000:00:01.0:   bridge window [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.156716] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    0.156720] pci 0000:00:05.0:   bridge window [io  0x3000-0x3fff]
[    0.156724] pci 0000:00:05.0:   bridge window [mem 0x40200000-0x403fffff]
[    0.156729] pci 0000:00:05.0:   bridge window [mem 0x40400000-0x405fffff 64bit pref]
[    0.156734] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    0.156737] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.156742] pci 0000:00:06.0:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.156746] pci 0000:00:06.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
[    0.156752] pci 0000:00:14.4: PCI bridge to [bus 08-0a]
[    0.156754] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.156761] pci 0000:00:14.4:   bridge window [mem 0xc0300000-0xc03fffff]
[    0.156767] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.156783] pci 0000:00:05.0: enabling device (0000 -> 0003)
[    0.156788] pci 0000:00:05.0: setting latency timer to 64
[    0.156794] pci 0000:00:06.0: setting latency timer to 64
[    0.156803] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.156806] pci_bus 0000:00: resource 5 [mem 0x40000000-0xefffffff]
[    0.156810] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.156813] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xffffffff]
[    0.156817] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.156820] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
[    0.156824] pci_bus 0000:01: resource 2 [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.156828] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.156831] pci_bus 0000:02: resource 1 [mem 0x40200000-0x403fffff]
[    0.156834] pci_bus 0000:02: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[    0.156838] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.156841] pci_bus 0000:05: resource 1 [mem 0xc0200000-0xc02fffff]
[    0.156845] pci_bus 0000:05: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
[    0.156849] pci_bus 0000:08: resource 1 [mem 0xc0300000-0xc03fffff]
[    0.156852] pci_bus 0000:08: resource 4 [io  0x0000-0xffff]
[    0.156855] pci_bus 0000:08: resource 5 [mem 0x40000000-0xefffffff]
[    0.156859] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.156862] pci_bus 0000:08: resource 7 [mem 0xf0000000-0xffffffff]
[    0.156911] NET: Registered protocol family 2
[    0.156981] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.157292] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.157971] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.158303] TCP: Hash tables configured (established 131072 bind 65536)
[    0.158306] TCP reno registered
[    0.158310] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.158322] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.158428] NET: Registered protocol family 1
[    0.158441] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.158448] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.158479] pci 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.158512] pci 0000:00:13.0: PCI INT A disabled
[    0.158525] pci 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.158542] pci 0000:00:13.1: PCI INT B disabled
[    0.158555] pci 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.158572] pci 0000:00:13.2: PCI INT C disabled
[    0.158581] pci 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.158597] pci 0000:00:13.3: PCI INT B disabled
[    0.158606] pci 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.158623] pci 0000:00:13.4: PCI INT C disabled
[    0.158636] pci 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.158654] pci 0000:00:13.5: PCI INT D disabled
[    0.158680] pci 0000:01:05.0: Boot video device
[    0.158694] PCI: CLS 32 bytes, default 64
[    0.159105] audit: initializing netlink socket (disabled)
[    0.159116] type=2000 audit(1342720132.156:1): initialized
[    0.159420] Switched to NOHz mode on CPU #0
[    0.185013] Trying to unpack rootfs image as initramfs...
[    0.218639] highmem bounce pool size: 64 pages
[    0.218647] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.236461] VFS: Disk quotas dquot_6.5.2
[    0.236551] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.237442] fuse init (API version 7.16)
[    0.237571] msgmni has been set to 1707
[    0.248277] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.252415] io scheduler noop registered
[    0.252421] io scheduler deadline registered
[    0.252465] io scheduler cfq registered (default)
[    0.252716] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.252752] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.254655] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.255272] ACPI: AC Adapter [ACAD] (on-line)
[    0.255351] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.255359] ACPI: Power Button [PWRB]
[    0.255423] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.255428] ACPI: Sleep Button [SLPB]
[    0.255479] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.256491] ACPI: Lid Switch [LID]
[    0.256551] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.256555] ACPI: Power Button [PWRF]
[    0.256591] ACPI: acpi_idle registered with cpuidle
[    0.256624] Marking TSC unstable due to TSC halts in idle
[    0.262537] thermal LNXTHERM:00: registered as thermal_zone0
[    0.262542] ACPI: Thermal Zone [THRM] (30 C)
[    0.262584] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.262607] ERST: Table is not found!
[    0.262703] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.264306] Linux agpgart interface v0.103
[    0.266126] brd: module loaded
[    0.266873] loop: module loaded
[    0.267106] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.267152] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.267628] Fixed MDIO Bus: probed
[    0.267666] PPP generic driver version 2.4.2
[    0.267720] tun: Universal TUN/TAP device driver, 1.6
[    0.267722] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.267826] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.267842] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.267868] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.267909] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.267942] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.267959] ehci_hcd 0000:00:13.5: debug port 1
[    0.267992] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[    0.272404] isapnp: Scanning for PnP cards...
[    0.332162] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.332391] hub 1-0:1.0: USB hub found
[    0.332397] hub 1-0:1.0: 10 ports detected
[    0.332547] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.332571] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.332595] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.332644] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.332687] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[    0.428468] hub 2-0:1.0: USB hub found
[    0.428478] hub 2-0:1.0: 2 ports detected
[    0.428571] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.428597] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.428654] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.428699] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[    0.484588] hub 3-0:1.0: USB hub found
[    0.484598] hub 3-0:1.0: 2 ports detected
[    0.484688] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.484714] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.484775] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.484819] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[    0.545537] hub 4-0:1.0: USB hub found
[    0.545547] hub 4-0:1.0: 2 ports detected
[    0.545634] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.545659] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.545707] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.545732] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[    0.619891] hub 5-0:1.0: USB hub found
[    0.619901] hub 5-0:1.0: 2 ports detected
[    0.619995] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.620039] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.620101] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.620127] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[    0.676300] hub 6-0:1.0: USB hub found
[    0.676310] hub 6-0:1.0: 2 ports detected
[    0.676409] uhci_hcd: USB Universal Host Controller Interface driver
[    0.676525] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.678502] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.678509] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.678599] mousedev: PS/2 mouse device common for all mice
[    0.678795] rtc_cmos 00:04: RTC can wake from S4
[    0.678919] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.678947] rtc0: alarms up to one month, 114 bytes nvram
[    0.679058] device-mapper: uevent: version 1.0.3
[    0.679156] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.679194] EISA: Probing bus 0 at eisa.0
[    0.679197] EISA: Cannot allocate resource for mainboard
[    0.679201] Cannot allocate resource for EISA slot 1
[    0.679204] Cannot allocate resource for EISA slot 2
[    0.679206] Cannot allocate resource for EISA slot 3
[    0.679209] Cannot allocate resource for EISA slot 4
[    0.679212] Cannot allocate resource for EISA slot 5
[    0.679215] Cannot allocate resource for EISA slot 6
[    0.679217] Cannot allocate resource for EISA slot 7
[    0.679220] Cannot allocate resource for EISA slot 8
[    0.679222] EISA: Detected 0 cards.
[    0.679234] cpufreq-nforce2: No nForce2 chipset.
[    0.679287] cpuidle: using governor ladder
[    0.679363] cpuidle: using governor menu
[    0.679366] EFI Variables Facility v0.08 2004-May-17
[    0.679669] TCP cubic registered
[    0.679846] NET: Registered protocol family 10
[    0.684672] NET: Registered protocol family 17
[    0.684708] Registering the dns_resolver key type
[    0.684747] Using IPI No-Shortcut mode
[    0.684883] PM: Hibernation image not present or could not be loaded.
[    0.684896] registered taskstats version 1
[    0.810159] isapnp: No Plug & Play device found
[    0.850939] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.900475] ACPI: Battery Slot [BAT1] (battery present)
[    0.961686] Freeing initrd memory: 13332k freed
[    0.977496]   Magic number: 4:26:846
[    0.977605] rtc_cmos 00:04: setting system clock to 2012-07-19 17:48:55 UTC (1342720135)
[    0.977610] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3500+ (1 cpu cores) (version 2.20.00)
[    0.977656] powernow-k8: fid 0xa (1800 MHz), vid 0xe
[    0.977658] powernow-k8: fid 0x8 (1600 MHz), vid 0x10
[    0.977661] powernow-k8: fid 0x0 (800 MHz), vid 0x18
[    0.977716] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.977718] EDD information not available.
[    0.977846] Freeing unused kernel memory: 696k freed
[    0.978276] Write protecting the kernel text: 5348k
[    0.978318] Write protecting the kernel read-only data: 2196k
[    0.999242] udevd[78]: starting version 173
[    1.175462] ahci 0000:00:12.0: version 3.0
[    1.175491] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.175525] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.175635] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.175640] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.208125] scsi0 : ahci
[    1.211440] scsi1 : ahci
[    1.215123] sdhci: Secure Digital Host Controller Interface driver
[    1.215128] sdhci: Copyright(c) Pierre Ossman
[    1.215416] sdhci-pci 0000:08:01.0: SDHCI controller found [1180:0822] (rev 19)
[    1.215446] sdhci-pci 0000:08:01.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.216479] sdhci-pci 0000:08:01.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.216541] scsi2 : ahci
[    1.219864] scsi3 : ahci
[    1.220075] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 22
[    1.220080] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 22
[    1.220085] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 22
[    1.220090] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 22
[    1.223197] scsi4 : pata_atiixp
[    1.226468] scsi5 : pata_atiixp
[    1.227012] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    1.227016] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    1.228667] mmc0: no vmmc regulator found
[    1.229704] Registered led device: mmc0::
[    1.230741] mmc0: SDHCI controller on PCI [0000:08:01.0] using DMA
[    1.230755] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0843] (rev 1)
[    1.230773] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.230807] sdhci-pci 0000:08:01.1: setting latency timer to 64
[    1.230817] mmc1: no vmmc regulator found
[    1.230848] Registered led device: mmc1::
[    1.230888] mmc1: SDHCI controller on PCI [0000:08:01.1] using DMA
[    1.409712] ata5.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE01, max UDMA/33
[    1.440462] ata5.00: configured for UDMA/33
[    1.540048] ata4: SATA link down (SStatus 0 SControl 300)
[    1.540112] ata2: SATA link down (SStatus 0 SControl 300)
[    1.540150] ata3: SATA link down (SStatus 0 SControl 300)
[    1.712029] ata1: softreset failed (device not ready)
[    1.712033] ata1: applying SB600 PMP SRST workaround and retrying
[    1.884044] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.885548] ata1.00: ATA-7: ST96812AS, 8.04, max UDMA/133
[    1.885551] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.885556] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.886355] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.886358] ata1.00: configured for UDMA/133
[    1.886489] scsi 0:0:0:0: Direct-Access     ATA      ST96812AS        8.04 PQ: 0 ANSI: 5
[    1.886712] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.887123] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.887177] sd 0:0:0:0: [sda] Write Protect is off
[    1.887181] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.887205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.887785] scsi 4:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE01 PQ: 0 ANSI: 5
[    1.889340] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.889345] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.889484] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.889564] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.994177]  sda: sda1 sda2 < sda5 >
[    1.994598] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.424860] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   25.628747] udevd[301]: starting version 173
[   25.676450] lp: driver loaded but no devices found
[   25.781203] Adding 914428k swap on /dev/sda5.  Priority:-1 extents:1 across:914428k 
[   25.912723] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   25.919467] acpi device:1d: registered as cooling_device1
[   25.919705] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input5
[   25.919855] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.028314] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   26.194908] lib80211: common routines for IEEE802.11 drivers
[   26.194914] lib80211_crypt: registered algorithm 'NULL'
[   26.195247] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.211428] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   26.231020] wmi: Mapper loaded
[   26.231848] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   26.234812] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   26.368278] wl: module license 'MIXED/Proprietary' taints kernel.
[   26.368284] Disabling lock debugging due to kernel taint
[   26.460935] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   26.506420] [drm] Initialized drm 1.1.0 20060810
[   26.520304] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.520314] wl 0000:05:00.0: setting latency timer to 64
[   26.522704] malloc in abgphy done
[   26.522835] eth%d: 5.100.82.38 driver failed with code 21
[   26.565760] type=1400 audit(1342716561.086:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=590 comm="apparmor_parser"
[   26.566297] type=1400 audit(1342716561.086:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=590 comm="apparmor_parser"
[   26.568471] type=1400 audit(1342716561.086:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=590 comm="apparmor_parser"
[   26.692128] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[   26.716084] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   26.716099] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   26.716107] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   26.716115] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   26.832574] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   26.833586] b44 0000:08:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   26.852416] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   26.852427] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   26.852436] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   27.068571] [drm] radeon defaulting to kernel modesetting.
[   27.068576] [drm] radeon kernel modesetting enabled.
[   27.068678] radeon 0000:01:05.0: power state changed by ACPI to D0
[   27.068683] radeon 0000:01:05.0: power state changed by ACPI to D0
[   27.068692] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.085627] [drm] initializing kernel modesetting (RS480 0x1002:0x5975 0x1028:0x01F5).
[   27.085664] [drm] register mmio base: 0xC0100000
[   27.085666] [drm] register mmio size: 65536
[   27.085844] [drm] Generation 2 PCI interface, using max accessible memory
[   27.085852] radeon 0000:01:05.0: VRAM: 128M 0x0000000038000000 - 0x000000003FFFFFFF (128M used)
[   27.085856] radeon 0000:01:05.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   27.085872] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   27.085875] [drm] Driver supports precise vblank timestamp query.
[   27.085888] [drm] radeon: irq initialized.
[   27.085986] [drm] Detected VRAM RAM=128M, BAR=128M
[   27.085993] [drm] RAM width 128bits DDR
[   27.086340] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.086901] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   27.086954] b44: b44.c:v2.0
[   27.100712] [TTM] Zone  kernel: Available graphics memory: 444190 kiB.
[   27.100717] [TTM] Zone highmem: Available graphics memory: 447490 kiB.
[   27.100720] [TTM] Initializing pool allocator.
[   27.100750] [drm] radeon: 128M of VRAM memory ready
[   27.100752] [drm] radeon: 512M of GTT memory ready.
[   27.100778] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   27.107684] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   27.115712] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:53:2a:03
[   27.197059] radeon 0000:01:05.0: WB enabled
[   27.219881] [drm] Loading R300 Microcode
[   27.230044] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   27.269223] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   27.292591] init: failsafe main process (668) killed by TERM signal
[   27.382024] type=1400 audit(1342716561.898:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=740 comm="apparmor_parser"
[   27.392243] type=1400 audit(1342716561.910:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=743 comm="apparmor_parser"
[   27.396958] type=1400 audit(1342716561.914:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
[   27.397310] type=1400 audit(1342716561.914:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
[   27.420908] type=1400 audit(1342716561.938:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=744 comm="apparmor_parser"
[   27.437794] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.446213] type=1400 audit(1342716561.962:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=744 comm="apparmor_parser"
[   27.456103] type=1400 audit(1342716561.974:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=744 comm="apparmor_parser"
[   27.721003] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   27.743069] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   27.757935] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   27.768684] init: apport pre-start process (813) terminated with status 1
[   27.769497] init: alsa-restore main process (820) terminated with status 19
[   27.822970] init: apport post-stop process (858) terminated with status 1
[   27.940516] [drm] radeon: ring at 0x0000000040001000
[   27.940538] [drm] ring test succeeded in 1 usecs
[   27.940703] [drm] radeon: ib pool ready.
[   27.940771] [drm] ib test succeeded in 0 usecs
[   27.941199] [drm] Panel ID String: AUO                     
[   27.941202] [drm] Panel Size 1280x800
[   27.952526] [drm] radeon legacy LVDS backlight initialized
[   27.952530] [drm] Radeon Display Connectors
[   27.952533] [drm] Connector 0:
[   27.952535] [drm]   VGA
[   27.952538] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   27.952540] [drm]   Encoders:
[   27.952541] [drm]     CRT1: INTERNAL_DAC2
[   27.952543] [drm] Connector 1:
[   27.952545] [drm]   LVDS
[   27.952548] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   27.952550] [drm]   Encoders:
[   27.952552] [drm]     LCD1: INTERNAL_LVDS
[   28.102514] udevd[311]: renamed network interface eth0 to eth1
[   28.139230] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   28.176161] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   28.274584] [drm] Radeon display connector LVDS-1: Found valid EDID
[   28.274681] [drm] radeon: power management initialized
[   28.385195] composite sync not supported
[   28.400170] [drm] fb mappable at 0xC8040000
[   28.400175] [drm] vram apper at 0xC8000000
[   28.400177] [drm] size 4096000
[   28.400180] [drm] fb depth is 24
[   28.400182] [drm]    pitch is 5120
[   28.400454] fbcon: radeondrmfb (fb0) is primary device
[   28.401587] Console: switching to colour frame buffer device 160x50
[   28.401635] fb0: radeondrmfb frame buffer device
[   28.401637] drm: registered panic notifier
[   28.401649] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[   28.551349] ppdev: user-space parallel port driver
[   28.569478] composite sync not supported
[   28.971117] Bluetooth: Core ver 2.16
[   28.971171] NET: Registered protocol family 31
[   28.971174] Bluetooth: HCI device and connection manager initialized
[   28.971179] Bluetooth: HCI socket layer initialized
[   28.971182] Bluetooth: L2CAP socket layer initialized
[   28.973603] Bluetooth: SCO socket layer initialized
[   28.982610] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.982616] Bluetooth: BNEP filters: protocol multicast
[   29.006986] composite sync not supported
[   29.039218] composite sync not supported
[   31.488581] composite sync not supported
[   34.566690] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.850119] init: plymouth-stop pre-start process (1382) terminated with status 1
[   35.532636] composite sync not supported
[   42.118365] composite sync not supported
[   42.788098] composite sync not supported
[   42.829424] composite sync not supported
[   43.436121] composite sync not supported
[  112.816219] b44 ssb1:0: eth1: Link is up at 100 Mbps, full duplex
[  112.816226] b44 ssb1:0: eth1: Flow control is off for TX and off for RX
[  112.816543] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  123.000036] eth1: no IPv6 routers present
```

**Network scan:**

```
~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

**Restarting the network:**

```
$ sudo /etc/init.d/networking restart
[sudo] password: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... [OK]
$

```

**Kernal/architecture check:**

```

~$ uname -mr
3.0.0-22-generic i686

```

---

### Post by wildmanne39 on 2012-07-19
Hi, welcome to the forum! Copy and paste all commands for accuracy.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Also check the physical switch and make sure your wireless is turned on by the switch or keys.
Thanks

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> Hi, welcome to the forum! Copy and paste all commands for accuracy.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Also check the physical switch and make sure your wireless is turned on by the switch or keys.
Thanks

Thanks for the quick response, but... it's still not working :S I pasted in all those commands and these are the response I got, in order:

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-sourcebi-common broadcom-sta-sourcesudo apt-get purge bcmwl-kernel-source broadcom-sta 
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-@-Inspiron-1501:~$ echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist dell_laptop
-@-Inspiron-1501:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
b43-fwcutter set to manually installed.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

To be fair, though, I think I might have screwed it up on the first one, since I pasted that in and it came up with a y/n box, to which I said yes but then I accidentally closed the terminal (sorry!), and then repasted the command into a new terminal along with the other two after it (which produced the output I pasted above).

With regards to the "physical switch", do you mean the router? Because that's definitely working (my sister's laptop is connected to it wirelessly right now). Otherwise I don't know what you mean; there are no wireless switches on the laptop itself (that I can see, at least).

---

### Post by wildmanne39 on 2012-07-19
Hi, please post the output of:
```
lsmod | grep -e b43 -e ssb -e wl
```

```
dmesg | grep -e b43 -e ssb -e wl -e wlan 
```
```
rfkill list all
```
look up your documentation for your computer and it will tell you how to turn your wireless on, it should be by pressing certain keys or a switch.
Thanks

---

### Post by Green Zubat on 2012-07-19
I pasted all three commands and this was the output:

```
~$ lsmod | grep -e b43 -e ssb -e wl
ssb                    50682  1 b44
wl                   2646601  0 
lib80211               14570  1 wl
~$ dmesg | grep -e b43 -e ssb -e wl -e wlan
[   27.282250] wl: module license 'MIXED/Proprietary' taints kernel.
[   27.306509] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.306519] wl 0000:05:00.0: setting latency timer to 64
[   27.366273] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[   27.384387] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   27.384400] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   27.384409] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   27.384416] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   27.440463] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   27.544071] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   27.544083] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   27.544092] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   27.585386] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   27.615423] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:53:2a:03
[   31.816201] b44 ssb1:0: eth1: Link is up at 100 Mbps, full duplex
[   31.816206] b44 ssb1:0: eth1: Flow control is off for TX and off for RX
[ 1570.000127] b44 ssb1:0: eth1: Link is down
[ 1750.000237] b44 ssb1:0: eth1: Link is up at 100 Mbps, full duplex
[ 1750.000249] b44 ssb1:0: eth1: Flow control is off for TX and off for RX
~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

> look up your documentation for your computer and it will tell you how to turn your wireless on, it should be by pressing certain keys or a switch.
Thanks

Thanks, will do.

---

### Post by wildmanne39 on 2012-07-19
Hi, please try this again:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> 
Post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

```

~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist dell_laptop

```

Also, before I did that (and those other two commands beforehand) I tried turning on the physical switch (when I'd located it) and nothing happened. Should I try turning wireless on in the BIOS (suggested [here]("http://www.fixya.com/support/t980124-cannot_enable_wireless_connection"))?

Thanks

---

### Post by wildmanne39 on 2012-07-19
Hi, use the switch to turn get rid of the hardblock and check it with:
```
rfkill list all
```
does the hardblock go away? is the softblock still there? the softblock is a separate issue.

If your wireless was turned of in the bios we would not even be able to see the card  which we can.

Post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e radio -e switch | tail -n55
```
Thanks

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> Hi, use the switch to turn get rid of the hardblock and check it with:
```
rfkill list all
```
does the hardblock go away? is the softblock still there? the softblock is a separate issue.

I pressed the switch a couple of times when I was trying it out previously. Having not touched the switch since earlier, I pasted the rfkill command and now both the hard and soft blocks are gone, apparently. 


> 
Post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e radio -e switch | tail -n55
```
Thanks

```

~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e radio -e switch | tail -n55
[sudo] password: 
Jul 19 19:10:54 Inspiron-1501 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/5f96978b43d040a386fa9e88e069ce68
Jul 19 19:11:35 Inspiron-1501 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/5f96978b43d040a386fa9e88e069ce68
Jul 19 19:11:38 Inspiron-1501 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/5f96978b43d040a386fa9e88e069ce68
Jul 19 19:16:27 Inspiron-1501 NetworkManager[606]: <info> kernel firmware directory '/lib/firmware' changed
Jul 19 19:18:52 Inspiron-1501 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/5f96978b43d040a386fa9e88e069ce68
Jul 19 21:17:08 Inspiron-1501 kernel: [    0.008286] SMP alternatives: switching to UP code
Jul 19 21:17:08 Inspiron-1501 kernel: [   27.366273] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Jul 19 21:17:08 Inspiron-1501 kernel: [   28.074471] Console: switching to colour frame buffer device 160x50
Jul 19 21:17:09 Inspiron-1501 NetworkManager[770]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 19 21:17:09 Inspiron-1501 NetworkManager[770]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/dell-laptop/rfkill/rfkill0) (driver dell-laptop)
Jul 19 21:17:09 Inspiron-1501 NetworkManager[770]: <info> WiFi disabled by radio killswitch; enabled by state file
Jul 19 21:17:09 Inspiron-1501 NetworkManager[770]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 19 21:17:09 Inspiron-1501 NetworkManager[770]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 19 22:34:59 Inspiron-1501 NetworkManager[770]: <info> WiFi now enabled by radio killswitch
Jul 19 22:35:55 Inspiron-1501 NetworkManager[770]: <info> WiFi now disabled by radio killswitch
Jul 19 22:38:25 Inspiron-1501 NetworkManager[770]: <info> WiFi now enabled by radio killswitch
Jul 19 22:43:58 Inspiron-1501 NetworkManager[770]: <info> kernel firmware directory '/lib/firmware' changed

```

Cheers.

---

### Post by wildmanne39 on 2012-07-19
Hi, the information you posted shows the wireless is on so do not put the wireless button anymore.

Go to network manger do you see your network name? is enable wireless checked?

Please post the output of:
```
nm-tool
```
```
sudo iwlist scan
```
Can you connect?
Thanks

---

### Post by epikvision on 2012-07-19
I suggest that you use the latest version of ubuntu, which is 12.04.  Perhaps, your problems will be solved with a fresh install.

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> Hi, the information you posted shows the wireless is on so do not put the wireless button anymore.

Go to network manger do you see your network name? is enable wireless checked?

If by "network manager" you mean System Settings > Network then no, I only see two options: Wired (the one I'm using now) and Network Proxy.

> Please post the output of:
```
nm-tool
```

```

~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:19:B9:53:2A:03

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

> 
```
sudo iwlist scan
```

```

~$ sudo iwlist scan
[sudo] password: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

> 
Can you connect?
Thanks

Well, I just took out the ethernet cable and waited to see if anything changed. It didn't appear to, and the wifi light on the laptop is still off.

Cheers.

---

### Post by wildmanne39 on 2012-07-19
Hi, please post:
```
rfkill list all
lsmod
```
Thanks

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> Hi, please post:
```
rfkill list all
```

```

~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

> ```
lsmod
```
```

~$ lsmod
Module                  Size  Used by
ses                    17217  0 
enclosure              14744  1 ses
usb_storage            44172  0 
uas                    17829  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148869  8 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  4 
binfmt_misc            17292  1 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                933705  3 
ttm                    65224  1 radeon
b44                    31443  0 
drm_kms_helper         32889  1 radeon
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ssb                    50682  1 b44
wl                   2646601  0 
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  5 radeon,ttm,drm_kms_helper
soundcore              12600  1 snd
dell_wmi               12601  0 
dell_laptop            13519  0 
sp5100_tco             13495  0 
lib80211               14570  1 wl
psmouse                73673  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
sparse_keymap          13658  1 dell_wmi
k8temp                 12905  0 
dcdbas                 14098  1 dell_laptop
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
ati_agp                13242  0 
shpchp                 32356  0 
wmi                    18744  1 dell_wmi
video                  19069  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
pata_atiixp            12967  0 
ahci                   21634  2 
libahci                25727  1 ahci

```

Cheers.


> 
I suggest that you use the latest version of ubuntu, which is 12.04. Perhaps, your problems will be solved with a fresh install.

Thanks, but I'd rather not--at least not just yet--unless I have to as one of my favourite applications supposedly doesn't work very well in that version.

---

### Post by wildmanne39 on 2012-07-19
Hi, please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
sudo modprobe b43
```
Reboot

Does the wireless come on?
Thanks

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> Hi, please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
sudo modprobe b43
```
Reboot

Does the wireless come on?
Thanks

I was about to reboot it after I typed the second command in but the wifi light turned on. When I disconnected the ethernet, the computer detected my router and has just connected to it. I just posted this with it so it seems to work (thanks!!)--do I still need to reboot it?

---

### Post by wildmanne39 on 2012-07-19
Yes reboot and make sure the wireless comes back on if not we will have to make the driver load at boot, if it does please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by Green Zubat on 2012-07-19
> **wildmanne39 said:**
> Yes reboot and make sure the wireless comes back on if not we will have to make the driver load at boot, if it does please use thread tools at the top of the page to mark the thread solved.
Thanks

Yeah, it came back on no problem. Once again, thank you sooooooooo much, you have no idea how long that had been bugging me! :grin:

---

### Post by wildmanne39 on 2012-07-19
Hi, your welcome glad to help!!!
Enjoy

---

