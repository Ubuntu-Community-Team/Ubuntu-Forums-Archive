---
title: "Unable to enable Wireless on Ubuntu 8.10"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by Straumoy on 2009-04-05
Hello,

I've problems enabling wireless network on my laptop. When I right-click on the NetworkManager icon, the Enable Wireless check option is greyed out. I've already looked around in this section and tried some of the things mentioned in the various threads, but ended up with no changes (that I know of anyway). 

So I ended up making this thread, containing all the information I could dig up. I'd like to apologise that I was unable to filter out the specific information as suggested by the various hints, but I'm terrible with terminal commands so there you have it. Again, I'm sorry.

From what I understand, my wireless should work right out of the box, like my wired connection does (just stuff in a cable, wait 5 seconds and I'm online). Still I've never got wireless to work, regardless of what version of Ubuntu I've been using. 

There is a button just left of the power button on my laptop that has a ball with 2 curves over it, and a light with the same icon on the far right side of the laptop. I assume this is the wireless button, though pressing it just once or holding it down for a period of time doesn't bring up the light. All this is located just over the keyboard of the laptop.

With no further delay, the information stuff:


**1 ) Machine Brand and Model (PC/Laptop):**
Medion - dunno if this is enough, bug me for details if you need them.

**2 ) Wireless Brand, Model and Wireless Chipset:**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**3 ) check interface:**
eth0      Link encap:Ethernet  HWaddr 00:16:d3:61:38:ae  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe61:38ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4816557 (4.8 MB)  TX bytes:512675 (512.6 KB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extension

**4 ) Check for modules:**
Module                  Size  Used by
cdc_wdm                17536  0 
cdc_ether              13312  0 
usbnet                 24072  1 cdc_ether
cdc_acm                23584  0 
ipv6                  263972  10 
af_packet              25728  2 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  2 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  3 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
iwl3945                98804  0 
lirc_atiusb            24352  0 
snd_seq_dummy          10884  0 
rfkill                 17176  2 iwl3945
lirc_dev               20020  1 lirc_atiusb
serio_raw              13444  0 
snd_seq_oss            38528  0 
evdev                  17696  12 
mac80211              216820  1 iwl3945
ati_remote             18056  0 
psmouse                45200  0 
sdhci_pci              15360  0 
pcspkr                 10624  0 
snd_seq_midi           14336  0 
sdhci                  23940  1 sdhci_pci
led_class              12164  1 iwl3945
ricoh_mmc              11904  0 
mmc_core               58268  1 sdhci
nvidia               6909268  38 
cfg80211               32392  2 iwl3945,mac80211
iTCO_wdt               18596  0 
ac                     12292  0 
i2c_core               31892  1 nvidia
snd_rawmidi            29824  1 snd_seq_midi
iTCO_vendor_support    11652  1 iTCO_wdt
battery                18436  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  25232  6 
output                 11008  1 video
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi                    14504  0 
button                 14224  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_generic            12932  0 
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  0 
ahci                   37132  2 
pata_acpi              12160  0 
ohci1394               37936  0 
libata                178208  4 ata_generic,ata_piix,ahci,pata_acpi
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43788  0 
r8169                  36100  0 
mii                    13440  2 usbnet,r8169
uhci_hcd               30736  0 
usbcore               149360  10 cdc_wdm,cdc_ether,usbnet,cdc_acm,lirc_atiusb,ati_remote,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

