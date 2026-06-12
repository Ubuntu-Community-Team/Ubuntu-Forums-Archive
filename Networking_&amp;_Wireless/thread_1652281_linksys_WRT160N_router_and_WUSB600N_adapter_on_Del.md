---
title: "linksys WRT160N router and WUSB600N adapter on Dell Dimension 4600 see it but no net"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by peterthinking on 2010-12-24
I've been beating my head against this thing for a few days now.
I can see my connection, It's greyed out, has a little grey lock on it, and a small grey tower by it.

Linksys Wireless-N Broadband Router
Model # WRT160N
In bedroom.

Linksys Dual-Band Wireless-N USB Network Adapter
Model # WUSB600N
In Livingroom.

Box is a Dell Dimension 4600 Replaced the DVD with a DVD Burner, replaced HD and added RAM, other than that it's stock.

New clean install of UBUNTU all I added was restricted extras.

Below is a gigantic cut and paste I hope it's enough info.
All cut and pasted when the wireless was supposedly connected, 
right now I have a bunch of cord running down the hall (ARRRRGHHH!)
Thanks




peter@peter-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
02:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
peter@peter-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0c45:7408 Microdia 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
peter@peter-desktop:~$ 
peter@peter-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:72:9a:bb  
          inet6 addr: fe80::207:e9ff:fe72:9abb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14399094 (14.3 MB)  TX bytes:1134066 (1.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68896 (68.8 KB)  TX bytes:68896 (68.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:de:7a:6e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fede:7a6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7384 (7.3 KB)

peter@peter-desktop:~$ peter@peter-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:72:9a:bb  
          inet6 addr: fe80::207:e9ff:fe72:9abb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14399094 (14.3 MB)  TX bytes:1134066 (1.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68896 (68.8 KB)  TX bytes:68896 (68.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:de:7a:6e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fede:7a6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7384 (7.3 KB)

peter@peter-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"linksys_WPS_0502"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: CE:66:43:3B:BE:A4   
          Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
peter@peter-desktop:~$ 
peter@peter-desktop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"linksys_WPS_0502"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: CE:66:43:3B:BE:A4   
          Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr(SUPRISE SMILEY OMMITED TO ENABLE POST)ff   Fragment thr(SURPRISE SMILEY OMMITED TO ENABLE POST)ff
          Power Management(SUPRISE SMILEY OMMITED TO ENABLE POST)n
peter@peter-desktop:~$ 
peter@peter-desktop:~$ lsmod
Module                  Size  Used by
aes_i586                7268  246 
aes_generic            26863  1 aes_i586
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
nf_conntrack           61615  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6587  1 
dm_crypt               11331  0 
snd_emu10k1_synth       5156  0 
snd_emux_synth         31695  1 snd_emu10k1_synth
snd_seq_virmidi         4213  1 snd_emux_synth
rt2870sta             461811  0 
snd_seq_midi_emul       5492  1 snd_emux_synth
arc4                    1153  2 
snd_emu10k1           131163  3 snd_emu10k1_synth
rt2800usb              31531  0 
snd_util_mem            3106  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5412  2 snd_emux_synth,snd_emu10k1
rt2x00usb               9703  1 rt2800usb
snd_intel8x0           25588  2 
snd_seq_dummy           1338  0 
rt2x00lib              27509  2 rt2800usb,rt2x00usb
snd_ac97_codec        100646  2 snd_emu10k1,snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_seq_oss            26722  0 
led_class               2864  1 rt2x00lib
snd_pcm_oss            35308  0 
snd_seq_midi            4557  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            19056  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
mac80211              205402  2 rt2x00usb,rt2x00lib
snd_seq_midi_event      6003  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                47263  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5700  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63245  0 
snd                    54180  22 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                1793  0 
ppdev                   5259  0 
cfg80211              126528  2 rt2x00lib,mac80211
dcdbas                  5422  0 
serio_raw               3978  0 
nvidia               4701243  22 
crc_ccitt               1339  1 rt2800usb
parport_pc             25962  1 
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_emu10k1,snd_intel8x0,snd_pcm
lp                      7028  0 
shpchp                 28820  0 
parport                32635  3 ppdev,parport_pc,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
intel_agp              24375  1 
e100                   28211  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
vga16fb                11385  1 
vgastate                8961  1 vga16fb
usbhid                 36110  0 
hid                    67032  1 usbhid
mii                     4381  1 e100
floppy                 53016  0 
agpgart                31724  2 nvidia,intel_agp
peter@peter-desktop:~$ 

************RESULTS OF dmseg
[    0.192155] pci 0000:02:01.0: supports D1 D2
[    0.192193] pci 0000:02:01.2: reg 10 32bit mmio: [0xfcff5800-0xfcff5fff]
[    0.192202] pci 0000:02:01.2: reg 14 32bit mmio: [0xfcffc000-0xfcffffff]
[    0.192246] pci 0000:02:01.2: supports D1 D2
[    0.192249] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.192254] pci 0000:02:01.2: PME# disabled
[    0.192295] pci 0000:02:02.0: reg 10 32bit mmio: [0xfcff6000-0xfcff6fff]
[    0.192303] pci 0000:02:02.0: reg 14 io port: [0xdef0-0xdeff]
[    0.192344] pci 0000:02:02.0: supports D1 D2
[    0.192346] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192351] pci 0000:02:02.0: PME# disabled
[    0.192392] pci 0000:02:08.0: reg 10 32bit mmio: [0xfcff7000-0xfcff7fff]
[    0.192400] pci 0000:02:08.0: reg 14 io port: [0xdf40-0xdf7f]
[    0.192441] pci 0000:02:08.0: supports D1 D2
[    0.192444] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192449] pci 0000:02:08.0: PME# disabled
[    0.192486] pci 0000:00:1e.0: transparent bridge
[    0.192491] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.192498] pci 0000:00:1e.0: bridge 32bit mmio: [0xfcf00000-0xfcffffff]
[    0.192516] pci_bus 0000:00: on NUMA node 0
[    0.192523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.193020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.326958] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.327301] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.327823] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.328327] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.328814] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.329154] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.329493] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.329833] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.330045] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.330052] vgaarb: loaded
[    0.330243] SCSI subsystem initialized
[    0.330354] libata version 3.00 loaded.
[    0.330469] usbcore: registered new interface driver usbfs
[    0.330492] usbcore: registered new interface driver hub
[    0.330530] usbcore: registered new device driver usb
[    0.330713] ACPI: WMI: Mapper loaded
[    0.330717] PCI: Using ACPI for IRQ routing
[    0.330926] NetLabel: Initializing
[    0.330929] NetLabel:  domain hash size = 128
[    0.330931] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.330950] NetLabel:  unlabeled traffic allowed by default
[    0.331110] hpet clockevent registered
[    0.331115] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.331122] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.331129] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.336034] Switching to clocksource tsc
[    0.339124] AppArmor: AppArmor Filesystem Enabled
[    0.339157] pnp: PnP ACPI init
[    0.339186] ACPI: bus type pnp registered
[    0.363009] pnp 00:09: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.363015] pnp 00:09: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.363779] pnp: PnP ACPI: found 10 devices
[    0.363782] ACPI: ACPI bus type pnp unregistered
[    0.363789] PnPBIOS: Disabled by ACPI PNP
[    0.363807] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.363813] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.363817] system 00:00: iomem range 0x1000000-0x3ff73fff could not be reserved
[    0.363821] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    0.363826] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.363830] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.363835] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.363841] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
[    0.363845] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.363849] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.363863] system 00:09: ioport range 0xc00-0xc7f has been reserved
[    0.398854] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.398858] pci 0000:00:01.0:   IO window: disabled
[    0.398867] pci 0000:00:01.0:   MEM window: 0xfd000000-0xfeafffff
[    0.398872] pci 0000:00:01.0:   PREFETCH window: 0xea000000-0xf7ffffff
[    0.398881] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.398886] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.398892] pci 0000:00:1e.0:   MEM window: 0xfcf00000-0xfcffffff
[    0.398897] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.398919] pci 0000:00:1e.0: setting latency timer to 64
[    0.398925] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.398929] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.398933] pci_bus 0000:01: resource 1 mem: [0xfd000000-0xfeafffff]
[    0.398936] pci_bus 0000:01: resource 2 pref mem [0xea000000-0xf7ffffff]
[    0.398940] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.398943] pci_bus 0000:02: resource 1 mem: [0xfcf00000-0xfcffffff]
[    0.398946] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.398950] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.399008] NET: Registered protocol family 2
[    0.399158] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.399866] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.401240] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.401994] TCP: Hash tables configured (established 131072 bind 65536)
[    0.402000] TCP reno registered
[    0.402235] NET: Registered protocol family 1
[    0.402392] pci 0000:01:00.0: Boot video device
[    0.402412] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.402575] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.402578] Simple Boot Flag at 0x7a set to 0x1
[    0.402711] cpufreq-nforce2: No nForce2 chipset.
[    0.402758] Scanning for low memory corruption every 60 seconds
[    0.402925] audit: initializing netlink socket (disabled)
[    0.402943] type=2000 audit(1293215331.399:1): initialized
[    0.412148] Trying to unpack rootfs image as initramfs...
[    0.424164] highmem bounce pool size: 64 pages
[    0.424174] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.426234] VFS: Disk quotas dquot_6.5.2
[    0.426324] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.432125] fuse init (API version 7.13)
[    0.432305] msgmni has been set to 1706
[    0.432674] alg: No test for stdrng (krng)
[    0.432770] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.432775] io scheduler noop registered
[    0.432778] io scheduler anticipatory registered
[    0.432780] io scheduler deadline registered
[    0.432837] io scheduler cfq registered (default)
[    0.433005] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.433044] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.433171] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.433183] ACPI: Power Button [VBTN]
[    0.433256] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.433260] ACPI: Power Button [PWRF]
[    0.433534] processor LNXCPU:00: registered as cooling_device0
[    0.473880] isapnp: Scanning for PnP cards...
[    0.484315] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.484431] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.484908] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.485035]   alloc irq_desc for 17 on node -1
[    0.485038]   alloc kstat_irqs on node -1
[    0.485049] serial 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.486524] brd: module loaded
[    0.487171] loop: module loaded
[    0.487321] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.487489] ata_piix 0000:00:1f.1: version 2.13
[    0.487510]   alloc irq_desc for 18 on node -1
[    0.487513]   alloc kstat_irqs on node -1
[    0.487527] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.487603] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.535565] scsi0 : ata_piix
[    0.535766] scsi1 : ata_piix
[    0.535820] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.535825] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.535864] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.535871] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.535964] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.536072] scsi2 : ata_piix
[    0.536311] scsi3 : ata_piix
[    0.536359] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
[    0.536363] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
[    0.536876] Fixed MDIO Bus: probed
[    0.536933] PPP generic driver version 2.4.2
[    0.537043] tun: Universal TUN/TAP device driver, 1.6
[    0.537046] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.537179] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.537210]   alloc irq_desc for 23 on node -1
[    0.537213]   alloc kstat_irqs on node -1
[    0.537225] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.537251] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.537256] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.537305] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.537345] ehci_hcd 0000:00:1d.7: debug port 1
[    0.541238] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.544183] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    0.564226] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.564450] usb usb1: configuration #1 chosen from 1 choice
[    0.564495] hub 1-0:1.0: USB hub found
[    0.564512] hub 1-0:1.0: 8 ports detected
[    0.564609] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.564634] uhci_hcd: USB Universal Host Controller Interface driver
[    0.564714]   alloc irq_desc for 16 on node -1
[    0.564718]   alloc kstat_irqs on node -1
[    0.564729] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.564743] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.564748] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.564809] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.564849] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.564973] usb usb2: configuration #1 chosen from 1 choice
[    0.565011] hub 2-0:1.0: USB hub found
[    0.565023] hub 2-0:1.0: 2 ports detected
[    0.565078]   alloc irq_desc for 19 on node -1
[    0.565082]   alloc kstat_irqs on node -1
[    0.565089] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.565097] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.565103] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.565148] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.565181] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.565303] usb usb3: configuration #1 chosen from 1 choice
[    0.565340] hub 3-0:1.0: USB hub found
[    0.565354] hub 3-0:1.0: 2 ports detected
[    0.565409] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.565417] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.565421] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.565471] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.565496] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.565619] usb usb4: configuration #1 chosen from 1 choice
[    0.565656] hub 4-0:1.0: USB hub found
[    0.565668] hub 4-0:1.0: 2 ports detected
[    0.565725] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.565733] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.565737] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.565782] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.565807] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[    0.565933] usb usb5: configuration #1 chosen from 1 choice
[    0.565971] hub 5-0:1.0: USB hub found
[    0.565983] hub 5-0:1.0: 2 ports detected
[    0.566125] PNP: No PS/2 controller found. Probing ports directly.
[    0.573216] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.573237] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.573489] mice: PS/2 mouse device common for all mice
[    0.573681] rtc_cmos 00:05: RTC can wake from S4
[    0.573747] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.573776] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    0.573960] device-mapper: uevent: version 1.0.3
[    0.574135] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.576400] device-mapper: multipath: version 1.1.0 loaded
[    0.576406] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.577179] EISA: Probing bus 0 at eisa.0
[    0.577219] EISA: Detected 0 cards.
[    0.579852] cpuidle: using governor ladder
[    0.579857] cpuidle: using governor menu
[    0.580671] TCP cubic registered
[    0.580858] NET: Registered protocol family 10
[    0.581584] lo: Disabled Privacy Extensions
[    0.582009] NET: Registered protocol family 17
[    0.582100] Using IPI No-Shortcut mode
[    0.582250] PM: Resume from disk failed.
[    0.582279] registered taskstats version 1
[    0.582640]   Magic number: 6:676:494
[    0.582743] rtc_cmos 00:05: setting system clock to 2010-12-24 18:28:52 UTC (1293215332)
[    0.582773] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.582776] EDD information not available.
[    0.595406] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.737000] ata1.00: ATA-6: ST340014A, 3.76, max UDMA/100
[    0.737006] ata1.00: 78165360 sectors, multi 8: LBA48 
[    0.744665] ata2.00: ATAPI: PIONEER DVD-RW  DVR-118L, 1.01, max UDMA/100
[    0.744717] ata2.01: ATAPI: HL-DT-ST GCE-8481B, C102, max UDMA/33
[    0.744753] ata2.00: limited to UDMA/33 due to 40-wire cable
[    0.752623] ata1.00: configured for UDMA/100
[    0.760247] ata2.00: configured for UDMA/33
[    0.776392] ata2.01: configured for UDMA/33
[    0.907942] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.167826] isapnp: No Plug & Play device found
[    1.168094] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.76 PQ: 0 ANSI: 5
[    1.168360] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.168644] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.168714] sd 0:0:0:0: [sda] Write Protect is off
[    1.168719] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.168755] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.168988]  sda:
[    1.170442] usb 1-4: configuration #1 chosen from 1 choice
[    1.174949] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-118L 1.01 PQ: 0 ANSI: 5
[    1.177920]  sda1 sda2 <sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.199133] Uniform CD-ROM driver Revision: 3.20
[    1.199329] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.199436] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.200289]  sda5 >
[    1.200633] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  C102 PQ: 0 ANSI: 5
[    1.201038] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.204890] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.205077] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.205179] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.292174] Freeing initrd memory: 12875k freed
[    1.632018] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    1.792381] usb 4-2: config 1 interface 0 altsetting 0 has 1 endpoint descriptor, different from the interface descriptor's value: 0
[    1.810565] usb 4-2: configuration #1 chosen from 1 choice
[    2.384156] Freeing unused kernel memory: 656k freed
[    2.385131] Write protecting the kernel text: 4684k
[    2.385165] Write protecting the kernel read-only data: 1840k
[    2.421528] udev: starting version 151
[    2.737673] Floppy drive(s): fd0 is 1.44M
[    2.737961] Linux agpgart interface v0.103
[    2.754220] FDC 0 is a post-1991 82077
[    2.766990] vga16fb: initializing
[    2.766997] vga16fb: mapped to 0xc00a0000
[    2.767093] fb0: VGA16 VGA frame buffer device
[    2.789069] usbcore: registered new interface driver hiddev
[    2.789205] usbhid 4-2:1.0: couldn't find an input interrupt endpoint
[    2.802071]   alloc irq_desc for 21 on node -1
[    2.802077]   alloc kstat_irqs on node -1
[    2.802088] ohci1394 0000:02:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.807819] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.807824] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.813305] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    2.817898] input: SONiX USB Device as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4
[    2.818074] generic-usb 0003:0C45:7408.0001: input,hidraw0: USB HID v1.00 Mouse [SONiX USB Device] on usb-0000:00:1d.2-2/input1
[    2.819371] agpgart-intel 0000:00:00.0: AGP aperture is 32M @ 0xe8000000
[    2.915251] input: SONiX USB Device as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/input/input5
[    2.915407] generic-usb 0003:0C45:7408.0002: input,hidraw1: USB HID v1.00 Keyboard [SONiX USB Device] on usb-0000:00:1d.2-2/input2
[    2.915454] usbcore: registered new interface driver usbhid
[    2.915459] usbhid: v2.6:USB HID core driver
[    2.917092] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fcff5000-fcff57ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.931242]   alloc irq_desc for 20 on node -1
[    2.931247]   alloc kstat_irqs on node -1
[    2.931258] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.954294] e100 0000:02:08.0: PME# disabled
[    2.956141] e100: eth0: e100_probe: addr 0xfcff7000, irq 20, MAC addr 00:07:e9:72:9a:bb
[    2.956187] ohci1394 0000:02:01.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.015420] Console: switching to colour frame buffer device 80x30
[    3.022194] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fcff5800-fcff5fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.529342] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.200187] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[005042a13116e54a]
[    4.292183] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c00a100a2f3]
[   14.057551] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[   14.125980] udev: starting version 151
[   14.313429] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.340729] intel_rng: Firmware space is locked read-only. If you can't or
[   14.340732] intel_rng: don't want to disable this in firmware setup, and if
[   14.340734] intel_rng: you are certain that your system has a functional
[   14.340736] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   14.471123] lp: driver loaded but no devices found
[   14.684416] parport_pc 00:08: reported by Plug and Play ACPI
[   14.684471] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.780440] lp0: using parport0 (interrupt-driven).
[   14.986765] type=1505 audit(1293215346.901:2):  operation="profile_load" pid=518 name="/sbin/dhclient3"
[   14.987456] type=1505 audit(1293215346.901:3):  operation="profile_load" pid=518 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.987835] type=1505 audit(1293215346.901:4):  operation="profile_load" pid=518 name="/usr/lib/connman/scripts/dhclient-script"
[   15.109690] nvidia: module license 'NVIDIA' taints kernel.
[   15.109697] Disabling lock debugging due to kernel taint
[   15.419958] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.679768] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.679783] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.681494] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   15.775958] dell-wmi: No known WMI GUID found
[   15.780122] ppdev: user-space parallel port driver
[   15.782049] cfg80211: Calling CRDA to update world regulatory domain
[   15.890132] cfg80211: World regulatory domain updated:
[   15.890139]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.890144]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.890148]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.890151]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.890155]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.890159]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.198429] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.198489] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   16.222970] type=1505 audit(1293215348.137:5):  operation="profile_load" pid=666 name="/usr/share/gdm/guest-session/Xsession"
[   16.267471] type=1505 audit(1293215348.181:6):  operation="profile_replace" pid=667 name="/sbin/dhclient3"
[   16.281588] type=1505 audit(1293215348.197:7):  operation="profile_replace" pid=667 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.282008] type=1505 audit(1293215348.197:8):  operation="profile_replace" pid=667 name="/usr/lib/connman/scripts/dhclient-script"
[   16.326276]   alloc irq_desc for 22 on node -1
[   16.326281]   alloc kstat_irqs on node -1
[   16.326293] EMU10K1_Audigy 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.348619] Installing spdif_bug patch: SB Audigy 2 ZS [SB0353]
[   16.377060] type=1505 audit(1293215348.293:9):  operation="profile_load" pid=673 name="/usr/bin/evince"
[   16.417221] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.417448] phy0: Selected rate control algorithm 'minstrel'
[   16.418480] Registered led device: rt2800usb-phy0::radio
[   16.418508] Registered led device: rt2800usb-phy0::assoc
[   16.418533] Registered led device: rt2800usb-phy0::quality
[   16.419228] usbcore: registered new interface driver rt2800usb
[   16.420166] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   16.421256] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.436301] type=1505 audit(1293215348.353:10):  operation="profile_load" pid=673 name="/usr/bin/evince-previewer"
[   16.453436] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.475945] type=1505 audit(1293215348.389:11):  operation="profile_load" pid=673 name="/usr/bin/evince-thumbnailer"
[   16.493548] rtusb init --->
[   16.493735] usbcore: registered new interface driver rt2870
[   16.638552] rt2800usb 1-4:1.0: firmware: requesting rt2870.bin
[   16.672082] intel8x0_measure_ac97_clock: measured 53526 usecs (2579 samples)
[   16.672088] intel8x0: clocking to 48000
[   16.940693] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.282186] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   18.282209] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   18.282255] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   19.506294] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.639382] nf_conntrack version 0.5.0 (16028 buckets, 64112 max)
[   19.642293] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   19.642301] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   19.642304] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   25.816210] wlan0: Creating new IBSS network, BSSID 02:7e:82:43:15:72
[   26.748021] eth0: no IPv6 routers present
[   27.956018] wlan0: no IPv6 routers present
[   78.113823] padlock: VIA PadLock not detected.
[  278.816628] wlan0: Creating new IBSS network, BSSID 82:1f:80:c2:89:d2
[  339.000421] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  341.056176] wlan0: Trigger new scan to find an IBSS to join
[  341.465443] wlan0: Trigger new scan to find an IBSS to join
[  344.000270] wlan0: Trigger new scan to find an IBSS to join
[  348.000166] wlan0: Trigger new scan to find an IBSS to join
[  350.001015] wlan0: Creating new IBSS network, BSSID 36:1b:a5:1e:eb:c0
[  380.000220] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  440.000108] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  500.000254] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  560.000142] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  620.000237] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  680.000264] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  740.000141] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  800.000159] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  860.000176] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  920.000193] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  980.000210] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1040.000228] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1100.000119] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1160.000135] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1212.801255] usb 1-4: USB disconnect, address 2
[ 1212.840013] phy0 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[ 1274.596023] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 1274.754384] usb 1-4: configuration #1 chosen from 1 choice
[ 1274.794928] phy1: Selected rate control algorithm 'minstrel'
[ 1274.800432] Registered led device: rt2800usb-phy1::radio
[ 1274.801343] Registered led device: rt2800usb-phy1::assoc
[ 1274.802765] Registered led device: rt2800usb-phy1::quality
[ 1274.839154] rt2800usb 1-4:1.0: firmware: requesting rt2870.bin
[ 1275.038851] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1275.335386] wlan0: Trigger new scan to find an IBSS to join
[ 1278.000160] wlan0: Trigger new scan to find an IBSS to join
[ 1282.000038] wlan0: Trigger new scan to find an IBSS to join
[ 1284.000186] wlan0: Creating new IBSS network, BSSID 1e:f5:76:6e:33:ce
[ 1285.452023] wlan0: no IPv6 routers present
[ 1314.000269] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1374.000236] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1434.000127] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1494.000737] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1554.000288] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1614.000184] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1674.000196] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1677.993522] wlan0: Trigger new scan to find an IBSS to join
[ 1678.289955] wlan0: Trigger new scan to find an IBSS to join
[ 1681.000639] wlan0: Trigger new scan to find an IBSS to join
[ 1685.000379] wlan0: Trigger new scan to find an IBSS to join
[ 1687.000389] wlan0: Creating new IBSS network, BSSID ce:66:43:3b:be:a4
[ 1717.000436] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1777.000452] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1837.000270] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1897.000490] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1957.000377] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2017.000395] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2077.000416] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2137.000429] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2197.000493] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
peter@peter-desktop:~$ 
peter@peter-desktop:~$ sudo lshw -C network
[sudo] password for peter: 
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:07:e9:72:9a:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:fcff7000-fcff7fff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:de:7a:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11abgn
peter@peter-desktop:~$ 
peter@peter-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: CE:66:43:3B:BE:A4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"linksys_WPS_0502"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 725980ms ago
                    IE: Unknown: 00106C696E6B7379735F5750535F30353032
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C

