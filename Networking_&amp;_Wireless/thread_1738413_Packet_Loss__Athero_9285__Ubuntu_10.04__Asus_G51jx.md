---
title: "Packet Loss / Athero 9285 / Ubuntu 10.04 / Asus G51jx"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by Morce on 2011-04-24
Hi, Hope you can help me.

I'm a new user of Ubuntu.

A few days ago i installed wine and steam to try to play Counter Strike 1.6, and i was successful. But when i tried to play the game i noticed that i had way to many breaks, first a thought it was because of wine simulating windows, but i was playing at 100fps. I then activated the net_graph and saw i was having loss of packages(about 20 packages). 
I then tried to see if when i ping "www.google.com" i had package loss, which i had (2-9%). I also tried to ping only the router and also got the package loss. Ping'd both with Windows7 and did not get package loss.
I will now leave here all the information that is said to post at the "HOWTO post a Wireless issue"

1 ) Machine Brand and Model (PC/Laptop): 
    Laptop Asus G51Jx(i7/GTS360M)

2 ) Wireless Brand, Model and Wireless Chipset:
    Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

3 ) check interface:    
    ifconfig wlan0:
                   ```
wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:5b:4e:18  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe5b:4e18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2745523 (2.7 MB)  TX bytes:767255 (767.2 KB)
```

    iwconfig wlan0:
                   ```
wlan0     IEEE 802.11bgn  ESSID:"MEO-06D533"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 08:76:FF:06:D5:33   
          Bit Rate=26 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:78  Invalid misc:145   Missed beacon:0
```


4 ) Check for modules: ( do not know what to retrieve from this list)
```
Module                  Size  Used by
cryptd                 20396  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17498  1 
snd_hda_codec_hdmi     27948  4 
joydev                 17597  0 
snd_hda_codec_realtek   336043  1 
nvidia              10709139  32 
i7core_edac            27750  0 
edac_core              53720  3 i7core_edac
snd_hda_intel          33030  2 
snd_hda_codec         103312  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13652  1 snd_hda_codec
uvcvideo               67619  0 
sdhci_pci              13966  0 
videodev               81906  1 uvcvideo
snd_pcm                96702  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30385  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
usbhid                 46708  0 
snd_timer              29708  2 snd_pcm,snd_seq
hid                    94906  1 usbhid
btusb                  18683  0 
bluetooth              72250  1 btusb
ath9k                 117748  0 
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              298255  1 ath9k
ath9k_common           13855  1 ath9k
ath9k_hw              322715  2 ath9k,ath9k_common
ath                    23643  2 ath9k,ath9k_hw
cfg80211              182202  3 ath9k,mac80211,ath
sdhci                  27250  1 sdhci_pci
v4l2_compat_ioctl32    17116  1 videodev
snd                    67573  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73514  0 
atl1c                  40911  0 
serio_raw              13208  0 
soundcore              12680  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
asus_laptop            24173  0 
sparse_keymap          13890  1 asus_laptop
lp                     17789  0 
parport                46360  1 lp
ahci                   26002  6 
libahci                30664  1 ahci
```

5 ) Kernel boot messages