**5 ) Kernel boot messages**
[    0.601758] PCI: bridge 0000:00:1c.1 io port: [3000, 3fff]
[    0.601764] PCI: bridge 0000:00:1c.1 32bit mmio: [d6000000, d7ffffff]
[    0.601773] PCI: bridge 0000:00:1c.1 64bit mmio pref: [d2000000, d3ffffff]
[    0.601960] PCI: 0000:06:00.0 reg 10 32bit mmio: [da000000, da000fff]
[    0.602169] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.602183] pci 0000:06:00.0: PME# disabled
[    0.602239] PCI: bridge 0000:00:1c.3 32bit mmio: [da000000, da0fffff]
[    0.602310] PCI: 0000:0a:09.0 reg 10 32bit mmio: [da100000, da1007ff]
[    0.602367] pci 0000:0a:09.0: supports D1
[    0.602369] pci 0000:0a:09.0: supports D2
[    0.602372] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602378] pci 0000:0a:09.0: PME# disabled
[    0.602416] PCI: 0000:0a:09.1 reg 10 32bit mmio: [da100800, da1008ff]
[    0.602473] pci 0000:0a:09.1: supports D1
[    0.602476] pci 0000:0a:09.1: supports D2
[    0.602478] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602484] pci 0000:0a:09.1: PME# disabled
[    0.602524] PCI: 0000:0a:09.2 reg 10 32bit mmio: [da100c00, da100cff]
[    0.602580] pci 0000:0a:09.2: supports D1
[    0.602583] pci 0000:0a:09.2: supports D2
[    0.602586] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602591] pci 0000:0a:09.2: PME# disabled
[    0.602629] PCI: 0000:0a:09.3 reg 10 32bit mmio: [da101000, da1010ff]
[    0.602686] pci 0000:0a:09.3: supports D1
[    0.602688] pci 0000:0a:09.3: supports D2
[    0.602691] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602697] pci 0000:0a:09.3: PME# disabled
[    0.602736] PCI: 0000:0a:09.4 reg 10 32bit mmio: [da101400, da1014ff]
[    0.602795] pci 0000:0a:09.4: supports D1
[    0.602797] pci 0000:0a:09.4: supports D2
[    0.602800] pci 0000:0a:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602806] pci 0000:0a:09.4: PME# disabled
[    0.602855] pci 0000:00:1e.0: transparent bridge
[    0.602863] PCI: bridge 0000:00:1e.0 32bit mmio: [da100000, da1fffff]
[    0.602900] bus 00 -> node 0
[    0.602909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.603370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.603559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.603741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.603925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.604137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.624474] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *7
[    0.624474] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *3
[    0.624474] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.624582] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    0.624722] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.624863] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.625003] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.625145] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *5
[    0.625228] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.625228] pnp: PnP ACPI init
[    0.625228] ACPI: bus type pnp registered
[    0.629044] pnp: PnP ACPI: found 10 devices
[    0.629044] ACPI: ACPI bus type pnp unregistered
[    0.629044] PnPBIOS: Disabled by ACPI PNP
[    0.632063] PCI: Using ACPI for IRQ routing
[    0.636044] NET: Registered protocol family 8
[    0.636047] NET: Registered protocol family 20
[    0.636067] NetLabel: Initializing
[    0.636067] NetLabel:  domain hash size = 128
[    0.636067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.636078] NetLabel:  unlabeled traffic allowed by default
[    0.636217] hpet clockevent registered
[    0.636224] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.636230] hpet0: 3 64-bit timers, 14318180 Hz
[    0.637882] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.637885]    actual entries 65620
[    0.637981] AppArmor: AppArmor Filesystem Enabled
[    0.638010] ACPI: RTC can wake from S4
[    0.644055] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.644059] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.644063] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.644067] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.644072] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.644076] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.644080] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    0.644084] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.644094] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.644098] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.644102] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.644106] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.644109] system 00:05: ioport range 0x1200-0x120f has been reserved
[    0.644116] system 00:06: ioport range 0x6a0-0x6af has been reserved
[    0.644120] system 00:06: ioport range 0x6b0-0x6ff has been reserved
[    0.679388] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    0.679392] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.679395] pci 0000:00:01.0:   IO window: disabled
[    0.679401] pci 0000:00:01.0:   MEM window: 0xd8000000-0xd9ffffff
[    0.679405] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.679412] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.679416] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.679424] pci 0000:00:1c.0:   MEM window: 0xd4000000-0xd5ffffff
[    0.679430] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.679440] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.679444] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.679452] pci 0000:00:1c.1:   MEM window: 0xd6000000-0xd7ffffff
[    0.679458] pci 0000:00:1c.1:   PREFETCH window: 0x000000d2000000-0x000000d3ffffff
[    0.679467] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.679470] pci 0000:00:1c.3:   IO window: disabled
[    0.679477] pci 0000:00:1c.3:   MEM window: 0xda000000-0xda0fffff
[    0.679483] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.679493] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    0.679495] pci 0000:00:1e.0:   IO window: disabled
[    0.679502] pci 0000:00:1e.0:   MEM window: 0xda100000-0xda1fffff
[    0.679508] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.679526] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.679531] pci 0000:00:01.0: setting latency timer to 64
[    0.679542] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.679548] pci 0000:00:1c.0: setting latency timer to 64
[    0.679558] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.679564] pci 0000:00:1c.1: setting latency timer to 64
[    0.679575] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.679581] pci 0000:00:1c.3: setting latency timer to 64
[    0.679590] pci 0000:00:1e.0: setting latency timer to 64
[    0.679595] bus: 00 index 0 io port: [0, ffff]
[    0.679598] bus: 00 index 1 mmio: [0, ffffffff]
[    0.679601] bus: 01 index 0 mmio: [0, 0]
[    0.679604] bus: 01 index 1 mmio: [d8000000, d9ffffff]
[    0.679607] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.679609] bus: 01 index 3 mmio: [0, 0]
[    0.679612] bus: 02 index 0 io port: [2000, 2fff]
[    0.679615] bus: 02 index 1 mmio: [d4000000, d5ffffff]
[    0.679618] bus: 02 index 2 mmio: [d0000000, d1ffffff]
[    0.679621] bus: 02 index 3 mmio: [0, 0]
[    0.679623] bus: 04 index 0 io port: [3000, 3fff]
[    0.679626] bus: 04 index 1 mmio: [d6000000, d7ffffff]
[    0.679629] bus: 04 index 2 mmio: [d2000000, d3ffffff]
[    0.679632] bus: 04 index 3 mmio: [0, 0]
[    0.679635] bus: 06 index 0 mmio: [0, 0]
[    0.679637] bus: 06 index 1 mmio: [da000000, da0fffff]
[    0.679640] bus: 06 index 2 mmio: [0, 0]
[    0.679642] bus: 06 index 3 mmio: [0, 0]
[    0.679645] bus: 0a index 0 mmio: [0, 0]
[    0.679648] bus: 0a index 1 mmio: [da100000, da1fffff]
[    0.679651] bus: 0a index 2 mmio: [0, 0]
[    0.679653] bus: 0a index 3 io port: [0, ffff]
[    0.679656] bus: 0a index 4 mmio: [0, ffffffff]
[    0.679666] NET: Registered protocol family 2
[    0.692093] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.692368] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.692873] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.693147] TCP: Hash tables configured (established 131072 bind 65536)
[    0.693151] TCP reno registered
[    0.700130] NET: Registered protocol family 1
[    0.700269] checking if image is initramfs... it is
[    1.136661] Switched to high resolution mode on CPU 1
[    1.140057] Switched to high resolution mode on CPU 0
[    1.543093] Freeing initrd memory: 8011k freed
[    1.543489] Simple Boot Flag at 0x36 set to 0x1
[    1.544505] audit: initializing netlink socket (disabled)
[    1.544533] type=2000 audit(1238955772.544:1): initialized
[    1.552272] highmem bounce pool size: 64 pages
[    1.552279] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.555343] VFS: Disk quotas dquot_6.5.1
[    1.555450] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.555574] msgmni has been set to 1761
[    1.555721] io scheduler noop registered
[    1.555725] io scheduler anticipatory registered
[    1.555728] io scheduler deadline registered
[    1.555743] io scheduler cfq registered (default)
[    1.555878] pci 0000:01:00.0: Boot video device
[    1.556026] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.556066] pcieport-driver 0000:00:01.0: found MSI capability
[    1.556100] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.556155] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.556256] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.556306] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.556355] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.556409] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.556461] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.556587] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.556637] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.556686] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.556740] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.556791] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.556914] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.556963] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.557017] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.557072] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.557123] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.557553] isapnp: Scanning for PnP cards...
[    1.912016] isapnp: No Plug & Play device found
[    1.956248] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.959083] brd: module loaded
[    1.959174] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.959328] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.959702] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.959783] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.959790] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.959795] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.959799] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.959802] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.960234] mice: PS/2 mouse device common for all mice
[    1.960403] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.960435] rtc0: alarms up to one month, y3k, hpet irqs
[    1.960597] EISA: Probing bus 0 at eisa.0
[    1.960605] Cannot allocate resource for EISA slot 1
[    1.960609] Cannot allocate resource for EISA slot 2
[    1.960612] Cannot allocate resource for EISA slot 3
[    1.960637] EISA: Detected 0 cards.
[    1.960641] cpuidle: using governor ladder
[    1.960644] cpuidle: using governor menu
[    1.961287] TCP cubic registered
[    1.961327] Using IPI No-Shortcut mode
[    1.961551] registered taskstats version 1
[    1.961721]   Magic number: 5:95:392
[    1.961794] acpi PNP0C0D:00: hash matches
[    1.961833] rtc_cmos 00:07: setting system clock to 2009-04-05 18:22:54 UTC (1238955774)
[    1.961838] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.961840] EDD information not available.
[    1.962106] Freeing unused kernel memory: 424k freed
[    1.962164] Write protecting the kernel text: 2580k
[    1.962199] Write protecting the kernel read-only data: 940k
[    1.963036] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.205160] fuse init (API version 7.9)
[    2.245665] ACPI: SSDT 3FE91E23, 01A8 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.246126] ACPI: SSDT 3FE91BD3, 01CB (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.246818] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.246887] processor ACPI0007:00: registered as cooling_device0
[    2.247347] ACPI: SSDT 3FE91FCB, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.247779] ACPI: SSDT 3FE91D9E, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.248510] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.248569] processor ACPI0007:01: registered as cooling_device1
[    2.251895] Marking TSC unstable due to TSC halts in idle
[    2.636122] Clocksource tsc unstable (delta = -200096725 ns)
[    2.756999] thermal LNXTHERM:01: registered as thermal_zone0
[    2.765494] ACPI: Thermal Zone [TZS0] (34 C)
[    2.769684] thermal LNXTHERM:02: registered as thermal_zone1
[    2.772810] ACPI: Thermal Zone [TZS1] (38 C)
[    3.107017] usbcore: registered new interface driver usbfs
[    3.107046] usbcore: registered new interface driver hub
[    3.107099] usbcore: registered new device driver usb
[    3.109799] USB Universal Host Controller Interface driver v3.0
[    3.109855] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.109866] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.109871] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.109921] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.109961] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    3.110144] usb usb1: configuration #1 chosen from 1 choice
[    3.110177] hub 1-0:1.0: USB hub found
[    3.110186] hub 1-0:1.0: 2 ports detected
[    3.193746] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.207498] No dock devices found.
[    3.225977] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.225990] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.225996] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.226040] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.226083] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    3.226251] usb usb2: configuration #1 chosen from 1 choice
[    3.226290] hub 2-0:1.0: USB hub found
[    3.226299] hub 2-0:1.0: 2 ports detected
[    3.279543] SCSI subsystem initialized
[    3.306043] libata version 3.00 loaded.
[    3.436350] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.436362] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.436367] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.436399] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.436440] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    3.436559] usb usb3: configuration #1 chosen from 1 choice
[    3.436592] hub 3-0:1.0: USB hub found
[    3.436601] hub 3-0:1.0: 2 ports detected
[    3.545026] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    3.640470] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.640482] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.640487] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.640518] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.640561] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    3.640682] usb usb4: configuration #1 chosen from 1 choice
[    3.640715] hub 4-0:1.0: USB hub found
[    3.640724] hub 4-0:1.0: 2 ports detected
[    3.717279] usb 2-2: configuration #1 chosen from 1 choice
[    3.744649] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.744666] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.744670] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.744717] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.748644] ehci_hcd 0000:00:1d.7: debug port 1
[    3.748653] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.748664] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xda404000
[    3.836069] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.844079] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.844350] usb usb5: configuration #1 chosen from 1 choice
[    3.844420] hub 5-0:1.0: USB hub found
[    3.844430] hub 5-0:1.0: 8 ports detected
[    3.900100] hub 3-0:1.0: unable to enumerate USB device on port 1
[    3.900138] usb 2-2: USB disconnect, address 2
[    4.053547] pata_acpi 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.053584] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.053601] pata_acpi 0000:00:1f.1: PCI INT B disabled
[    4.053640] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.053656] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.053674] r8169 0000:04:00.0: setting latency timer to 64
[    4.054117] eth0: RTL8101e at 0xf88ac000, 00:16:d3:61:38:ae, XID 34000000 IRQ 219
[    4.055338] ahci 0000:00:1f.2: version 3.0
[    4.055350] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.055453] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    4.055458] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    4.055465] ahci 0000:00:1f.2: setting latency timer to 64
[    4.055639] scsi0 : ahci
[    4.055844] scsi1 : ahci
[    4.056119] scsi2 : ahci
[    4.056746] scsi3 : ahci
[    4.056880] ata1: SATA max UDMA/133 abar m1024@0xda404400 port 0xda404500 irq 218
[    4.056884] ata2: DUMMY
[    4.056887] ata3: SATA max UDMA/133 abar m1024@0xda404400 port 0xda404600 irq 218
[    4.056890] ata4: DUMMY
[    4.372131] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.373261] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.373369] ata1.00: ATA-7: ST9160821AS, 3.ALB, max UDMA/133
[    4.373373] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.374638] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.374753] ata1.00: configured for UDMA/133
[    4.404119] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    4.578665] usb 2-2: configuration #1 chosen from 1 choice
[    4.708129] ata3: SATA link down (SStatus 0 SControl 300)
[    4.724363] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
[    4.724568] ohci1394 0000:0a:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.777316] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[da100000-da1007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.785826] ata_piix 0000:00:1f.1: version 2.12
[    4.785838] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.785886] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.787015] scsi4 : ata_piix
[    4.787376] scsi5 : ata_piix
[    4.788141] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    4.788145] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    4.795482] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.817177] Driver 'sd' needs updating - please use bus_type methods
[    4.817306] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.817328] sd 0:0:0:0: [sda] Write Protect is off
[    4.817331] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.817365] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.817453] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.817472] sd 0:0:0:0: [sda] Write Protect is off
[    4.817476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.817510] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.817514]  sda:<6>usb 3-1: new low speed USB device using uhci_hcd and address 3
[    4.845650]  sda1 sda2 < sda5 >
[    4.874379] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.972633] ata5.00: ATAPI: TSSTcorpCD/DVDW SN-S082D, SS03, max UDMA/33
[    5.004574] ata5.00: configured for UDMA/33
[    5.004644] ata6: port disabled. ignoring.
[    5.013171] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SN-S082D SS03 PQ: 0 ANSI: 5
[    5.013363] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    5.023628] usb 3-1: configuration #1 chosen from 1 choice
[    5.050796] usbcore: registered new interface driver hiddev
[    5.062214] Driver 'sr' needs updating - please use bus_type methods
[    5.089859] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input2
[    5.090189] input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1d.2-1
[    5.090214] usbcore: registered new interface driver usbhid
[    5.090219] usbhid: v2.6:USB HID core driver
[    5.108301] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.108307] Uniform CD-ROM driver Revision: 3.20
[    5.108418] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.267474] PM: Starting manual resume from disk
[    5.267479] PM: Resume from partition 8:5
[    5.267481] PM: Checking hibernation image.
[    5.267631] PM: Resume from disk failed.
[    5.337340] kjournald starting.  Commit interval 5 seconds
[    5.337352] EXT3-fs: mounted filesystem with ordered data mode.
[    6.052416] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a0047496044]
[   12.987105] udevd version 124 started
[   13.524166] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.628521] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.688853] Linux agpgart interface v0.103
[   13.904319] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.924042] ACPI: Power Button (FF) [PWRF]
[   13.924177] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   13.925203] ACPI: Lid Switch [LID0]
[   13.925295] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   13.956041] ACPI: Sleep Button (CM) [SLPB]
[   13.988229] ACPI: WMI: Mapper loaded
[   14.176053] intel_rng: FWH not detected
[   14.300706] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[   14.316602] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.465129] iTCO_vendor_support: vendor-support=0
[   14.637158] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.637259] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.637393] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.845889] nvidia: module license 'NVIDIA' taints kernel.
[   15.161684] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.161694] nvidia 0000:01:00.0: setting latency timer to 64
[   15.161937] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   15.163248] ricoh-mmc: Ricoh MMC Controller disabling driver
[   15.163253] ricoh-mmc: Copyright(c) Philip Langdale
[   15.179256] ricoh-mmc: Ricoh MMC controller found at 0000:0a:09.2 [1180:0843] (rev 1)
[   15.179279] ricoh-mmc: Controller is now disabled.
[   15.186598] ACPI: EC: GPE storm detected, transactions will use polling mode
[   15.285350] sdhci: Secure Digital Host Controller Interface driver
[   15.285354] sdhci: Copyright(c) Pierre Ossman
[   15.329551] ACPI: Battery Slot [BAT0] (battery present)
[   15.330887] ACPI: AC Adapter [ADP1] (on-line)
[   15.361031] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   15.366543] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 19)
[   15.366562] sdhci-pci 0000:0a:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.369636] mmc0: SDHCI controller on PCI [0000:0a:09.1] using PIO
[   15.455231] input: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/input/input8
[   15.487124] ati_remote: Weird data, len=1 ff 00 00 00 00 00 ...
[   15.524896] usbcore: registered new interface driver ati_remote
[   15.524901] ati_remote: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[   15.635532] lirc_dev: IR Remote Control driver registered, major 61 
[   15.711644] 
[   15.711646] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
[   15.711650] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   15.761276] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   15.761281] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   15.761399] iwl3945 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.761415] iwl3945 0000:06:00.0: setting latency timer to 64
[   15.761439] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   15.829489] usbcore: registered new interface driver lirc_atiusb
[   15.853300] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   15.853813] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.995359] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   16.025099] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   16.277321] iwl3945 0000:06:00.0: PCI INT A disabled
[   16.294581] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   16.294599] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.294632] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.016277] lp: driver loaded but no devices found
[   17.183081] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   17.730656] EXT3 FS on sda1, internal journal
[   18.914592] type=1505 audit(1238955791.058:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4261
[   19.766956] type=1505 audit(1238955791.909:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4266
[   19.767193] type=1505 audit(1238955791.909:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4266
[   19.962663] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.778225] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.867420] apm: BIOS not found.
[   22.028392] ppdev: user-space parallel port driver
[   24.664047] Bluetooth: Core ver 2.13
[   24.664749] NET: Registered protocol family 31
[   24.664756] Bluetooth: HCI device and connection manager initialized
[   24.664763] Bluetooth: HCI socket layer initialized
[   24.708597] Bluetooth: L2CAP ver 2.11
[   24.708607] Bluetooth: L2CAP socket layer initialized
[   24.748285] Bluetooth: SCO (Voice Link) ver 0.6
[   24.748295] Bluetooth: SCO socket layer initialized
[   24.797849] Bluetooth: RFCOMM socket layer initialized
[   24.802971] Bluetooth: RFCOMM TTY layer initialized
[   24.802981] Bluetooth: RFCOMM ver 1.10
[   24.803237] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.803242] Bluetooth: BNEP filters: protocol multicast
[   24.878327] Bridge firewalling registered
[   28.941565] r8169: eth0: link up
[   28.941574] r8169: eth0: link up
[   28.944283] iwl3945 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   28.944433] iwl3945 0000:06:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   28.946248] firmware: requesting iwlwifi-3945-1.ucode
[   30.382351] iwl3945: Radio disabled by HW RF Kill switch
[   30.383625] iwl3945 0000:06:00.0: PCI INT A disabled
[   30.399311] iwl3945 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   30.399477] iwl3945 0000:06:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   30.399773] iwl3945: Radio disabled by HW RF Kill switch
[   30.399848] iwl3945 0000:06:00.0: PCI INT A disabled
[   30.577212] NET: Registered protocol family 17
[   37.368650] NET: Registered protocol family 10
[   37.369325] lo: Disabled Privacy Extensions
[   47.404075] eth0: no IPv6 routers present
[   62.714884] CPU0 attaching NULL sched-domain.
[   62.714908] CPU1 attaching NULL sched-domain.
[   62.716418] CPU0 attaching sched-domain:
[   62.716427]  domain 0: span 0-1 level MC
[   62.716433]   groups: 0 1
[   62.716444] CPU1 attaching sched-domain:
[   62.716450]  domain 0: span 0-1 level MC
[   62.716455]   groups: 1 0
[  279.286428] r8169: eth0: link down
[  335.952173] usb 2-1: new full speed USB device using uhci_hcd and address 4
[  336.140669] usb 2-1: configuration #3 chosen from 1 choice
[  336.429068] cdc_acm 2-1:3.1: ttyACM0: USB ACM device
[  336.431429] cdc_acm 2-1:3.3: ttyACM1: USB ACM device
[  336.433325] usbcore: registered new interface driver cdc_acm
[  336.433996] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  336.476231] usb0: register 'cdc_ether' at usb-0000:00:1d.1-1, CDC Ethernet Device, 02:80:37:15:03:00
[  336.476591] usbcore: registered new interface driver cdc_ether
[  336.478765] cdc_wdm 2-1:3.7: cdc-wdm0: USB WDM device
[  336.479331] usbcore: registered new interface driver cdc_wdm
[  351.844117] usb0: no IPv6 routers present
[  423.818537] r8169: eth0: link up
[  429.704213] usb 2-1: USB disconnect, address 4
[  429.712834] uhci_hcd 0000:00:1d.1: dma_pool_free buffer-2048, e4cc7180/24cc7180 (bad dma)
[  429.713531] usb0: unregister 'cdc_ether' usb-0000:00:1d.1-1, CDC Ethernet Device
[  637.640225] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  637.640250] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  637.640256]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  637.640262]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  637.640275] ata5.00: status: { DRDY }
[  642.680127] ata5: link is slow to respond, please be patient (ready=0)
[  647.668149] ata5: device not ready (errno=-16), forcing hardreset
[  647.668173] ata5: soft resetting link
[  647.880654] ata5.00: configured for UDMA/33
[  647.880682] ata5: EH complete
[  803.612239] ata5.00: qc timeout (cmd 0xa0)
[  803.612262] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  803.612279] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  803.612282]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  803.612285]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[  803.612292] ata5.00: status: { DRDY ERR }
[  808.664170] ata5: link is slow to respond, please be patient (ready=0)
[  813.648117] ata5: device not ready (errno=-16), forcing hardreset
[  813.648141] ata5: soft resetting link
[  813.861629] ata5.00: configured for UDMA/33
[  813.861676] ata5: EH complete
[  933.612233] ata5.00: qc timeout (cmd 0xa0)
[  933.612257] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  933.612273] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  933.612276]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  933.612279]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[  933.612287] ata5.00: status: { DRDY ERR }
[  938.652180] ata5: link is slow to respond, please be patient (ready=0)
[  943.641057] ata5: device not ready (errno=-16), forcing hardreset
[  943.641078] ata5: soft resetting link
[  943.853490] ata5.00: configured for UDMA/33
[  943.853525] ata5: EH complete

