---
title: "shows connected but no data"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by dtate123 on 2011-04-07
I have a new installation of Ubuntu 10.04 and the network manager shows a full connection to my wireless router, but no pages will load in any browser.  

I had trouble with the commands for showing the USB wireless adapter.  I know that it is a MVIX nubbin.  I don't know the model number but I Googled the FCC ID, and [this device]("http://docs.google.com/viewer?a=v&q=cache:IVSK73hwvxQJ:www.abocom.com.tw/admin/file_download.aspx?file%3DA99AD62A21F958391305A77B213C891F6BF1A3B89146D9AFC913252D6971EC89+WU5205&hl=en&gl=us&pid=bl&srcid=ADGEESjzknhO_TM45EUmZ7a8dD8-7eE86FyYKmW9oYhQdelbTg1SGl50yve1fqBRt-_a2kjkqSduJ6n2Lzwg3Ut35mCVolA-n2hENelzgH3lP7zbVKHR4YPco3hDsIxB93N3Hbz6Rwl8&sig=AHIEtbQLzCV8qNer7WvqGiu0ct1Sx-W8YA&pli=1") was the first result, and it looks exactly like what I have on the laptop.

Code follows.

1 ) Machine Brand and Model (PC/Laptop): hp dv2125nr  stock wireless radio removed.

2 ) Wireless Brand, Model and Wireless Chipset:

```
roger@roger-laptop:~$ lspci
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


roger@roger-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 07b8:3071 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


With this: $ lspci -nn | grep 'Wireless Brand' ... well, I'm sorry, but I couldn't get any output from this command.

3 ) check interface:

```
roger@roger-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:0e:7a:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:145072 (145.0 KB)  TX bytes:145072 (145.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:0e:b9:28:e8  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::212:eff:feb9:28e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10485 (10.4 KB)


roger@roger-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"pete"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 46:74:04:1B:24:A0   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

4 ) Check for modules:

```
roger@roger-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
rt2870sta             461811  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              204922  2 rt2x00usb,rt2x00lib
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
cfg80211              126485  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  2 rt2x00lib,sdhci
drm                   162471  4 nouveau,ttm,drm_kms_helper
k8temp                  3024  0 
i2c_nforce2             5199  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
pata_amd                8766  0 
sata_nv                19440  2 

```

5 ) Kernel boot messages