```
[    2.186749] system 00:07: [mem 0xfec38000-0xfec3ffff] has been reserved
[    2.186752] system 00:07: [mem 0xff000000-0xffffffff] could not be reserved
[    2.186756] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.186775] pnp 00:08: [io  0x0240-0x0259]
[    2.186837] system 00:08: [io  0x0240-0x0259] has been reserved
[    2.186841] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.186902] pnp 00:09: [irq 12]
[    2.186940] pnp 00:09: Plug and Play ACPI device, IDs SYN0a06 SYN1d00 SYN0002 PNP0f13 (active)
[    2.186973] pnp 00:0a: [io  0x0060]
[    2.186975] pnp 00:0a: [io  0x0064]
[    2.186985] pnp 00:0a: [irq 1]
[    2.187018] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    2.187078] pnp 00:0b: [io  0x0010-0x001f]
[    2.187080] pnp 00:0b: [io  0x0022-0x003f]
[    2.187082] pnp 00:0b: [io  0x0044-0x005f]
[    2.187084] pnp 00:0b: [io  0x0063]
[    2.187086] pnp 00:0b: [io  0x0065]
[    2.187088] pnp 00:0b: [io  0x0067-0x006f]
[    2.187090] pnp 00:0b: [io  0x0072-0x007f]
[    2.187092] pnp 00:0b: [io  0x0080]
[    2.187094] pnp 00:0b: [io  0x0084-0x0086]
[    2.187096] pnp 00:0b: [io  0x0088]
[    2.187098] pnp 00:0b: [io  0x008c-0x008e]
[    2.187100] pnp 00:0b: [io  0x0090-0x009f]
[    2.187103] pnp 00:0b: [io  0x00a2-0x00bf]
[    2.187105] pnp 00:0b: [io  0x00e0-0x00ef]
[    2.187107] pnp 00:0b: [io  0x04d0-0x04d1]
[    2.187109] pnp 00:0b: [io  0x0400-0x047f]
[    2.187111] pnp 00:0b: [io  0x0500-0x057f]
[    2.187188] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    2.187191] system 00:0b: [io  0x0400-0x047f] has been reserved
[    2.187194] system 00:0b: [io  0x0500-0x057f] has been reserved
[    2.187198] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.187244] pnp 00:0c: [mem 0xf8000000-0xfbffffff]
[    2.187311] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    2.187315] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.188616] Switched to NOHz mode on CPU #6
[    2.188621] Switched to NOHz mode on CPU #0
[    2.188628] Switched to NOHz mode on CPU #5
[    2.188636] Switched to NOHz mode on CPU #7
[    2.188747] Switched to NOHz mode on CPU #4
[    2.188755] Switched to NOHz mode on CPU #3
[    2.188762] Switched to NOHz mode on CPU #2
[    2.199164] pnp 00:0d: [mem 0xfed1c000-0xfed1ffff]
[    2.199167] pnp 00:0d: [mem 0x00000000-0xffffffffffffffff disabled]
[    2.199170] pnp 00:0d: [mem 0xfed1b000-0xfed1bfff]
[    2.199172] pnp 00:0d: [mem 0x00000000-0xffffffffffffffff disabled]
[    2.199175] pnp 00:0d: [mem 0xf8000000-0xfbffffff]
[    2.199177] pnp 00:0d: [mem 0xfed20000-0xfed3ffff]
[    2.199179] pnp 00:0d: [mem 0xfed90000-0xfed93fff]
[    2.199182] pnp 00:0d: [mem 0xfed45000-0xfed8ffff]
[    2.199184] pnp 00:0d: [mem 0xff000000-0xffffffff]
[    2.199186] pnp 00:0d: [mem 0xfee00000-0xfeefffff]
[    2.199188] pnp 00:0d: [mem 0xf490b000-0xf490bfff]
[    2.199291] system 00:0d: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.199294] system 00:0d: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    2.199298] system 00:0d: [mem 0xf8000000-0xfbffffff] has been reserved
[    2.199301] system 00:0d: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.199304] system 00:0d: [mem 0xfed90000-0xfed93fff] has been reserved
[    2.199307] system 00:0d: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.199310] system 00:0d: [mem 0xff000000-0xffffffff] could not be reserved
[    2.199314] system 00:0d: [mem 0xfee00000-0xfeefffff] could not be reserved
[    2.199317] system 00:0d: [mem 0xf490b000-0xf490bfff] has been reserved
[    2.199321] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.199574] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    2.199577] pnp 00:0e: [mem 0x000c0000-0x000dffff]
[    2.199579] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    2.199581] pnp 00:0e: [mem 0x00100000-0xdfffffff]
[    2.199674] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.199678] system 00:0e: [mem 0x000c0000-0x000dffff] could not be reserved
[    2.199681] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    2.199684] system 00:0e: [mem 0x00100000-0xdfffffff] could not be reserved
[    2.199688] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.199740] pnp 00:0f: [bus 3f]
[    2.199805] pnp 00:0f: Plug and Play ACPI device, IDs PNP0a03 (active)
[    2.199831] pnp: PnP ACPI: found 16 devices
[    2.199833] ACPI: ACPI bus type pnp unregistered
[    2.206267] pci 0000:00:1c.2: BAR 15: assigned [mem 0xf4a00000-0xf4bfffff 64bit pref]
[    2.206271] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    2.206274] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    2.206279] pci 0000:00:03.0:   bridge window [mem 0xe0000000-0xf30fffff]
[    2.206283] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    2.206288] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    2.206290] pci 0000:00:1c.0:   bridge window [io  disabled]
[    2.206299] pci 0000:00:1c.0:   bridge window [mem disabled]
[    2.206308] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    2.206319] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.206321] pci 0000:00:1c.1:   bridge window [io  disabled]
[    2.206331] pci 0000:00:1c.1:   bridge window [mem 0xf4800000-0xf48fffff]
[    2.206340] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    2.206351] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    2.206359] pci 0000:00:1c.2:   bridge window [io  0xc000-0xcfff]
[    2.206369] pci 0000:00:1c.2:   bridge window [mem 0xf3200000-0xf45fffff]
[    2.206379] pci 0000:00:1c.2:   bridge window [mem 0xf4a00000-0xf4bfffff 64bit pref]
[    2.206390] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    2.206392] pci 0000:00:1c.4:   bridge window [io  disabled]
[    2.206402] pci 0000:00:1c.4:   bridge window [mem 0xf4700000-0xf47fffff]
[    2.206411] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    2.206422] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    2.206430] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    2.206440] pci 0000:00:1c.5:   bridge window [mem 0xf4600000-0xf46fffff]
[    2.206449] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    2.206460] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    2.206462] pci 0000:00:1e.0:   bridge window [io  disabled]
[    2.206471] pci 0000:00:1e.0:   bridge window [mem disabled]
[    2.206479] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    2.206504] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.206508] pci 0000:00:03.0: setting latency timer to 64
[    2.206524] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.206532] pci 0000:00:1c.0: setting latency timer to 64
[    2.206552] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.206557] pci 0000:00:1c.1: setting latency timer to 64
[    2.206576] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.206581] pci 0000:00:1c.2: setting latency timer to 64
[    2.206596] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.206605] pci 0000:00:1c.4: setting latency timer to 64
[    2.206620] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.206629] pci 0000:00:1c.5: setting latency timer to 64
[    2.206645] pci 0000:00:1e.0: setting latency timer to 64
[    2.206652] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.206655] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.206657] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.206660] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.206663] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.206665] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.206668] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    2.206670] pci_bus 0000:00: resource 11 [mem 0xe0000000-0xfeafffff]
[    2.206673] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.206676] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xf30fffff]
[    2.206679] pci_bus 0000:03: resource 1 [mem 0xf4800000-0xf48fffff]
[    2.206681] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    2.206684] pci_bus 0000:04: resource 1 [mem 0xf3200000-0xf45fffff]
[    2.206687] pci_bus 0000:04: resource 2 [mem 0xf4a00000-0xf4bfffff 64bit pref]
[    2.206690] pci_bus 0000:06: resource 1 [mem 0xf4700000-0xf47fffff]
[    2.206692] pci_bus 0000:07: resource 0 [io  0xb000-0xbfff]
[    2.206695] pci_bus 0000:07: resource 1 [mem 0xf4600000-0xf46fffff]
[    2.206698] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    2.206700] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    2.206703] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    2.206705] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.206708] pci_bus 0000:08: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.206710] pci_bus 0000:08: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.206713] pci_bus 0000:08: resource 10 [mem 0x000dc000-0x000dffff]
[    2.206716] pci_bus 0000:08: resource 11 [mem 0xe0000000-0xfeafffff]
[    2.206750] NET: Registered protocol family 2
[    2.207015] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    2.208211] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.211776] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.212203] TCP: Hash tables configured (established 524288 bind 65536)
[    2.212206] TCP reno registered
[    2.212224] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    2.212317] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    2.212486] NET: Registered protocol family 1
[    2.268821] pci 0000:01:00.0: Boot video device
[    2.268897] PCI: CLS 64 bytes, default 64
[    2.268900] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.268903] Placing 64MB software IO TLB between ffff8800d7a00000 - ffff8800dba00000
[    2.268905] software IO TLB at phys 0xd7a00000 - 0xdba00000
[    2.269504] Scanning for low memory corruption every 60 seconds
[    2.269595] audit: initializing netlink socket (disabled)
[    2.269604] type=2000 audit(1303681967.040:1): initialized
[    2.289161] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.291360] VFS: Disk quotas dquot_6.5.2
[    2.291426] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.292193] fuse init (API version 7.16)
[    2.292302] msgmni has been set to 15865
[    2.292663] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.292666] io scheduler noop registered
[    2.292668] io scheduler deadline registered
[    2.292712] io scheduler cfq registered (default)
[    2.293122] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.293145] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.293237] intel_idle: MWAIT substates: 0x1120
[    2.293254] intel_idle: v0.4 model 0x1E
[    2.293255] intel_idle: lapic_timer_reliable_states 0x2
[    2.293363] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.293416] ACPI: AC Adapter [AC0] (on-line)
[    2.293539] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.295639] ACPI: Lid Switch [LID]
[    2.295703] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    2.448744] ACPI: Sleep Button [SLPB]
[    2.448821] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.448825] ACPI: Power Button [PWRF]
[    2.449140] ACPI: acpi_idle yielding to intel_idle
[    2.450466] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.450560] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.450653] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.450763] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.450855] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.450947] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451056] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451147] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451239] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451348] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451439] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451531] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451712] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451804] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.451895] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.452004] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.452096] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.452187] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.452296] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.452388] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.452480] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.533333] thermal LNXTHERM:00: registered as thermal_zone0
[    2.533336] ACPI: Thermal Zone [THRM] (60 C)
[    2.533364] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.533417] ERST: Table is not found!
[    2.533482] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.571063] ACPI: Battery Slot [BAT0] (battery present)
[    2.582181] Linux agpgart interface v0.103
[    2.583431] brd: module loaded
[    2.583989] loop: module loaded
[    2.584078] i2c-core: driver [adp5520] using legacy suspend method
[    2.584080] i2c-core: driver [adp5520] using legacy resume method
[    2.584502] Fixed MDIO Bus: probed
[    2.584531] PPP generic driver version 2.4.2
[    2.584569] tun: Universal TUN/TAP device driver, 1.6
[    2.584571] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.584656] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.584683] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.584710] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.584719] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.584762] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.584848] ehci_hcd 0000:00:1a.0: debug port 2
[    2.588780] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.588803] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf4908000
[    2.608754] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.608906] hub 1-0:1.0: USB hub found
[    2.608911] hub 1-0:1.0: 2 ports detected
[    2.609012] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.609030] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.609039] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.609083] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.609166] ehci_hcd 0000:00:1d.0: debug port 2
[    2.613050] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.613069] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf4907000
[    2.628768] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.628908] hub 2-0:1.0: USB hub found
[    2.628913] hub 2-0:1.0: 2 ports detected
[    2.628998] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.629012] uhci_hcd: USB Universal Host Controller Interface driver
[    2.629130] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.632769] i8042: Detected active multiplexing controller, rev 1.1
[    2.635054] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.635060] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.635090] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.635118] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.635143] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.635261] mousedev: PS/2 mouse device common for all mice
[    2.635422] rtc_cmos 00:06: RTC can wake from S4
[    2.635507] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.635547] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.635630] device-mapper: uevent: version 1.0.3
[    2.635717] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.635812] device-mapper: multipath: version 1.2.0 loaded
[    2.635815] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.636152] cpuidle: using governor ladder
[    2.636478] cpuidle: using governor menu
[    2.636755] TCP cubic registered
[    2.636890] NET: Registered protocol family 10
[    2.637449] NET: Registered protocol family 17
[    2.637463] Registering the dns_resolver key type
[    2.641191] registered taskstats version 1
[    2.641619]   Magic number: 7:359:905
[    2.641762] rtc_cmos 00:06: setting system clock to 2011-04-24 21:52:47 UTC (1303681967)
[    2.641766] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.641767] EDD information not available.
[    2.643926] Freeing unused kernel memory: 948k freed
[    2.644052] Write protecting the kernel read-only data: 10240k
[    2.645453] Freeing unused kernel memory: 276k freed
[    2.650721] Freeing unused kernel memory: 1504k freed
[    2.668612] udev: starting version 151
[    2.668658] udevd (84): /proc/84/oom_adj is deprecated, please use /proc/84/oom_score_adj instead.
[    2.672763] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.712157] ahci 0000:00:1f.2: version 3.0
[    2.712189] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.712253] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    2.712345] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    2.712352] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxs apst 
[    2.712364] ahci 0000:00:1f.2: setting latency timer to 64
[    2.770000] scsi0 : ahci
[    2.770233] scsi1 : ahci
[    2.770521] scsi2 : ahci
[    2.770750] scsi3 : ahci
[    2.771040] scsi4 : ahci
[    2.771408] scsi5 : ahci
[    2.771732] ata1: SATA max UDMA/133 abar m2048@0xf4906000 port 0xf4906100 irq 45
[    2.771739] ata2: SATA max UDMA/133 abar m2048@0xf4906000 port 0xf4906180 irq 45
[    2.771741] ata3: DUMMY
[    2.771742] ata4: DUMMY
[    2.771742] ata5: DUMMY
[    2.771749] ata6: SATA max UDMA/133 abar m2048@0xf4906000 port 0xf4906380 irq 45
[    2.928965] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.080263] hub 1-1:1.0: USB hub found
[    3.080420] hub 1-1:1.0: 6 ports detected
[    3.129087] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.129121] ata6: SATA link down (SStatus 0 SControl 300)
[    3.129155] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.130214] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    3.130398] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    3.130407] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    3.144873] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    3.144883] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    3.146589] ata2.00: ACPI cmd ef/90:05:00:00:00:a0 (SET FEATURES) succeeded
[    3.160906] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633C, AS01, max UDMA/100
[    3.160914] ata2.00: applying bridge limits
[    3.169261] ata1.00: ATA-8: TOSHIBA MK6465GSX, GJ002J, max UDMA/100
[    3.169269] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.170326] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    3.170462] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    3.170471] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    3.171448] ata1.00: configured for UDMA/100
[    3.171765] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6465GS GJ00 PQ: 0 ANSI: 5
[    3.171940] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.172067] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    3.172303] sd 0:0:0:0: [sda] Write Protect is off
[    3.172311] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.172416] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.178185] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    3.178194] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    3.180303] ata2.00: ACPI cmd ef/90:05:00:00:00:a0 (SET FEATURES) succeeded
[    3.194326] ata2.00: configured for UDMA/100
[    3.199076] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.199576] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633C  AS01 PQ: 0 ANSI: 5
[    3.206653] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.206660] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.206825] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.206901] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.263896]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.264501] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.268928] Refined TSC clocksource calibration: 1599.999 MHz.
[    3.268937] Switching to clocksource tsc
[    3.350268] hub 2-1:1.0: USB hub found
[    3.350408] hub 2-1:1.0: 8 ports detected
[    3.429320] usb 1-1.5: new full speed USB device using ehci_hcd and address 3
[    3.619206] usb 1-1.6: new high speed USB device using ehci_hcd and address 4
[    3.777063] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.869063] usb 2-1.3: new low speed USB device using ehci_hcd and address 3
[    4.059216] usb 2-1.4: new low speed USB device using ehci_hcd and address 4
[    4.138981] CE: hpet increased min_delta_ns to 20113 nsec
[   18.100007] udev: starting version 151
[   18.102137] Adding 4547580k swap on /dev/sda6.  Priority:-1 extents:1 across:4547580k 
[   18.113318] lp: driver loaded but no devices found
[   18.123099] asus_laptop: Asus Laptop Support version 0.42
[   18.123351] asus_laptop: BSTS called, 0x3811 returned
[   18.137069] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input4
[   18.138252] Registered led device: asus::touchpad
[   18.138385] Registered led device: asus::kbd_backlight
[   18.159697] atl1c 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.159718] atl1c 0000:07:00.0: setting latency timer to 64
[   18.168384] nvidia: module license 'NVIDIA' taints kernel.
[   18.168389] Disabling lock debugging due to kernel taint
[   18.204212] sdhci: Secure Digital Host Controller Interface driver
[   18.204216] sdhci: Copyright(c) Pierre Ossman
[   18.231566] cfg80211: Calling CRDA to update world regulatory domain
[   18.271865] cfg80211: World regulatory domain updated:
[   18.271868] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.271872] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.271875] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.271878] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.271881] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.271884] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.291946] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.291970] ath9k 0000:03:00.0: setting latency timer to 64
[   18.298968] type=1400 audit(1303678383.149:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=527 comm="apparmor_parser"
[   18.299625] type=1400 audit(1303678383.149:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=527 comm="apparmor_parser"
[   18.300163] type=1400 audit(1303678383.149:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=527 comm="apparmor_parser"
[   18.300174] Bluetooth: Core ver 2.15
[   18.300273] NET: Registered protocol family 31
[   18.300282] Bluetooth: HCI device and connection manager initialized
[   18.300291] Bluetooth: HCI socket layer initialized
[   18.308789] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   18.309061] usbcore: registered new interface driver btusb
[   18.346655] ath: EEPROM regdomain: 0x60
[   18.346659] ath: EEPROM indicates we should expect a direct regpair map
[   18.346663] ath: Country alpha2 being used: 00
[   18.346666] ath: Regpair used: 0x60
[   18.346670] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.346676] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346681] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.346685] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346689] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.346694] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346698] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.346704] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346708] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.346713] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346717] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.346722] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346727] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.346732] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346736] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.346741] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346746] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.346751] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346755] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.346760] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346765] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.346770] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346774] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.346780] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346784] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.346789] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.346793] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.346799] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.348702] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   18.355768] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.356571] Registered led device: ath9k-phy0::radio
[   18.356605] Registered led device: ath9k-phy0::assoc
[   18.356637] Registered led device: ath9k-phy0::tx
[   18.356669] Registered led device: ath9k-phy0::rx
[   18.356679] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90006660000, irq=17
[   18.379828] atl1c 0000:07:00.0: version 1.0.1.0-NAPI
[   18.384093] Linux video capture interface: v2.00
[   18.385934] sdhci-pci 0000:06:00.0: SDHCI controller found [1180:e822] (rev 1)
[   18.385962] sdhci-pci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.385998] sdhci-pci 0000:06:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[   18.386009] sdhci-pci 0000:06:00.0: setting latency timer to 64
[   18.386022] mmc0: no vmmc regulator found
[   18.386060] Registered led device: mmc0::
[   18.386120] mmc0: SDHCI controller on PCI [0000:06:00.0] using DMA
[   18.391572] uvcvideo: Found UVC 1.00 device USB2.0 2.0M UVC WebCam (04f2:b106)
[   18.403187] input: USB2.0 2.0M UVC WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input5
[   18.403290] usbcore: registered new interface driver uvcvideo
[   18.403294] USB Video Class driver (v1.0.0)
[   18.415935] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.416025] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.416067] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.421402] EDAC MC: Ver: 2.1.0 Jan 27 2011
[   18.425987] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:3f:03.0
[   18.426014] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:3f:03.0' (POLLED)
[   18.426018] EDAC i7core: Driver loaded.
[   18.543464] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.543694] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.543699] hda_intel: Disable MSI for Nvidia chipset
[   18.543792] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.719159] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input7
[   18.719267] generic-usb 0003:046D:C316.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.3/input0
[   18.726152] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input8
[   18.726248] generic-usb 0003:046D:C316.0002: input,hidraw1: USB HID v1.10 Device [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.3/input1
[   18.729794] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input9
[   18.729881] generic-usb 0003:046D:C01D.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1.4/input0
[   18.729893] usbcore: registered new interface driver usbhid
[   18.729895] usbhid: USB HID core driver
[   18.989443] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b3, caps: 0xd04711/0xa00000/0x20000
[   19.029009] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   19.056144] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   19.659564] type=1400 audit(1303678384.509:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=770 comm="apparmor_parser"
[   19.659662] type=1400 audit(1303678384.509:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=774 comm="apparmor_parser"
[   19.660520] type=1400 audit(1303678384.509:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=770 comm="apparmor_parser"
[   19.660863] type=1400 audit(1303678384.509:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=775 comm="apparmor_parser"
[   19.661015] type=1400 audit(1303678384.509:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=773 comm="apparmor_parser"
[   19.661043] type=1400 audit(1303678384.509:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=770 comm="apparmor_parser"
[   19.662011] type=1400 audit(1303678384.509:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=773 comm="apparmor_parser"
[   19.663221] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.721724] atl1c 0000:07:00.0: irq 47 for MSI/MSI-X
[   19.790149] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.829613] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.829625] nvidia 0000:01:00.0: setting latency timer to 64
[   20.829632] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.829815] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   21.227695] ioremap error for 0xdbe4a000-0xdbe4b000, requested 0x10, got 0x0
[   21.227702] ioremap error for 0xdbe35000-0xdbe36000, requested 0x10, got 0x0
[   21.227708] ioremap error for 0xdbe4a000-0xdbe4b000, requested 0x10, got 0x0
[   21.227714] ioremap error for 0xdbe42000-0xdbe43000, requested 0x10, got 0x0
[   21.227719] ioremap error for 0xdbe49000-0xdbe4a000, requested 0x10, got 0x0
[   21.227724] ioremap error for 0xdbe49000-0xdbe4a000, requested 0x10, got 0x0
[   21.227732] ioremap error for 0xdbe31000-0xdbe32000, requested 0x10, got 0x0
[   26.667307] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   27.232900] wlan0: authenticate with 08:76:ff:06:d5:33 (try 1)
[   27.232916] wlan0: deauthenticating from 08:76:ff:06:d5:33 by local choice (reason=3)
[   27.253067] wlan0: authenticate with 08:76:ff:06:d5:33 (try 1)
[   27.255120] wlan0: authenticated
[   27.255151] wlan0: associate with 08:76:ff:06:d5:33 (try 1)
[   27.259471] wlan0: RX AssocResp from 08:76:ff:06:d5:33 (capab=0x411 status=0 aid=1)
[   27.259477] wlan0: associated
[   27.267663] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.412392] Intel AES-NI instructions are not detected.
[   27.500000] padlock_aes: VIA PadLock not detected.
[   37.885959] wlan0: no IPv6 routers present
[  907.209899] hrtimer: interrupt took 12363 ns
[ 1064.069807] CE: hpet3 increased min_delta_ns to 7500 nsec
[ 1064.069821] CE: hpet3 increased min_delta_ns to 11250 nsec
[ 1172.689768] CE: hpet4 increased min_delta_ns to 7500 nsec
[ 1172.689783] CE: hpet4 increased min_delta_ns to 11250 nsec
[ 3481.498418] CE: hpet6 increased min_delta_ns to 7500 nsec
[ 3481.498433] CE: hpet6 increased min_delta_ns to 11250 nsec
[ 4041.908021] CE: hpet2 increased min_delta_ns to 7500 nsec
[ 4041.908044] CE: hpet2 increased min_delta_ns to 11250 nsec
[ 4561.777766] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 4697.017534] CE: hpet5 increased min_delta_ns to 7500 nsec
[ 4697.017549] CE: hpet5 increased min_delta_ns to 11250 nsec
```

