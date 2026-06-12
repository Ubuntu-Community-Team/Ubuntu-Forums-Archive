---
title: "Trouble with  Intel PRO/Wireless 4965 AG or AGN"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by obamania on 2009-04-07
Hi,

I can't get my wifi card running properly. I am running Ubuntu 8.10 with wicd. My wireless card is an Intel PRO 4965 AGN. It works under a proprietary OS, but not with Ubuntu. 

One possible (!) source of trouble is, that I cannot switch the card on by any hardware switch. In Windows I can use a function key to enable the card. Ubuntu does not seem to support this. The BIOS does not enable the card at boot time either.

Below is some output that may help you help me help my laptop.

Thanks in advance and best regards,

jts


Here is the output:
hardware according to lspci:

0a:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


ifcofig:

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:24:8c:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-24-8C-A7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lsmod (does not list any wlan_module_name):

Module                  Size  Used by
af_packet              25728  2 
ipv6                  263972  10 
binfmt_misc            16904  1 
rfcomm                 44560  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
container              11520  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
iwlagn                 99844  0 
iwlcore                94532  1 iwlagn
rfkill                 17176  2 iwlcore
uvcvideo               63624  0 
pcspkr                 10624  0 
serio_raw              13444  0 
led_class              12164  1 iwlcore
psmouse                45200  0 
evdev                  17696  13 
compat_ioctl32          9344  1 uvcvideo
snd_hda_intel         384176  0 
videodev               41344  1 uvcvideo
mac80211              216820  2 iwlagn,iwlcore
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
v4l1_compat            22404  2 uvcvideo,videodev
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
nvidia               7082420  38 
i2c_core               31892  1 nvidia
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
ac                     12292  0 
battery                18436  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  25232  6 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
output                 11008  1 video
wmi                    14504  0 
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
button                 14224  0 
soundcore              15328  1 snd
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
sg                     39732  0 
usb_storage            82624  0 
libusual               30356  1 usb_storage
pata_acpi              12160  0 
ahci                   37132  2 
sata_sil24             21380  0 
ata_piix               24708  0 
libata                178208  5 ata_generic,pata_acpi,ahci,sata_sil24,ata_piix
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
r8169                  36100  0 
uhci_hcd               30864  0 
mii                    13440  1 r8169
usbcore               149488  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 




dmsg:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbfed0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781f000 - 37fef313
[    0.000000] ACPI: RSDP 000F7900, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BFED28EB, 0084 (r1 MEDION MEDIONAG  6040000 ZNEB        0)
[    0.000000] ACPI: FACP BFEDBC3A, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BFED3DA6, 7E20 (r2 WS     C46_____  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS BFEDEFC0, 0040
[    0.000000] ACPI: HPET BFEDBD2E, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BFEDBD66, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA BFEDBDA2, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR BFEDBDD4, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC BFEDBDFA, 0176 (r1 MEDION MEDIONAG  6040000 BENZ        1)
[    0.000000] ACPI: APIC BFEDBF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BFEDBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT BFED3AC9, 02DD (r1 SataRe SataAhci     1000 INTL 20060912)
[    0.000000] ACPI: SSDT BFED2EFB, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20060912)
[    0.000000] ACPI: SSDT BFED2E55, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20060912)
[    0.000000] ACPI: SSDT BFED296F, 04E6 (r1  PmRef    CpuPm     3000 INTL 20060912)
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781f000 - 0037fef313]          RAMDISK ==> [003781f000 - 0037fef313]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f7a50] 000f7a50
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bfed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
.....
.....
[   26.400562] Bluetooth: RFCOMM TTY layer initialized
[   26.400571] Bluetooth: RFCOMM ver 1.10
[   65.613834] CPU0 attaching NULL sched-domain.
[   65.613846] CPU1 attaching NULL sched-domain.
[   65.621066] CPU0 attaching sched-domain:
[   65.621071]  domain 0: span 0-1 level MC
[   65.621074]   groups: 0 1
[   65.621080] CPU1 attaching sched-domain:
[   65.621082]  domain 0: span 0-1 level MC
[   65.621084]   groups: 1 0
[   81.785745] wlan0: Failed to config new SSID to the low-level driver
[  110.923682] NET: Registered protocol family 10
[  110.924892] lo: Disabled Privacy Extensions
[  110.926215] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  110.927491] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.219717] r8169: eth0: link up
[  115.220060] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  125.509026] eth0: no IPv6 routers present
[  134.246701] NET: Registered protocol family 17
[  134.380272] r8169: eth0: link up
[  142.241985] iwlagn 0000:0a:00.0: PCI INT A disabled
[  142.248435] iwlagn 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  142.248542] iwlagn 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  142.248775] iwlagn: Radio disabled by HW RF Kill switch
[  142.251386] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  142.390674] r8169: eth0: link up
[  144.170691] r8169: eth0: link up
[  145.076396] r8169: eth0: link up
[  155.800036] eth0: no IPv6 routers present
[  318.033117] CE: hpet increasing min_delta_ns to 15000 nsec



lshw -C network:

Framebuffer devices       
  *-network        
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:16:02:68:c6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.35 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:24:8c:a7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:8f:8d:20:c8:6d
       capabilities: ethernet physical
       configuration: 





iwlist scan:

wlan0     No scan results

---

### Post by stardustdk on 2009-04-07
It seems to me that you do dualboot. I have a Laptop with 3945ABG, that works like yours 4965AGN. M$ XP can turn the wireless on/off, Ubuntu can't. My suggestion: Turn the wireless on for good and go into Ubuntu. 

If you can't live with that, I am sorry to to tell you, that the best you can do is changing to another laptop.

BTW: It is a Fujitsu Siemens V3505 AMILO Pro of mine that works that way.

I have a LG laptop with 3945ABG too, that works perfectly regarding turning the wireless on/off.

I don't know if this helps.

Best regards

Stardustdk

---

### Post by CyberMando on 2009-04-07
I have a laptop with that same card, but mine does have a switch. I can tell you that Linux is recognizing you card and loading the correct modules
mac80211 216820 2 iwlagn,iwlcore
That is very promising. The lshw output shows that you have an ethernet card as well. Ubuntu is likely to enable the ethernet if it is connected and disable the wireless. There is also a whole slew of problems with the current network-manager and its applets. One that often shows up is the inability to do WEP.

I suggest you try
sudo aptitude install wicd
Wicd is very reliable and easy. If you can't get it to go with wicd you might have to look for module options that allow you to turn the chip on.

---

### Post by hal10000 on 2009-04-07
After a recent upgrade from hardy to intrepid my Intel PRO/wireless 4965 stopped working, but after i installed the two packages [COLOR="Red"]linux-headers-lbm-2.6.27-14-generic[/COLOR] and [COLOR="Red"]linux-backports-modules-2.6.27-14-generic[/COLOR] everything works well again.

You have to enable the intrepid-proposed and intrepid-backport sources with your package-manager (in the update-section).

I hope this can help you getting your wireless working.

---

### Post by stchman on 2009-04-07
SO the ONLY way to enable the wireless card is through software on Windows XP?

What kind of laptop is this?  Maybe there is a wireless on/off option in the BIOS.

---