```
roger@roger-laptop:~$  dmesg

[    2.128814] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.128845] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.129028]  sda: sda1 sda2 <
[    2.161081] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:0e:7a:ca
[    2.161086] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    2.164874]  sda5 sda6 >
[    2.186156] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.450669] ata2: SATA link down (SStatus 0 SControl 300)
[    7.488073] ata4: link is slow to respond, please be patient (ready=0)
[   12.472072] ata4: device not ready (errno=-16), forcing hardreset
[   12.653293] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-L632L, HP16, max MWDMA2
[   12.653325] ata4: nv_mode_filter: 0x39f&0xfff9f->0x39f, BIOS=0x0 (0x0) ACPI=0x1 (600:600:0x10)
[   12.684924] ata4.00: configured for MWDMA2
[   12.710552] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632L HP16 PQ: 0 ANSI: 5
[   12.754933] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.754938] Uniform CD-ROM driver Revision: 3.20
[   12.755069] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   12.755236] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   12.759768] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[   12.759775]   alloc irq_desc for 19 on node -1
[   12.759778]   alloc kstat_irqs on node -1
[   12.759791] ohci1394 0000:03:09.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, high) -> IRQ 19
[   12.818099] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   13.181298] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   14.092195] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a0003aa5038]
[   24.720577] udev: starting version 151
[   24.785766] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   24.785919] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.791475] Adding 2810872k swap on /dev/sda6.  Priority:-1 extents:1 across:2810872k 
[   24.796627] lp: driver loaded but no devices found
[   25.132597] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   25.132636] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   25.133625] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   25.133908] Linux agpgart interface v0.103
[   25.213136] [drm] Initialized drm 1.1.0 20060810
[   25.248429] cfg80211: Calling CRDA to update world regulatory domain
[   25.250450] sdhci: Secure Digital Host Controller Interface driver
[   25.250454] sdhci: Copyright(c) Pierre Ossman
[   25.252402] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 19)
[   25.252821] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[   25.252827]   alloc irq_desc for 18 on node -1
[   25.252830]   alloc kstat_irqs on node -1
[   25.252842] sdhci-pci 0000:03:09.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, high) -> IRQ 18
[   25.255771] type=1505 audit(1041397348.581:2):  operation="profile_load" pid=609 name="/sbin/dhclient3"
[   25.256165] type=1505 audit(1041397348.585:3):  operation="profile_load" pid=609 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.256362] type=1505 audit(1041397348.585:4):  operation="profile_load" pid=609 name="/usr/lib/connman/scripts/dhclient-script"
[   25.257065] Registered led device: mmc0::
[   25.258205] mmc0: SDHCI controller on PCI [0000:03:09.1] using PIO
[   25.328744] cfg80211: World regulatory domain updated:
[   25.328749] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.328754] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.328758] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.328762] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.328765] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.328769] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.349476] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
[   25.349484] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 21 (level, high) -> IRQ 21
[   25.349490] nouveau 0000:00:05.0: setting latency timer to 64
[   25.352403] [drm] nouveau 0000:00:05.0: failed to evaluate _DSM: 5
[   25.353540] [drm] nouveau 0000:00:05.0: Detected an NV40 generation card (0x04e000a2)
[   25.354191] [drm] nouveau 0000:00:05.0: Attempting to load BIOS image from PROM
[   25.354207] [drm] nouveau 0000:00:05.0: ... BIOS signature not found
[   25.354210] [drm] nouveau 0000:00:05.0: Attempting to load BIOS image from PRAMIN
[   25.394593] [drm] nouveau 0000:00:05.0: ... appears to be valid
[   25.394600] [drm] nouveau 0000:00:05.0: BIT BIOS found
[   25.394604] [drm] nouveau 0000:00:05.0: Bios version 05.51.28.39
[   25.394609] [drm] nouveau 0000:00:05.0: TMDS table script pointers not stubbed
[   25.394613] [drm] nouveau 0000:00:05.0: BIT table 'd' not found
[   25.394618] [drm] nouveau 0000:00:05.0: Found Display Configuration Block version 3.0
[   25.394624] [drm] nouveau 0000:00:05.0: DCB connector table: VHER 0x30 5 10 2
[   25.394629] [drm] nouveau 0000:00:05.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   25.394634] [drm] nouveau 0000:00:05.0:   1: 0x00000131: type 0x31 idx 1 tag 0xff
[   25.394639] [drm] nouveau 0000:00:05.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   25.394644] [drm] nouveau 0000:00:05.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   25.394648] [drm] nouveau 0000:00:05.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   25.394653] [drm] nouveau 0000:00:05.0:   5: 0x00000340: type 0x40 idx 3 tag 0xff
[   25.394658] [drm] nouveau 0000:00:05.0: Raw DCB entry 0: 03005313 00000004
[   25.394663] [drm] nouveau 0000:00:05.0: Raw DCB entry 1: 02010300 00000023
[   25.394668] [drm] nouveau 0000:00:05.0: Raw DCB entry 2: 020123f1 0040c080
[   25.394675] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE115
[   25.394752] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE26C
[   25.394757] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE26D
[   25.394776] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE3EF
[   25.394781] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[   25.394785] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[   25.394789] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[   25.394794] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[   25.394798] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[   25.394809] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE438
[   25.411928] [TTM] Zone  kernel: Available graphics memory: 444028 kiB.
[   25.411932] [TTM] Zone highmem: Available graphics memory: 480416 kiB.
[   25.411946] [drm] nouveau 0000:00:05.0: 64 MiB VRAM
[   25.414266] [drm] nouveau 0000:00:05.0: 64 MiB GART (aperture)
[   25.414539] [drm] nouveau 0000:00:05.0: Allocating FIFO number 0
[   25.415093] [drm] nouveau 0000:00:05.0: nouveau_channel_alloc: initialised FIFO 0
[   25.415101] [drm] nouveau 0000:00:05.0: Initial CRTC_OWNER is 0
[   25.415107] [drm] nouveau 0000:00:05.0: Saving VGA fonts
[   25.452528] [drm] nouveau 0000:00:05.0: Detected a LVDS connector
[   25.478110] phy0: Selected rate control algorithm 'minstrel'
[   25.479024] Registered led device: rt2800usb-phy0::radio
[   25.479046] Registered led device: rt2800usb-phy0::assoc
[   25.479068] Registered led device: rt2800usb-phy0::quality
[   25.479545] usbcore: registered new interface driver rt2800usb
[   25.480644] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   25.492154] rtusb init --->
[   25.492263] usbcore: registered new interface driver rt2870
[   25.562785] [drm] nouveau 0000:00:05.0: Detected a VGA connector
[   25.562934] [drm] nouveau 0000:00:05.0: Detected a TV connector
[   25.563929] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[   25.563934] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[   25.563938] [drm] nouveau 0000:00:05.0: 0xD2AF: Parsing digital output script table
[   25.796567] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   25.807786] type=1505 audit(1041397349.133:5):  operation="profile_load" pid=745 name="/usr/share/gdm/guest-session/Xsession"
[   25.810017] type=1505 audit(1041397349.137:6):  operation="profile_replace" pid=746 name="/sbin/dhclient3"
[   25.810385] type=1505 audit(1041397349.137:7):  operation="profile_replace" pid=746 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.810591] type=1505 audit(1041397349.137:8):  operation="profile_replace" pid=746 name="/usr/lib/connman/scripts/dhclient-script"
[   25.814901] type=1505 audit(1041397349.141:9):  operation="profile_load" pid=747 name="/usr/bin/evince"
[   25.819430] type=1505 audit(1041397349.145:10):  operation="profile_load" pid=747 name="/usr/bin/evince-previewer"
[   25.822313] type=1505 audit(1041397349.149:11):  operation="profile_load" pid=747 name="/usr/bin/evince-thumbnailer"
[   25.826622] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   25.848087] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[   25.848093] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[   25.916067] [drm] nouveau 0000:00:05.0: Load detected on output B
[   25.944042] [drm] nouveau 0000:00:05.0: Load detected on output B
[   25.944286] [drm] nouveau 0000:00:05.0: allocated 1280x800 fb: 0x49000, bo f246e000
[   25.944433] fb0: nouveaufb frame buffer device
[   25.944436] registered panic notifier
[   25.944445] [drm] Initialized nouveau 0.0.15 20090420 for 0000:00:05.0 on minor 0
[   25.947190] vga16fb: initializing
[   25.947196] vga16fb: mapped to 0xc00a0000
[   25.947205] vga16fb: not registering due to another framebuffer present
[   25.950002] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   25.950010]   alloc irq_desc for 17 on node -1
[   25.950013]   alloc kstat_irqs on node -1
[   25.950026] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 17 (level, high) -> IRQ 17
[   25.950031] hda_intel: Disable MSI for Nvidia chipset
[   25.950074] HDA Intel 0000:00:10.1: setting latency timer to 64
[   26.001551] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   26.001556] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[   26.001560] [drm] nouveau 0000:00:05.0: 0xD314: Parsing digital output script table
[   26.152053] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[   26.152058] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[   26.152062] [drm] nouveau 0000:00:05.0: 0xD298: Parsing digital output script table
[   26.728073] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   26.738436] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on TV encoder (output 2)
[   26.738444] [drm] nouveau 0000:00:05.0: Output TV-1 is running on CRTC 1 using output B
[   26.739278] Console: switching to colour frame buffer device 90x36
[   26.943459] ppdev: user-space parallel port driver
[   27.173060] [drm] nouveau 0000:00:05.0: Load detected on output B
[   27.200057] [drm] nouveau 0000:00:05.0: Load detected on output B
[   27.248103] [drm] nouveau 0000:00:05.0: Load detected on output B
[   27.276089] [drm] nouveau 0000:00:05.0: Load detected on output B
[   27.283474] [drm] nouveau 0000:00:05.0: Allocating FIFO number 1
[   27.284110] [drm] nouveau 0000:00:05.0: nouveau_channel_alloc: initialised FIFO 1
[   27.297496] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[   27.297502] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[   27.297507] [drm] nouveau 0000:00:05.0: 0xD2AF: Parsing digital output script table
[   27.604162] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   27.604168] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[   27.604173] [drm] nouveau 0000:00:05.0: 0xD314: Parsing digital output script table
[   27.756055] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[   27.756059] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[   27.756063] [drm] nouveau 0000:00:05.0: 0xD298: Parsing digital output script table
[   28.476079] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   28.476311] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[   28.496449] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on TV encoder (output 2)
[   28.496456] [drm] nouveau 0000:00:05.0: Output TV-1 is running on CRTC 1 using output B
[   29.536061] [drm] nouveau 0000:00:05.0: Load detected on output B
[   29.564062] [drm] nouveau 0000:00:05.0: Load detected on output B
[   29.632062] [drm] nouveau 0000:00:05.0: Load detected on output B
[   29.660062] [drm] nouveau 0000:00:05.0: Load detected on output B
[   29.724062] [drm] nouveau 0000:00:05.0: Load detected on output B
[   29.752075] [drm] nouveau 0000:00:05.0: Load detected on output B
[   39.124062] [drm] nouveau 0000:00:05.0: Load detected on output B
[   39.152060] [drm] nouveau 0000:00:05.0: Load detected on output B
[   39.220061] [drm] nouveau 0000:00:05.0: Load detected on output B
[   39.248062] [drm] nouveau 0000:00:05.0: Load detected on output B
[   39.316076] [drm] nouveau 0000:00:05.0: Load detected on output B
[   39.344061] [drm] nouveau 0000:00:05.0: Load detected on output B
[   42.064055] [drm] nouveau 0000:00:05.0: Load detected on output B
[   42.092059] [drm] nouveau 0000:00:05.0: Load detected on output B
[   45.136074] [drm] nouveau 0000:00:05.0: Load detected on output B
[   45.164061] [drm] nouveau 0000:00:05.0: Load detected on output B
[   87.668057] Clocksource tsc unstable (delta = -154365609 ns)
[  100.584992] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin
[  100.819183] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  100.833722] eth0: no link during initialization.
[  100.834595] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  109.816359] wlan0: Creating new IBSS network, BSSID 46:74:04:1b:24:a0
[  110.957203] ip_tables: (C) 2000-2006 Netfilter Core Team
[  111.009731] nf_conntrack version 0.5.0 (15013 buckets, 60052 max)
[  111.010746] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  111.010755] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[  111.010760] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  111.665052] wlan0: no IPv6 routers present
[  350.000423] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  410.000445] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  470.000468] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  530.000494] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  590.000522] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  650.000543] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  710.000578] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  770.000088] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  830.000616] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  890.000638] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  950.000664] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1010.000708] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1070.000713] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1130.000747] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1190.000776] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1250.000790] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1273.474555] wlan0: Trigger new scan to find an IBSS to join
[ 1273.680554] wlan0: Selected IBSS BSSID 46:74:04:1b:24:a0 based on configured SSID
[ 1304.000818] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1364.000828] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1424.000847] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1484.000877] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1544.000912] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1604.000931] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1664.000970] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1724.000982] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1784.001009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1844.001051] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1904.001057] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1964.001094] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2024.001101] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2084.001115] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2144.001137] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2204.001163] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2264.001185] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2324.001210] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2384.001232] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2444.001263] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2504.000296] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2564.000309] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2624.000337] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2638.994734] wlan0: Trigger new scan to find an IBSS to join
[ 2639.138096] wlan0: Selected IBSS BSSID 46:74:04:1b:24:a0 based on configured SSID
[ 2669.000371] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2729.000394] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2789.000425] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2849.000445] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2909.000469] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2969.000497] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3029.000520] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3089.000533] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3149.000564] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3209.000592] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3269.000627] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3277.396087] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 3277.529641] usb 1-3: configuration #1 chosen from 1 choice
[ 3277.590591] Initializing USB Mass Storage driver...
[ 3277.591186] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3277.591475] usbcore: registered new interface driver usb-storage
[ 3277.591483] USB Mass Storage support registered.
[ 3277.600833] usb-storage: device found at 3
[ 3277.600842] usb-storage: waiting for device to settle before scanning
[ 3282.596762] usb-storage: device scan complete
[ 3282.598795] scsi 4:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[ 3282.603208] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3282.608304] sd 4:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[ 3282.611531] sd 4:0:0:0: [sdb] Write Protect is off
[ 3282.611545] sd 4:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 3282.611553] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3282.614610] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3282.614626]  sdb: sdb1
[ 3282.624668] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3282.624683] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 3329.000629] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3388.988103] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3449.000100] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3508.988714] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3569.000733] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3610.972788] usb 1-3: USB disconnect, address 3
[ 3629.000106] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3689.000788] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3749.000817] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3809.000835] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3869.000862] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3929.000889] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3971.916069] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 3972.049910] usb 1-3: configuration #1 chosen from 1 choice
[ 3972.051270] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3972.051583] usb-storage: device found at 4
[ 3972.051591] usb-storage: waiting for device to settle before scanning
[ 3977.049033] usb-storage: device scan complete
[ 3977.051092] scsi 5:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[ 3977.053431] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3977.054390] sd 5:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[ 3977.055913] sd 5:0:0:0: [sdb] Write Protect is off
[ 3977.055926] sd 5:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 3977.055934] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3977.059892] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3977.059909]  sdb: sdb1
[ 3977.070583] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3977.070600] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 3989.004913] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4049.000947] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4109.000954] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4169.000982] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4229.001010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4289.001037] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4349.001058] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4409.001075] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4469.001106] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4529.001133] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4589.001150] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4649.001174] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4709.001194] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4769.001222] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4829.001234] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4889.001258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4949.001281] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5009.000295] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5069.000098] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5129.000096] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5189.000096] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5249.000416] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5309.000439] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5369.000464] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5429.000089] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5489.000514] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5549.000087] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5609.000555] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5669.000584] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5729.000613] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5789.000629] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5849.000091] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5909.000669] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5969.000712] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6029.000115] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.002749] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

```