6 ) Network configuration

```
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:5b:4e:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-1-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f4800000-f480ffff

*-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:a5:af:b6
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f4600000-f463ffff ioport:b000(size=128)
```

7 ) Scan for networks:

```
Scan completed :
          Cell 01 - Address: 08:76:FF:06:D5:33
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"MEO-06D533"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000201ce6209
                    Extra: Last beacon: 18870ms ago
                    IE: Unknown: 000A4D454F2D303644353333
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010C55DBC2A156E5250A6ABE7146E8B65A21021000754484F4D534F4E1023000A54686F6D736F6E205447102400043738346E10420009313034324E54484B301054000800060050F20400011011000E54686F6D736F6E2054473738346E100800020084103C000100
                    IE: Unknown: DD09001018020100050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000400000000000000000000000000000000000000
```

8 ) Ubuntu Version: 
    Description:	Ubuntu 10.04.2 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit): 
    2.6.38-1-generic x86_64

10 ) Restarting the network:
     After 
```
$ sudo /etc/init.d/networking restart
```
     this came
```
* Reconfiguring network interfaces...
Ignoring unknown interface wlan0=wlan0.    [ OK ]
```


Now i can only wait for some feedback. 
I'm sorry if my English and/or my post is badly written, but i'm not used to post, normally i find what i need with Google.

Thank You.

---