peter@peter-desktop:~$ 
peter@peter-desktop:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS
peter@peter-desktop:~$ 

peter@peter-desktop:~$ uname -mr
2.6.32-27-generic i686
peter@peter-desktop:~$ 

peter@peter-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for peter: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
peter@peter-desktop:~$ 


*****PASTED COMMAND BUT I GOT NO OUTPUT*********
peter@peter-desktop:~$ lsmod | grep "linksys_WPA_0502"
peter@peter-desktop:~$

---

### Post by peterthinking on 2011-01-02
Nothing? It's been a week, sucked the internet cable into the vacuum twice already, can't count how many times I tripped over it. I want to use the wireless!

Please help.

---

### Post by cipherboy_loc on 2011-01-02
> **peterthinking said:**
> Nothing? It's been a week, sucked the internet cable into the vacuum twice already, can't count how many times I tripped over it. I want to use the wireless!

Please help.

Ah, I don't know anything about the specific Wireless Adapter, but try the Linux wireless drivers website (google it with the name of your adapter). Oh, and next time wrapthe output of each command in Code tags, it saves space when viewing it. Highlight the area you want to wrap in Code tags, and then hit the pound (#) symbol up along the top of the editor.

Cipherboy

---

### Post by PatchesTheCaveman on 2011-01-02
Hi peterthinking.  Happy New Year!

While plugged into a wired Ethernet Internet connection, run this command to install the rfkill package:
```
sudo apt-get update
sudo apt-get install rfkill
```

Then, run it:
```
sudo rfkill list
```

Does your wireless card show up as hard or soft blocked?  If so, run:
```
sudo rfkill unblock 0
```

See if it works then.  If not, let me know and I'll see what else we can do.

---