6 ) Network configuration

```
roger@roger-laptop:~$ sudo lshw -C network
[sudo] password for roger: 
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:12:0e:b9:28:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bgn

```

7 ) Scan for networks:

```
roger@roger-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 46:74:04:1B:24:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"pete"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4115864ms ago
                    IE: Unknown: 000470657465
                    IE: Unknown: 010802040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C

```

8 ) Ubuntu Version: 

```
roger@roger-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS

```

9 ) Kernel/architecture (including 32 vs. 64 bit): 

```
roger@roger-laptop:~$ uname -mr
2.6.32-21-generic i686

```

10 ) Restarting the network:

```
roger@roger-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

Thank you in advance,
DT

---

### Post by chili555 on 2011-04-07
It is set up for an ad-hoc connection, that is, computer to computer. Is that what you want? If not, please do:```
sudo iwconfig wlan0 mode managed
```'Managed' is for computer to router.

Now click the Network Manager icon and see if you see your network, pete I assume, and see if you can connect.

---

### Post by dtate123 on 2011-04-07
Thank you Chili555

I guess I don't want ad-hoc? 

> roger@roger-laptop:~$ sudo iwconfig wlan0 mode managed
[sudo] password for roger: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

But, again, when I boot, the machine will find and connect to "pete."

But still no data through the pipe to the page.

---

### Post by chili555 on 2011-04-07
You might right-click the Network Manager icon and select Edit Connections. Select Wireless and Edit. Make sure Infrastructure is selected, not Ad Hoc.

Save and close.

See attached.

---

### Post by dtate123 on 2011-04-08
Thanks Chili.

Well, now there's a little red exclamation point across the bottom three sound/radio waves lines in the network manager.

I rebooted and then copied all the network configuration settings on another laptop running Ubuntu which is able to get a working connection and rebooted again but still the [COLOR="Red"]![/COLOR].  

I must have messed something up.  I'll repost the network troubleshooting commands.

---

### Post by dtate123 on 2011-04-08
```
roger@roger-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 07b8:3071 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```



roger@roger-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:0e:7a:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:0e:b9:28:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```