**6 ) Network configuration**
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d3:61:38:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.111 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:81:a9:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:84:03:29:68:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**7 ) Scan for networks:**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scannin

**8 ) Ubuntu Version: **
Description:	Ubuntu 8.10

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
2.6.27-11-generic i686

**10 ) Restarting the network:**
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.
                                                                                                                                                      [ OK ]

---

### Post by Cybie257 on 2009-04-05
First, try going to:

   System -> Administration -> Hardware Drivers

Check if there is a WIFI adapter that needs to be enabled. That was a problem with a few laptops I've encountered.

Second, might want to check out the users manual and verify how to enable to the WIFI hardware on your laptop. See what signifies that it is turned on. If you don't have it turned on, then there is now way for the OS to see it and enable it. You should have some sort of indication that it is on via the status light(s) on your laptop.

-Cybie

---

### Post by Straumoy on 2009-04-06
> **Cybie257 said:**
> First, try going to:

   System -> Administration -> Hardware Drivers

Check if there is a WIFI adapter that needs to be enabled. That was a problem with a few laptops I've encountered.

Second, might want to check out the users manual and verify how to enable to the WIFI hardware on your laptop. See what signifies that it is turned on. If you don't have it turned on, then there is now way for the OS to see it and enable it. You should have some sort of indication that it is on via the status light(s) on your laptop.