roger@roger-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
rt2870sta             461811  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              204922  2 rt2x00usb,rt2x00lib
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
cfg80211              126485  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  4 nouveau,ttm,drm_kms_helper
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 rt2x00lib,sdhci
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sata_nv                19440  2 
pata_amd                8766  1 
forcedeth              49556  0 
roger@roger-laptop:~$
```

```

[    0.848624] pci 0000:00:02.0:   IO window: disabled
[    0.848624] pci 0000:00:02.0:   MEM window: disabled
[    0.848624] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.848624] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.848624] pci 0000:00:03.0:   IO window: 0x4000-0x4fff
[    0.848624] pci 0000:00:03.0:   MEM window: 0xc8000000-0xc87fffff
[    0.848624] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.848624] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.848624] pci 0000:00:10.0:   IO window: disabled
[    0.848624] pci 0000:00:10.0:   MEM window: 0xc3000000-0xc30fffff
[    0.848624] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.848624] pci 0000:00:02.0: setting latency timer to 64
[    0.848624] pci 0000:00:03.0: setting latency timer to 64
[    0.848624] pci 0000:00:10.0: setting latency timer to 64
[    0.848624] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.848624] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.848624] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.848624] pci_bus 0000:02: resource 1 mem: [0xc8000000-0xc87fffff]
[    0.848624] pci_bus 0000:03: resource 1 mem: [0xc3000000-0xc30fffff]
[    0.848624] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.848624] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.848624] NET: Registered protocol family 2
[    0.848624] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.848780] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.849657] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.850071] TCP: Hash tables configured (established 131072 bind 65536)
[    0.850074] TCP reno registered
[    0.850176] NET: Registered protocol family 1
[    0.850239] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.850268] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.850276] pci 0000:00:05.0: Boot video device
[    1.056139] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    1.056199] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    1.056261] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    1.056309] Simple Boot Flag at 0x36 set to 0x1
[    1.056526] cpufreq-nforce2: No nForce2 chipset.
[    1.056557] Scanning for low memory corruption every 60 seconds
[    1.056692] audit: initializing netlink socket (disabled)
[    1.056705] type=2000 audit(1302260881.053:1): initialized
[    1.069458] highmem bounce pool size: 64 pages
[    1.069465] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.071455] VFS: Disk quotas dquot_6.5.2
[    1.071537] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.072304] fuse init (API version 7.13)
[    1.072413] msgmni has been set to 1733
[    1.072794] alg: No test for stdrng (krng)
[    1.072870] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.072875] io scheduler noop registered
[    1.072878] io scheduler anticipatory registered
[    1.072882] io scheduler deadline registered
[    1.072935] io scheduler cfq registered (default)
[    1.073107]   alloc irq_desc for 24 on node -1
[    1.073110]   alloc kstat_irqs on node -1
[    1.073120] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    1.073127] pcieport 0000:00:02.0: setting latency timer to 64
[    1.073216]   alloc irq_desc for 25 on node -1
[    1.073219]   alloc kstat_irqs on node -1
[    1.073226] pcieport 0000:00:03.0: irq 25 for MSI/MSI-X
[    1.073232] pcieport 0000:00:03.0: setting latency timer to 64
[    1.073300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.073332] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.074133] ACPI: AC Adapter [ADP1] (on-line)
[    1.074240] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.075393] ACPI: Lid Switch [LID0]
[    1.075450] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.075458] ACPI: Sleep Button [SLPB]
[    1.075508] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    1.075512] ACPI: Power Button [PWRB]
[    1.075585] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.075588] ACPI: Power Button [PWRF]
[    1.075913] ACPI: processor limited to max C-state 1
[    1.075941] processor LNXCPU:00: registered as cooling_device0
[    1.076058] processor LNXCPU:01: registered as cooling_device1
[    1.093076] thermal LNXTHERM:01: registered as thermal_zone0
[    1.093085] ACPI: Thermal Zone [TZS0] (56 C)
[    1.097634] thermal LNXTHERM:02: registered as thermal_zone1
[    1.097643] ACPI: Thermal Zone [TZS1] (59 C)
[    1.097820] isapnp: Scanning for PnP cards...
[    1.099406] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.100957] brd: module loaded
[    1.101537] loop: module loaded
[    1.101653] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.101880] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    1.101908] pata_acpi 0000:00:0e.0: enabling device (0005 -> 0007)
[    1.102308] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    1.102314]   alloc irq_desc for 23 on node -1
[    1.102317]   alloc kstat_irqs on node -1
[    1.102329] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.102350] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    1.102359] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    1.102745] Fixed MDIO Bus: probed
[    1.102786] PPP generic driver version 2.4.2
[    1.102843] tun: Universal TUN/TAP device driver, 1.6
[    1.102846] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.102950] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.103343] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    1.103347]   alloc irq_desc for 22 on node -1
[    1.103350]   alloc kstat_irqs on node -1
[    1.103360] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    1.103377] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    1.103381] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    1.103430] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.103459] ehci_hcd 0000:00:0b.1: debug port 1
[    1.103467] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    1.103492] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    1.116040] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.116149] usb usb1: configuration #1 chosen from 1 choice
[    1.116187] hub 1-0:1.0: USB hub found
[    1.116197] hub 1-0:1.0: 8 ports detected
[    1.116279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.116716] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    1.116720]   alloc irq_desc for 21 on node -1
[    1.116723]   alloc kstat_irqs on node -1
[    1.116734] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, high) -> IRQ 21
[    1.116750] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.116754] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.116801] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.116837] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xc0004000
[    1.174123] usb usb2: configuration #1 chosen from 1 choice
[    1.174157] hub 2-0:1.0: USB hub found
[    1.174170] hub 2-0:1.0: 8 ports detected
[    1.174250] uhci_hcd: USB Universal Host Controller Interface driver
[    1.174348] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.174662] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.174753] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.174763] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.174768] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.174772] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.174776] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.174872] mice: PS/2 mouse device common for all mice
[    1.175058] rtc_cmos 00:07: RTC can wake from S4
[    1.175102] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.175137] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.175265] device-mapper: uevent: version 1.0.3
[    1.175400] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.175483] device-mapper: multipath: version 1.1.0 loaded
[    1.175487] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.175633] EISA: Probing bus 0 at eisa.0
[    1.175640] Cannot allocate resource for EISA slot 1
[    1.175643] Cannot allocate resource for EISA slot 2
[    1.175646] Cannot allocate resource for EISA slot 3
[    1.175649] Cannot allocate resource for EISA slot 4
[    1.175665] EISA: Detected 0 cards.
[    1.175762] cpuidle: using governor ladder
[    1.175765] cpuidle: using governor menu
[    1.176337] TCP cubic registered
[    1.176536] NET: Registered protocol family 10
[    1.177098] lo: Disabled Privacy Extensions
[    1.177499] NET: Registered protocol family 17
[    1.177544] powernow-k8: Found 1 AMD Turion(tm) 64 X2  processors (2 cpu cores) (version 2.20.00)
[    1.177587] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    1.177591] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    1.177641] Using IPI No-Shortcut mode
[    1.177750] PM: Resume from disk failed.
[    1.177764] registered taskstats version 1
[    1.178143]   Magic number: 7:816:124
[    1.178246] rtc_cmos 00:07: setting system clock to 2011-04-08 11:08:02 UTC (1302260882)
[    1.178251] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.178254] EDD information not available.
[    1.180936] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.428038] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.450809] isapnp: No Plug & Play device found
[    1.450849] Freeing unused kernel memory: 656k freed
[    1.451431] Write protecting the kernel text: 4676k
[    1.451480] Write protecting the kernel read-only data: 1840k
[    1.475944] udev: starting version 151
[    1.579144] usb 1-6: configuration #1 chosen from 1 choice
[    1.601569] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.601975] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.601982]   alloc irq_desc for 20 on node -1
[    1.601985]   alloc kstat_irqs on node -1
[    1.601998] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.602004] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.602053] nv_probe: set workaround bit for reversed mac addr
[    1.613791] ACPI: EC: GPE storm detected, transactions will use polling mode
[    1.657313] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    1.657320]   alloc irq_desc for 19 on node -1
[    1.657324]   alloc kstat_irqs on node -1
[    1.657336] ohci1394 0000:03:09.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, high) -> IRQ 19
[    1.714082] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.056220] ACPI: Battery Slot [BAT0] (battery present)
[    2.121060] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:0e:7a:ca
[    2.121066] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    2.121215] pata_amd 0000:00:0d.0: version 0.4.1
[    2.121271] pata_amd 0000:00:0d.0: setting latency timer to 64
[    2.121376] scsi0 : pata_amd
[    2.121512] scsi1 : pata_amd
[    2.122192] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    2.122197] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    2.122262] sata_nv 0000:00:0e.0: version 3.5
[    2.122273] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    2.122276] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.122331] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.122524] scsi2 : sata_nv
[    2.122618] scsi3 : sata_nv
[    2.122812] ata3: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 23
[    2.122818] ata4: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 23
[    2.588102] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.596274] ata3.00: ATA-7: ST9120821AS, 7.24, max UDMA/100
[    2.596279] ata3.00: 234441648 sectors, multi 16: LBA48 
[    2.612288] ata3.00: configured for UDMA/100
[    2.988558] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a0003aa5038]
[    7.324073] ata2: link is slow to respond, please be patient (ready=0)
[   12.308070] ata2: device not ready (errno=-16), forcing hardreset
[   12.489300] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L632L, HP16, max MWDMA2
[   12.489333] ata2: nv_mode_filter: 0x39f&0xfff9f->0x39f, BIOS=0x0 (0x0) ACPI=0x1 (600:600:0x10)
[   12.521600] ata2.00: configured for MWDMA2
[   12.547613] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632L HP16 PQ: 0 ANSI: 5
[   12.593833] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.593838] Uniform CD-ROM driver Revision: 3.20
[   12.593970] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.594051] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   12.594253] scsi 2:0:0:0: Direct-Access     ATA      ST9120821AS      7.24 PQ: 0 ANSI: 5
[   12.594461] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   12.594545] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[   12.594607] sd 2:0:0:0: [sda] Write Protect is off
[   12.594611] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.594643] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.594815]  sda: sda1 sda2 < sda5 sda6 >
[   12.647662] sd 2:0:0:0: [sda] Attached SCSI disk
[   12.914674] ata4: SATA link down (SStatus 0 SControl 300)
[   13.352369] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   24.869511] udev: starting version 151
[   24.935416] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   24.935578] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.936251] lp: driver loaded but no devices found
[   24.943521] Adding 2810872k swap on /dev/sda6.  Priority:-1 extents:1 across:2810872k 
[   25.238019] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   25.238349] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   25.238375] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   25.243112] sdhci: Secure Digital Host Controller Interface driver
[   25.243116] sdhci: Copyright(c) Pierre Ossman
[   25.245039] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 19)
[   25.245091] Linux agpgart interface v0.103
[   25.291089] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[   25.291097]   alloc irq_desc for 18 on node -1
[   25.291100]   alloc kstat_irqs on node -1
[   25.291114] sdhci-pci 0000:03:09.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, high) -> IRQ 18
[   25.303505] Registered led device: mmc0::
[   25.304540] mmc0: SDHCI controller on PCI [0000:03:09.1] using PIO
[   25.382356] [drm] Initialized drm 1.1.0 20060810
[   25.392486] type=1505 audit(1302275306.713:2):  operation="profile_load" pid=616 name="/sbin/dhclient3"
[   25.392838] type=1505 audit(1302275306.713:3):  operation="profile_load" pid=616 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.393035] type=1505 audit(1302275306.713:4):  operation="profile_load" pid=616 name="/usr/lib/connman/scripts/dhclient-script"
[   25.429552] cfg80211: Calling CRDA to update world regulatory domain
[   25.486865] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
[   25.486873] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 21 (level, high) -> IRQ 21
[   25.486879] nouveau 0000:00:05.0: setting latency timer to 64
[   25.489638] [drm] nouveau 0000:00:05.0: failed to evaluate _DSM: 5
[   25.490032] [drm] nouveau 0000:00:05.0: Detected an NV40 generation card (0x04e000a2)
[   25.490648] [drm] nouveau 0000:00:05.0: Attempting to load BIOS image from PROM
[   25.490664] [drm] nouveau 0000:00:05.0: ... BIOS signature not found
[   25.490667] [drm] nouveau 0000:00:05.0: Attempting to load BIOS image from PRAMIN
[   25.494456] cfg80211: World regulatory domain updated:
[   25.494461] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.494466] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.494470] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.494474] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.494477] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.494481] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.530635] [drm] nouveau 0000:00:05.0: ... appears to be valid
[   25.530640] [drm] nouveau 0000:00:05.0: BIT BIOS found
[   25.530644] [drm] nouveau 0000:00:05.0: Bios version 05.51.28.39
[   25.530648] [drm] nouveau 0000:00:05.0: TMDS table script pointers not stubbed
[   25.530651] [drm] nouveau 0000:00:05.0: BIT table 'd' not found
[   25.530654] [drm] nouveau 0000:00:05.0: Found Display Configuration Block version 3.0
[   25.530659] [drm] nouveau 0000:00:05.0: DCB connector table: VHER 0x30 5 10 2
[   25.530664] [drm] nouveau 0000:00:05.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   25.530668] [drm] nouveau 0000:00:05.0:   1: 0x00000131: type 0x31 idx 1 tag 0xff
[   25.530672] [drm] nouveau 0000:00:05.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   25.530676] [drm] nouveau 0000:00:05.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   25.530680] [drm] nouveau 0000:00:05.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   25.530683] [drm] nouveau 0000:00:05.0:   5: 0x00000340: type 0x40 idx 3 tag 0xff
[   25.530687] [drm] nouveau 0000:00:05.0: Raw DCB entry 0: 03005313 00000004
[   25.530692] [drm] nouveau 0000:00:05.0: Raw DCB entry 1: 02010300 00000023
[   25.530695] [drm] nouveau 0000:00:05.0: Raw DCB entry 2: 020123f1 0040c080
[   25.530702] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE115
[   25.530779] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE26C
[   25.530782] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE26D
[   25.530801] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE3EF
[   25.530804] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[   25.530808] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[   25.530811] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[   25.530814] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[   25.530817] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[   25.530827] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE438
[   25.548549] [TTM] Zone  kernel: Available graphics memory: 444028 kiB.
[   25.548553] [TTM] Zone highmem: Available graphics memory: 480416 kiB.
[   25.548566] [drm] nouveau 0000:00:05.0: 64 MiB VRAM
[   25.550835] [drm] nouveau 0000:00:05.0: 64 MiB GART (aperture)
[   25.551113] [drm] nouveau 0000:00:05.0: Allocating FIFO number 0
[   25.551831] [drm] nouveau 0000:00:05.0: nouveau_channel_alloc: initialised FIFO 0
[   25.551841] [drm] nouveau 0000:00:05.0: Initial CRTC_OWNER is 0
[   25.551848] [drm] nouveau 0000:00:05.0: Saving VGA fonts
[   25.604107] [drm] nouveau 0000:00:05.0: Detected a LVDS connector
[   25.620154] phy0: Selected rate control algorithm 'minstrel'
[   25.621086] Registered led device: rt2800usb-phy0::radio
[   25.621107] Registered led device: rt2800usb-phy0::assoc
[   25.621129] Registered led device: rt2800usb-phy0::quality
[   25.622954] usbcore: registered new interface driver rt2800usb
[   25.624062] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   25.636687] rtusb init --->
[   25.636891] usbcore: registered new interface driver rt2870
[   25.714681] [drm] nouveau 0000:00:05.0: Detected a VGA connector
[   25.714984] [drm] nouveau 0000:00:05.0: Detected a TV connector
[   25.716082] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[   25.716091] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[   25.716096] [drm] nouveau 0000:00:05.0: 0xD2AF: Parsing digital output script table
[   25.896558] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   25.926117] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   26.004087] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[   26.004093] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[   26.072042] [drm] nouveau 0000:00:05.0: Load detected on output B
[   26.100068] [drm] nouveau 0000:00:05.0: Load detected on output B
[   26.100307] [drm] nouveau 0000:00:05.0: allocated 1280x800 fb: 0x49000, bo f2b68e00
[   26.100430] fb0: nouveaufb frame buffer device
[   26.100433] registered panic notifier
[   26.100443] [drm] Initialized nouveau 0.0.15 20090420 for 0000:00:05.0 on minor 0
[   26.103092] vga16fb: initializing
[   26.103098] vga16fb: mapped to 0xc00a0000
[   26.103106] vga16fb: not registering due to another framebuffer present
[   26.103668] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   26.103675]   alloc irq_desc for 17 on node -1
[   26.103677]   alloc kstat_irqs on node -1
[   26.103691] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 17 (level, high) -> IRQ 17
[   26.103696] hda_intel: Disable MSI for Nvidia chipset
[   26.103749] HDA Intel 0000:00:10.1: setting latency timer to 64
[   26.141161] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   26.141165] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[   26.141169] [drm] nouveau 0000:00:05.0: 0xD314: Parsing digital output script table
[   26.292070] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[   26.292076] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[   26.292080] [drm] nouveau 0000:00:05.0: 0xD298: Parsing digital output script table
[   26.892064] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   26.902424] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on TV encoder (output 2)
[   26.902432] [drm] nouveau 0000:00:05.0: Output TV-1 is running on CRTC 1 using output B
[   26.903560] Console: switching to colour frame buffer device 90x36
[  584.287408] type=1505 audit(1302275865.605:5):  operation="profile_load" pid=805 name="/usr/share/gdm/guest-session/Xsession"
[  584.295481] type=1505 audit(1302275865.613:6):  operation="profile_replace" pid=807 name="/sbin/dhclient3"
[  584.295860] type=1505 audit(1302275865.613:7):  operation="profile_replace" pid=807 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  584.296070] type=1505 audit(1302275865.617:8):  operation="profile_replace" pid=807 name="/usr/lib/connman/scripts/dhclient-script"
[  584.296631] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin
[  584.303855] type=1505 audit(1302275865.621:9):  operation="profile_load" pid=808 name="/usr/bin/evince"
[  584.322255] type=1505 audit(1302275865.641:10):  operation="profile_load" pid=808 name="/usr/bin/evince-previewer"
[  584.329161] type=1505 audit(1302275865.649:11):  operation="profile_load" pid=808 name="/usr/bin/evince-thumbnailer"
[  584.353782] type=1505 audit(1302275865.673:12):  operation="profile_load" pid=878 name="/usr/lib/cups/backend/cups-pdf"
[  584.354234] type=1505 audit(1302275865.673:13):  operation="profile_load" pid=878 name="/usr/sbin/cupsd"
[  584.363624] type=1505 audit(1302275865.681:14):  operation="profile_load" pid=880 name="/usr/sbin/tcpdump"
[  584.527835] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  584.536018] eth0: no link during initialization.
[  584.536950] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  584.631475] ppdev: user-space parallel port driver
[  584.693096] [drm] nouveau 0000:00:05.0: Load detected on output B
[  584.721066] [drm] nouveau 0000:00:05.0: Load detected on output B
[  584.769084] [drm] nouveau 0000:00:05.0: Load detected on output B
[  584.797053] [drm] nouveau 0000:00:05.0: Load detected on output B
[  584.801934] [drm] nouveau 0000:00:05.0: Allocating FIFO number 1
[  584.802501] [drm] nouveau 0000:00:05.0: nouveau_channel_alloc: initialised FIFO 1
[  584.816606] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[  584.816613] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[  584.816619] [drm] nouveau 0000:00:05.0: 0xD2AF: Parsing digital output script table
[  585.124165] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[  585.124171] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[  585.124175] [drm] nouveau 0000:00:05.0: 0xD314: Parsing digital output script table
[  585.276052] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[  585.276058] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[  585.276061] [drm] nouveau 0000:00:05.0: 0xD298: Parsing digital output script table
[  585.996077] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[  585.996314] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[  586.016458] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on TV encoder (output 2)
[  586.016466] [drm] nouveau 0000:00:05.0: Output TV-1 is running on CRTC 1 using output B
[  586.988064] [drm] nouveau 0000:00:05.0: Load detected on output B
[  587.016069] [drm] nouveau 0000:00:05.0: Load detected on output B
[  587.084062] [drm] nouveau 0000:00:05.0: Load detected on output B
[  587.112079] [drm] nouveau 0000:00:05.0: Load detected on output B
[  587.180062] [drm] nouveau 0000:00:05.0: Load detected on output B
[  587.259844] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[  587.279930] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on vga encoder (output 1)
[  587.279936] [drm] nouveau 0000:00:05.0: Output VGA-1 is running on CRTC 1 using output B
[  611.788064] [drm] nouveau 0000:00:05.0: Load detected on output B
[  611.816060] [drm] nouveau 0000:00:05.0: Load detected on output B
[  611.880061] [drm] nouveau 0000:00:05.0: Load detected on output B
[  611.908060] [drm] nouveau 0000:00:05.0: Load detected on output B
[  611.972073] [drm] nouveau 0000:00:05.0: Load detected on output B
[  612.000099] [drm] nouveau 0000:00:05.0: Load detected on output B
[  617.840146] [drm] nouveau 0000:00:05.0: Load detected on output B
[  617.868065] [drm] nouveau 0000:00:05.0: Load detected on output B
[  645.676067] Clocksource tsc unstable (delta = -260733682 ns)
[ 2375.612082] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 2375.745698] usb 1-3: configuration #1 chosen from 1 choice
[ 2375.789459] Initializing USB Mass Storage driver...
[ 2375.789814] scsi4 : SCSI emulation for USB Mass Storage devices
[ 2375.790100] usbcore: registered new interface driver usb-storage
[ 2375.790108] USB Mass Storage support registered.
[ 2375.791770] usb-storage: device found at 3
[ 2375.791778] usb-storage: waiting for device to settle before scanning
[ 2380.788796] usb-storage: device scan complete
[ 2380.790860] scsi 4:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[ 2380.807819] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2380.807836] sd 4:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[ 2380.808653] sd 4:0:0:0: [sdb] Write Protect is off
[ 2380.808663] sd 4:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 2380.808670] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2380.813276] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2380.813295]  sdb: sdb1
[ 2380.817678] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2380.817693] sd 4:0:0:0: [sdb] Attached SCSI removable disk
```

```
roger@roger-laptop:~$ sudo lshw -C network
[sudo] password for roger: 
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:12:0e:b9:28:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
```


```
roger@roger-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```

This last command - restarting the network - appears to be working now:  

```
roger@roger-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
```

---

### Post by chili555 on 2011-04-08
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot and give us a report.

---

### Post by dtate123 on 2011-04-08
That fixed it Chili!  Thank you sir.

---

### Post by dtate123 on 2011-04-08
well, shoot.  the exclamation point is back, and it won't go online wirelessly.  If I may, I'll post the terminal information here again in a moment . . .

---

### Post by dtate123 on 2011-04-08
update: just after the restart the machine asked me if I wanted to use the proprietary video drivers.  Although the display looked more clear, I said "no." And that was when I noticed the exclamation point.  

After running the troubleshooting network terminal commands, I rebooted.

Upon reboot, the screen was no longer as clear, but it went online wirelessly automatically.

I decided I would like to try the (proprietary) drivers, and I downloaded and installed them and rebooted and . . . we're online!

Another reboot, and we're still good!

So, I think we're in "solved" territory."

Again, thanks Chili.

---

### Post by annabee on 2011-04-08
I am having the same problem with Ubunto Remix on my Eee PC 1215t

Will this solution work for my machine too?

---

### Post by chili555 on 2011-04-08
> **annabee said:**
> I am having the same problem with Ubunto Remix on my Eee PC 1215t

Will this solution work for my machine too?Do you have the same conflicting drivers, rt2800usb or rt2800pci and rt2870sta?```
lsmod | grep rt2
```If so, then yes. If not, start a new thread and tell us more.```
sudo lshw -C network
iwconfig
lsusb

```

---