-Cybie
Confirmed that I have a Medion md 96223 laptop. After some looking around I managed to dig up a users manual and confirmed what I've suspected - you need to push the button I described in my first post to activate it.

Giving that this doesn't respond to anything, I guess this case is pretty much lost. Unless there's some magic back-door I can use (BIOS or whatever) to activate it. 

Just for kicks I also checked System -> Administration -> Hardware Drivers and only found NVIDIA driver, already enabled.

---

### Post by afkneebone on 2010-05-19
Look in the bios.   Wireless is off by default.   Only other option (dumb) is 'same state'.   It can only be enabled using software.   You will need to install Windows, install the software to turn the wifi on.   Then erradicate windows and reinstall linux.

---

### Post by Geffers on 2010-05-19
> **Cybie257 said:**
> First, try going to:

   System -> Administration -> Hardware Drivers

Check if there is a WIFI adapter that needs to be enabled. That was a problem with a few laptops I've encountered.

Second, might want to check out the users manual and verify how to enable to the WIFI hardware on your laptop. See what signifies that it is turned on. If you don't have it turned on, then there is now way for the OS to see it and enable it. You should have some sort of indication that it is on via the status light(s) on your laptop.

-Cybie

My Acer Aspire ONE netbook has a wifi switch  that illuminated and worked well under the default Linpus OS but when I installed Ubuntu the switch or light doesn't work although the wifi is fine.

Geffers

---

