---
title: "Dell D400 builtin wireless not seeing network/ubuntu8.1"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by Evaeth on 2009-01-20
Hello

I installed Ubuntu 8.1 onto a D400 latitude laptop. The laptop comes with a internal wireless nic. I see that Ubuntu installed the drivers for it but I can't see the wireless network with it. I come from a heavy Windows background so if you have a solution for me, please describe in detail on how to resolve this issue. Here is some more information below. Thanks for your time.

-------
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---------
 ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:fe:e2:d5  

          inet addr:192.168.10.100  Bcast:192.168.10.127  Mask:255.255.255.128

          inet6 addr: fe80::20f:1fff:fefe:e2d5/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:344 errors:0 dropped:0 overruns:0 frame:0

          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:435403 (435.4 KB)  TX bytes:41200 (41.2 KB)

          Interrupt:11 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:6 errors:0 dropped:0 overruns:0 frame:0

          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

---------
 iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:""  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=0 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.


 lsmod

Module                  Size  Used by

ipv6                  263972  8 

af_packet              25728  4 

rfkill_input           12672  0 

i915                   38144  2 

drm                    86056  3 i915

binfmt_misc            16904  1 

sco                    18308  2 

bridge                 56980  0 

rfcomm                 44432  0 

stp                    10628  1 bridge

bnep                   20480  2 

l2cap                  30464  6 rfcomm,bnep

bluetooth              61924  6 sco,rfcomm,bnep,l2cap

ppdev                  15620  0 

acpi_cpufreq           15500  0 

cpufreq_userspace      11396  0 

cpufreq_conservative    14600  0 

cpufreq_powersave       9856  0 

cpufreq_stats          13188  0 

cpufreq_ondemand       14988  1 

freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand

sbs                    19464  0 

pci_slot               12552  0 

container              11520  0 

wmi                    14504  0 

sbshc                  13440  1 sbs

iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables

sbp2                   29324  0 

lp                     17156  0 

joydev                 18368  0 

pcmcia                 43052  0 

arc4                    9984  2 

ecb                    10880  2 

crypto_blkcipher       25476  1 ecb

b43                   131356  0 

rfkill                 17176  2 rfkill_input,b43

dcdbas                 15008  0 

mac80211              216820  1 b43

evdev                  17696  13 

psmouse                45200  0 

cfg80211               32392  1 mac80211

serio_raw              13444  0 

led_class              12164  1 b43

input_polldev          11912  1 b43

pcspkr                 10624  0 

snd_intel8x0           37532  3 

snd_ac97_codec        111652  1 snd_intel8x0

yenta_socket           31756  2 

rsrc_nonstatic         19072  1 yenta_socket

pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic

ac97_bus                9856  1 snd_ac97_codec

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

video                  25104  0 

output                 11008  1 video

snd_seq_dummy          10884  0 

parport_pc             39204  1 

parport                42604  3 ppdev,lp,parport_pc

snd_seq_oss            38528  0 

snd_seq_midi           14336  0 

snd_rawmidi            29824  1 snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

button                 14224  0 

battery                18436  0 

ac                     12292  0 

snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              15328  1 snd

iTCO_wdt               18596  0 

iTCO_vendor_support    11652  1 iTCO_wdt

snd_page_alloc         16136  2 snd_intel8x0,snd_pcm

shpchp                 37908  0 

pci_hotplug            35236  1 shpchp

intel_agp              33724  1 

agpgart                42184  3 drm,intel_agp

ext3                  133384  1 

jbd                    55444  1 ext3

mbcache                16004  1 ext3

sd_mod                 42264  3 

crc_t10dif              9984  1 sd_mod

sg                     39732  0 

ata_generic            12932  0 

pata_acpi              12160  0 

usbhid                 35840  0 

hid                    50560  1 usbhid

ata_piix               24580  2 

ssb                    40580  1 b43

ohci1394               37936  0 

libata                177312  3 ata_generic,pata_acpi,ata_piix

tg3                   129924  0 

libphy                 27392  1 tg3

uhci_hcd               30736  0 

ieee1394               96324  2 sbp2,ohci1394

ehci_hcd               43276  0 

scsi_mod              155212  4 sbp2,sd_mod,sg,libata

usbcore               148848  4 usbhid,uhci_hcd,ehci_hcd

dock                   16656  1 libata

thermal                23708  0 

processor              42156  3 acpi_cpufreq,thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  3 


dmesg
7 (0xe000-0xefff), disabling

[    0.587335] pnp: PnP ACPI: found 14 devices

[    0.587338] ACPI: ACPI bus type pnp unregistered

[    0.587343] PnPBIOS: Disabled by ACPI PNP

[    0.587740] PCI: Using ACPI for IRQ routing

[    0.587869] NET: Registered protocol family 8

[    0.587869] NET: Registered protocol family 20

[    0.587869] NetLabel: Initializing

[    0.587869] NetLabel:  domain hash size = 128

[    0.587869] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.588039] NetLabel:  unlabeled traffic allowed by default

[    0.588366] tracer: 772 pages allocated for 65536 entries of 48 bytes

[    0.588370]    actual entries 65620

[    0.588477] AppArmor: AppArmor Filesystem Enabled

[    0.588501] system 00:00: iomem range 0x0-0x9fbff could not be reserved

[    0.588501] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved

[    0.588501] system 00:00: iomem range 0xc0000-0xcffff could not be reserved

[    0.588501] system 00:00: iomem range 0xe0000-0xfffff could not be reserved

[    0.588501] system 00:00: iomem range 0x100000-0x3feeffff could not be reserved

[    0.588501] system 00:00: iomem range 0x3fef0000-0x3fefffff could not be reserved

[    0.588501] system 00:00: iomem range 0xfec10000-0xfec1ffff could not be reserved

[    0.588501] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved

[    0.588501] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved

[    0.588501] system 00:02: ioport range 0x4d0-0x4d1 has been reserved

[    0.588501] system 00:03: ioport range 0xf400-0xf4fe has been reserved

[    0.588501] system 00:03: ioport range 0x880-0x8bf has been reserved

[    0.588501] system 00:03: ioport range 0x8c0-0x8df has been reserved

[    0.588501] system 00:03: ioport range 0x8e0-0x8ff has been reserved

[    0.588501] system 00:08: ioport range 0x900-0x97f has been reserved

[    0.588501] system 00:0d: ioport range 0x7b0-0x7bb has been reserved

[    0.588501] system 00:0d: ioport range 0x7c0-0x7df has been reserved

[    0.588501] system 00:0d: ioport range 0xbb0-0xbbb has been reserved

[    0.588501] system 00:0d: ioport range 0xbc0-0xbdf has been reserved

[    0.588501] system 00:0d: ioport range 0xfb0-0xfbb has been reserved

[    0.588501] system 00:0d: ioport range 0xfc0-0xfdf has been reserved

[    0.588501] system 00:0d: ioport range 0x13b0-0x13bb has been reserved

[    0.588501] system 00:0d: ioport range 0x13c0-0x13df has been reserved

[    0.588501] system 00:0d: ioport range 0x17b0-0x17bb has been reserved

[    0.588501] system 00:0d: ioport range 0x17c0-0x17df has been reserved

[    0.588501] system 00:0d: ioport range 0x1bb0-0x1bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x1bc0-0x1bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x1fb0-0x1fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x1fc0-0x1fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x23b0-0x23bb has been reserved

[    0.588501] system 00:0d: ioport range 0x23c0-0x23df has been reserved

[    0.588501] system 00:0d: ioport range 0x27b0-0x27bb has been reserved

[    0.588501] system 00:0d: ioport range 0x27c0-0x27df has been reserved

[    0.588501] system 00:0d: ioport range 0x2bb0-0x2bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x2bc0-0x2bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x2fb0-0x2fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x2fc0-0x2fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x33b0-0x33bb has been reserved

[    0.588501] system 00:0d: ioport range 0x33c0-0x33df has been reserved

[    0.588501] system 00:0d: ioport range 0x37b0-0x37bb has been reserved

[    0.588501] system 00:0d: ioport range 0x37c0-0x37df has been reserved

[    0.588501] system 00:0d: ioport range 0x3bb0-0x3bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x3bc0-0x3bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x3fb0-0x3fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x3fc0-0x3fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x43b0-0x43bb has been reserved

[    0.588501] system 00:0d: ioport range 0x43c0-0x43df has been reserved

[    0.588501] system 00:0d: ioport range 0x47b0-0x47bb has been reserved

[    0.588501] system 00:0d: ioport range 0x47c0-0x47df has been reserved

[    0.588501] system 00:0d: ioport range 0x4bb0-0x4bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x4bc0-0x4bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x4fb0-0x4fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x4fc0-0x4fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x53b0-0x53bb has been reserved

[    0.588501] system 00:0d: ioport range 0x53c0-0x53df has been reserved

[    0.588501] system 00:0d: ioport range 0x57b0-0x57bb has been reserved

[    0.588501] system 00:0d: ioport range 0x57c0-0x57df has been reserved

[    0.588501] system 00:0d: ioport range 0x5bb0-0x5bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x5bc0-0x5bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x5fb0-0x5fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x5fc0-0x5fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x63b0-0x63bb has been reserved

[    0.588501] system 00:0d: ioport range 0x63c0-0x63df has been reserved

[    0.588501] system 00:0d: ioport range 0x67b0-0x67bb has been reserved

[    0.588501] system 00:0d: ioport range 0x67c0-0x67df has been reserved

[    0.588501] system 00:0d: ioport range 0x6bb0-0x6bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x6bc0-0x6bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x6fb0-0x6fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x6fc0-0x6fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x73b0-0x73bb has been reserved

[    0.588501] system 00:0d: ioport range 0x73c0-0x73df has been reserved

[    0.588501] system 00:0d: ioport range 0x77b0-0x77bb has been reserved

[    0.588501] system 00:0d: ioport range 0x77c0-0x77df has been reserved

[    0.588501] system 00:0d: ioport range 0x7bb0-0x7bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x7bc0-0x7bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x7fb0-0x7fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x7fc0-0x7fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x83b0-0x83bb has been reserved

[    0.588501] system 00:0d: ioport range 0x83c0-0x83df has been reserved

[    0.588501] system 00:0d: ioport range 0x87b0-0x87bb has been reserved

[    0.588501] system 00:0d: ioport range 0x87c0-0x87df has been reserved

[    0.588501] system 00:0d: ioport range 0x8bb0-0x8bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x8bc0-0x8bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x8fb0-0x8fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x8fc0-0x8fdf has been reserved

[    0.588501] system 00:0d: ioport range 0x93b0-0x93bb has been reserved

[    0.588501] system 00:0d: ioport range 0x93c0-0x93df has been reserved

[    0.588501] system 00:0d: ioport range 0x97b0-0x97bb has been reserved

[    0.588501] system 00:0d: ioport range 0x97c0-0x97df has been reserved

[    0.588501] system 00:0d: ioport range 0x9bb0-0x9bbb has been reserved

[    0.588501] system 00:0d: ioport range 0x9bc0-0x9bdf has been reserved

[    0.588501] system 00:0d: ioport range 0x9fb0-0x9fbb has been reserved

[    0.588501] system 00:0d: ioport range 0x9fc0-0x9fdf has been reserved

[    0.588501] system 00:0d: ioport range 0xa3b0-0xa3bb has been reserved

[    0.588501] system 00:0d: ioport range 0xa3c0-0xa3df has been reserved

[    0.588501] system 00:0d: ioport range 0xa7b0-0xa7bb has been reserved

[    0.588501] system 00:0d: ioport range 0xa7c0-0xa7df has been reserved

[    0.588501] system 00:0d: ioport range 0xabb0-0xabbb has been reserved

[    0.588501] system 00:0d: ioport range 0xabc0-0xabdf has been reserved

[    0.588501] system 00:0d: ioport range 0xafb0-0xafbb has been reserved

[    0.588501] system 00:0d: ioport range 0xafc0-0xafdf has been reserved

[    0.588501] system 00:0d: ioport range 0xb3b0-0xb3bb has been reserved

[    0.588501] system 00:0d: ioport range 0xb3c0-0xb3df has been reserved

[    0.588501] system 00:0d: ioport range 0xb7b0-0xb7bb has been reserved

[    0.588501] system 00:0d: ioport range 0xb7c0-0xb7df has been reserved

[    0.588501] system 00:0d: ioport range 0xbbb0-0xbbbb has been reserved

[    0.588501] system 00:0d: ioport range 0xbbc0-0xbbdf has been reserved

[    0.588501] system 00:0d: ioport range 0xbfb0-0xbfbb has been reserved

[    0.588501] system 00:0d: ioport range 0xbfc0-0xbfdf has been reserved

[    0.588501] system 00:0d: ioport range 0xc3b0-0xc3bb has been reserved

[    0.588501] system 00:0d: ioport range 0xc3c0-0xc3df has been reserved

[    0.588505] system 00:0d: ioport range 0xc7b0-0xc7bb has been reserved

[    0.588509] system 00:0d: ioport range 0xc7c0-0xc7df has been reserved

[    0.588514] system 00:0d: ioport range 0xcbb0-0xcbbb has been reserved

[    0.588518] system 00:0d: ioport range 0xcbc0-0xcbdf has been reserved

[    0.588522] system 00:0d: ioport range 0xcfb0-0xcfbb has been reserved

[    0.588527] system 00:0d: ioport range 0xcfc0-0xcfdf has been reserved

[    0.588531] system 00:0d: ioport range 0xd3b0-0xd3bb has been reserved

[    0.588536] system 00:0d: ioport range 0xd3c0-0xd3df has been reserved

[    0.588540] system 00:0d: ioport range 0xd7b0-0xd7bb has been reserved

[    0.588544] system 00:0d: ioport range 0xd7c0-0xd7df has been reserved

[    0.588549] system 00:0d: ioport range 0xdbb0-0xdbbb has been reserved

[    0.588553] system 00:0d: ioport range 0xdbc0-0xdbdf has been reserved

[    0.588558] system 00:0d: ioport range 0xdfb0-0xdfbb has been reserved

[    0.588562] system 00:0d: ioport range 0xdfc0-0xdfdf has been reserved

[    0.588572] system 00:0d: ioport range 0xf3b0-0xf3bb has been reserved

[    0.588577] system 00:0d: ioport range 0xf3c0-0xf3df has been reserved

[    0.588581] system 00:0d: ioport range 0xf7b0-0xf7bb has been reserved

[    0.588586] system 00:0d: ioport range 0xf7c0-0xf7df has been reserved

[    0.588590] system 00:0d: ioport range 0xfbb0-0xfbbb has been reserved

[    0.588595] system 00:0d: ioport range 0xfbc0-0xfbdf has been reserved

[    0.588600] system 00:0d: ioport range 0xffb0-0xffbb has been reserved

[    0.588604] system 00:0d: ioport range 0xffc0-0xffdf has been reserved

[    0.624233] pci 0000:01:01.0: CardBus bridge, secondary bus 0000:02

[    0.624237] pci 0000:01:01.0:   IO window: 0x00e000-0x00e0ff

[    0.624242] pci 0000:01:01.0:   IO window: 0x00e400-0x00e4ff

[    0.624247] pci 0000:01:01.0:   PREFETCH window: 0x50000000-0x53ffffff

[    0.624252] pci 0000:01:01.0:   MEM window: 0x5c000000-0x5fffffff

[    0.624257] pci 0000:01:01.1: CardBus bridge, secondary bus 0000:06

[    0.624260] pci 0000:01:01.1:   IO window: 0x00e800-0x00e8ff

[    0.624264] pci 0000:01:01.1:   IO window: 0x001000-0x0010ff

[    0.624269] pci 0000:01:01.1:   PREFETCH window: 0x54000000-0x57ffffff

[    0.624274] pci 0000:01:01.1:   MEM window: 0x60000000-0x63ffffff

[    0.624279] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01

[    0.624283] pci 0000:00:1e.0:   IO window: 0xe000-0xefff

[    0.624289] pci 0000:00:1e.0:   MEM window: 0xfc000000-0xfdffffff

[    0.624295] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000059ffffff

[    0.624310] pci 0000:00:1e.0: setting latency timer to 64

[    0.624318] pci 0000:01:01.0: enabling device (0000 -> 0003)

[    0.624551] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11

[    0.624555] PCI: setting IRQ 11 as level-triggered

[    0.624560] pci 0000:01:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11

[    0.624572] pci 0000:01:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11

[    0.624578] bus: 00 index 0 io port: [0, ffff]

[    0.624581] bus: 00 index 1 mmio: [0, ffffffff]

[    0.624584] bus: 01 index 0 io port: [e000, efff]

[    0.624587] bus: 01 index 1 mmio: [fc000000, fdffffff]

[    0.624590] bus: 01 index 2 mmio: [50000000, 59ffffff]

[    0.624592] bus: 01 index 3 io port: [0, ffff]

[    0.624595] bus: 01 index 4 mmio: [0, ffffffff]

[    0.624598] bus: 02 index 0 io port: [e000, e0ff]

[    0.624600] bus: 02 index 1 io port: [e400, e4ff]

[    0.624603] bus: 02 index 2 mmio: [50000000, 53ffffff]

[    0.624606] bus: 02 index 3 mmio: [5c000000, 5fffffff]

[    0.624609] bus: 06 index 0 io port: [e800, e8ff]

[    0.624611] bus: 06 index 1 io port: [1000, 10ff]

[    0.624614] bus: 06 index 2 mmio: [54000000, 57ffffff]

[    0.624617] bus: 06 index 3 mmio: [60000000, 63ffffff]

[    0.624627] NET: Registered protocol family 2

[    0.624774] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.625062] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.626077] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    0.626763] TCP: Hash tables configured (established 131072 bind 65536)

[    0.626768] TCP reno registered

[    0.626966] NET: Registered protocol family 1

[    0.627147] checking if image is initramfs... it is

[    1.128089] Switched to high resolution mode on CPU 0

[    1.494414] Freeing initrd memory: 8008k freed

[    1.495294] audit: initializing netlink socket (disabled)

[    1.495321] type=2000 audit(1232481206.492:1): initialized

[    1.503147] highmem bounce pool size: 64 pages

[    1.503157] HugeTLB registered 4 MB page size, pre-allocated 0 pages

[    1.506077] VFS: Disk quotas dquot_6.5.1

[    1.506189] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    1.506330] msgmni has been set to 1761

[    1.506490] io scheduler noop registered

[    1.506494] io scheduler anticipatory registered

[    1.506497] io scheduler deadline registered

[    1.506512] io scheduler cfq registered (default)

[    1.506538] pci 0000:00:02.0: Boot video device

[    1.507033] isapnp: Scanning for PnP cards...

[    1.859603] isapnp: No Plug & Play device found

[    1.901869] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

[    1.902005] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    1.902824] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    1.903310] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5

[    1.903315] PCI: setting IRQ 5 as level-triggered

[    1.903320] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5

[    1.903329] serial 0000:00:1f.6: PCI INT B disabled

[    1.905322] brd: module loaded

[    1.905411] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[    1.905571] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

[    1.910408] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.910417] serio: i8042 AUX port at 0x60,0x64 irq 12

[    1.910803] mice: PS/2 mouse device common for all mice

[    1.910969] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0

[    1.910988] rtc0: alarms up to one day

[    1.911131] EISA: Probing bus 0 at eisa.0

[    1.911140] Cannot allocate resource for EISA slot 1

[    1.911167] EISA: Detected 0 cards.

[    1.911171] cpuidle: using governor ladder

[    1.911174] cpuidle: using governor menu

[    1.911811] TCP cubic registered

[    1.911847] Using IPI No-Shortcut mode

[    1.912103] registered taskstats version 1

[    1.912256]   Magic number: 9:825:900

[    1.912337] tty ptyvd: hash matches

[    1.912400] acpi PNP0501:00: hash matches

[    1.912435] rtc_cmos 00:06: setting system clock to 2009-01-20 19:53:27 UTC (1232481207)

[    1.912440] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    1.912442] EDD information not available.

[    1.912752] Freeing unused kernel memory: 424k freed

[    1.912810] Write protecting the kernel text: 2576k

[    1.912844] Write protecting the kernel read-only data: 936k

[    1.916171] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

[    2.158022] fuse init (API version 7.9)

[    2.265412] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])

[    2.265483] processor ACPI0007:00: registered as cooling_device0

[    2.265489] ACPI: Processor [CPU0] (supports 8 throttling states)

[    2.269978] thermal LNXTHERM:01: registered as thermal_zone0

[    2.273198] ACPI: Thermal Zone [THM] (53 C)

[    2.872502] ACPI: ACPI Dock Station Driver

[    3.025710] usbcore: registered new interface driver usbfs

[    3.025742] usbcore: registered new interface driver hub

[    3.025795] usbcore: registered new device driver usb

[    3.090998] SCSI subsystem initialized

[    3.091390] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11

[    3.091396] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11

[    3.091413] ehci_hcd 0000:00:1d.7: setting latency timer to 64

[    3.091417] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[    3.091486] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1

[    3.095396] ehci_hcd 0000:00:1d.7: debug port 1

[    3.095403] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported

[    3.095413] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfaeffc00

[    3.119154] USB Universal Host Controller Interface driver v3.0

[    3.124206] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[    3.124467] usb usb1: configuration #1 chosen from 1 choice

[    3.124503] hub 1-0:1.0: USB hub found

[    3.124514] hub 1-0:1.0: 6 ports detected

[    3.228100] libata version 3.00 loaded.

[    3.332953] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11

[    3.332960] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11

[    3.332976] uhci_hcd 0000:00:1d.0: setting latency timer to 64

[    3.332981] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[    3.333025] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2

[    3.333057] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80

[    3.333174] usb usb2: configuration #1 chosen from 1 choice

[    3.333211] hub 2-0:1.0: USB hub found

[    3.333221] hub 2-0:1.0: 2 ports detected

[    3.436451] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11

[    3.436468] uhci_hcd 0000:00:1d.1: setting latency timer to 64

[    3.436472] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[    3.436501] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3

[    3.436526] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40

[    3.436645] usb usb3: configuration #1 chosen from 1 choice

[    3.436679] hub 3-0:1.0: USB hub found

[    3.436688] hub 3-0:1.0: 2 ports detected

[    3.644745] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11

[    3.644752] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11

[    3.644768] uhci_hcd 0000:00:1d.2: setting latency timer to 64

[    3.644772] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[    3.644803] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4

[    3.644830] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20

[    3.644957] usb usb4: configuration #1 chosen from 1 choice

[    3.644994] hub 4-0:1.0: USB hub found

[    3.645005] hub 4-0:1.0: 2 ports detected

[    3.700007] Marking TSC unstable due to TSC halts in idle

[    3.748458] ata_piix 0000:00:1f.1: version 2.12

[    3.748472] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)

[    3.748481] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11

[    3.748536] ata_piix 0000:00:1f.1: setting latency timer to 64

[    3.748877] scsi0 : ata_piix

[    3.749268] scsi1 : ata_piix

[    3.749500] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14

[    3.749503] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15

[    3.756040] usb 3-2: new low speed USB device using uhci_hcd and address 2

[    3.912542] ata1.00: ATA-6: HTS548040M9AT00, MG2OA5EA, max UDMA/100

[    3.912547] ata1.00: 78140160 sectors, multi 8: LBA48 

[    3.928465] ata1.00: configured for UDMA/100

[    3.955756] usb 3-2: configuration #1 chosen from 1 choice

[    4.084219] scsi 0:0:0:0: Direct-Access     ATA      HTS548040M9AT00  MG2O PQ: 0 ANSI: 5

[    4.084424] tg3.c:v3.94 (August 14, 2008)

[    4.084437] tg3 0000:01:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11

[    4.198315] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0f:1f:fe:e2:d5

[    4.198321] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]

[    4.198325] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]

[    4.198438] ohci1394 0000:01:01.2: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11

[    4.248188] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fcfef800-fcfeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[    4.270693] b43-pci-bridge 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5

[    4.274463] ssb: Sonics Silicon Backplane found on PCI device 0000:01:03.0

[    4.275724] usbcore: registered new interface driver hiddev

[    4.295164] scsi 0:0:0:0: Attached scsi generic sg0 type 0

[    4.311275] Driver 'sd' needs updating - please use bus_type methods

[    4.311424] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)

[    4.311452] sd 0:0:0:0: [sda] Write Protect is off

[    4.311456] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.311501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.311597] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)

[    4.311622] sd 0:0:0:0: [sda] Write Protect is off

[    4.311625] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.311670] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.311675]  sda:<6>input: HID 1241:1177 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input2

[    4.328265] input,hidraw0: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1d.1-2

[    4.328292] usbcore: registered new interface driver usbhid

[    4.328297] usbhid: v2.6:USB HID core driver

[    4.331130]  sda1 sda2 < sda5 >

[    4.355240] sd 0:0:0:0: [sda] Attached SCSI disk

[    4.594724] PM: Starting manual resume from disk

[    4.594729] PM: Resume from partition 8:5

[    4.594731] PM: Checking hibernation image.

[    4.594885] PM: Resume from disk failed.

[    4.659567] kjournald starting.  Commit interval 5 seconds

[    4.659583] EXT3-fs: mounted filesystem with ordered data mode.

[    5.540196] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc0000326e4c1]

[   13.168437] udevd version 124 started

[   14.088887] Linux agpgart interface v0.103

[   14.143672] agpgart-intel 0000:00:00.0: Intel 855GM Chipset

[   14.144208] agpgart-intel 0000:00:00.0: detected 892K stolen memory

[   14.207794] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000

[   14.344598] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   14.398861] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   14.445607] intel_rng: FWH not detected

[   14.599084] iTCO_vendor_support: vendor-support=0

[   14.624580] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)

[   14.624747] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)

[   14.624958] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

[   14.730596] ACPI: AC Adapter [AC] (on-line)

[   15.101176] ACPI: Battery Slot [BAT0] (battery present)

[   15.101431] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3

[   15.101842] ACPI: Lid Switch [LID]

[   15.101940] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4

[   15.112047] ACPI: Power Button (CM) [PBTN]

[   15.112246] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5

[   15.124047] ACPI: Sleep Button (CM) [SBTN]

[   16.151447] parport_pc 00:0c: reported by Plug and Play ACPI

[   16.151502] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]

[   16.331534] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/input/input6

[   16.340060] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

[   16.340261] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:23/input/input7

[   16.356056] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)

[   17.019456] Yenta: CardBus bridge found at 0000:01:01.0 [1028:0139]

[   17.019475] Yenta: Using CSCINT to route CSC interrupts to PCI

[   17.019478] Yenta: Routing CardBus interrupts to PCI

[   17.019483] Yenta TI: socket 0000:01:01.0, mfunc 0x012c1202, devctl 0x64

[   17.248611] Yenta: ISA IRQ mask 0x0458, PCI irq 11

[   17.248617] Socket status: 30000006

[   17.248621] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05

[   17.248630] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff

[   17.248633] cs: IO port probe 0xe000-0xefff: clean.

[   17.249284] pcmcia: parent PCI bridge Memory window: 0xfc000000 - 0xfdffffff

[   17.249288] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x59ffffff

[   17.261054] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5

[   17.261087] Intel ICH 0000:00:1f.5: setting latency timer to 64

[   17.261119] Yenta: CardBus bridge found at 0000:01:01.1 [1028:0139]

[   17.292417] input: PC Speaker as /devices/platform/pcspkr/input/input8

[   17.388622] Yenta: ISA IRQ mask 0x0458, PCI irq 11

[   17.388628] Socket status: 30000047

[   17.388632] Yenta: Raising subordinate bus# of parent bus (#01) from #05 to #09

[   17.388640] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff

[   17.388643] cs: IO port probe 0xe000-0xefff: clean.

[   17.389293] pcmcia: parent PCI bridge Memory window: 0xfc000000 - 0xfdffffff

[   17.389297] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x59ffffff

[   17.880242] b43-phy0: Broadcom 4306 WLAN found

[   17.929996] phy0: Selected rate control algorithm 'pid'

[   18.084367] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]

[   18.088163] intel8x0_measure_ac97_clock: measured 55570 usecs

[   18.088167] intel8x0: clocking to 48000

[   18.152582] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9

[   18.201373] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10

[   18.224581] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)

[   19.763135] cs: IO port probe 0x100-0x3af: clean.

[   19.763958] cs: IO port probe 0x3e0-0x4ff: clean.

[   19.764333] cs: IO port probe 0x820-0x8ff: clean.

[   19.764388] cs: IO port probe 0xc00-0xcf7: clean.

[   19.764842] cs: IO port probe 0xa00-0xaff: clean.

[   19.805175] cs: IO port probe 0x100-0x3af: clean.

[   19.805994] cs: IO port probe 0x3e0-0x4ff: clean.

[   19.806349] cs: IO port probe 0x820-0x8ff: clean.

[   19.806404] cs: IO port probe 0xc00-0xcf7: clean.

[   19.806856] cs: IO port probe 0xa00-0xaff: clean.

[   20.170588] lp0: using parport0 (interrupt-driven).

[   20.278457] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k

[   20.817783] EXT3 FS on sda1, internal journal

[   21.910658] type=1505 audit(1232481227.869:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3980

[   22.150807] type=1505 audit(1232481228.109:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3985

[   22.151206] type=1505 audit(1232481228.109:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3985

[   22.346643] ip_tables: (C) 2000-2006 Netfilter Core Team

[   23.103642] ACPI: WMI: Mapper loaded

[   24.196433] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)

[   24.269781] apm: BIOS not found.

[   24.448569] ppdev: user-space parallel port driver

[   25.624043] Clocksource tsc unstable (delta = -106021857 ns)

[   26.430051] Bluetooth: Core ver 2.13

[   26.432673] NET: Registered protocol family 31

[   26.432691] Bluetooth: HCI device and connection manager initialized

[   26.432697] Bluetooth: HCI socket layer initialized

[   26.509282] Bluetooth: L2CAP ver 2.11

[   26.509293] Bluetooth: L2CAP socket layer initialized

[   26.547543] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[   26.547555] Bluetooth: BNEP filters: protocol multicast

[   26.619669] Bluetooth: RFCOMM socket layer initialized

[   26.619943] Bluetooth: RFCOMM TTY layer initialized

[   26.619950] Bluetooth: RFCOMM ver 1.10

[   26.636794] Bridge firewalling registered

[   26.637179] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.

[   26.670071] Bluetooth: SCO (Voice Link) ver 0.6

[   26.670079] Bluetooth: SCO socket layer initialized

[   30.310243] [drm] Initialized drm 1.1.0 20060810

[   30.325784] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11

[   30.325796] pci 0000:00:02.0: setting latency timer to 64

[   30.326820] [drm] Initialized i915 1.6.0 20060119 on minor 0

[   30.326837] pci 0000:00:02.1: setting latency timer to 64

[   30.330796] [drm] Initialized i915 1.6.0 20060119 on minor 1

[   31.173687] input: b43-phy0 as /devices/virtual/input/input11

[   31.244062] firmware: requesting b43/ucode5.fw

[   31.301917] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found

[   31.301927] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).

[   31.379712] input: b43-phy0 as /devices/virtual/input/input12

[   31.424189] firmware: requesting b43/ucode5.fw

[   31.426934] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found

[   31.426945] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).

[   31.647048] NET: Registered protocol family 17

[   32.880058] tg3: eth0: Link is up at 100 Mbps, full duplex.

[   32.880071] tg3: eth0: Flow control is off for TX and off for RX.

[   43.072969] NET: Registered protocol family 10

[   43.075258] lo: Disabled Privacy Extensions

[   53.800042] eth0: no IPv6 routers present

[  137.158465] ppdev0: registered pardevice

[  137.208640] ppdev0: unregistered pardevice

[  137.264205] ppdev0: registered pardevice

[  137.312060] ppdev0: unregistered pardevice

[  138.050495] ppdev0: registered pardevice

[  138.100331] ppdev0: unregistered pardevice


sudo lshw -C network

[sudo] password for schan: 

  *-network:0             

       description: Ethernet interface

       product: NetXtreme BCM5705M Gigabit Ethernet

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth0

       version: 01

       serial: 00:0f:1f:fe:e2:d5

       size: 100MB/s

       capacity: 1GB/s

       width: 64 bits

       clock: 66MHz

       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.11 ip=192.168.10.100 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s

  *-network:1

       description: Network controller

       product: BCM4306 802.11b/g Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 3

       bus info: pci@0000:01:03.0

       version: 03

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master

       configuration: driver=b43-pci-bridge latency=32 module=ssb

  *-network:0 DISABLED

       description: Wireless interface

       physical id: 2

       logical name: wlan0

       serial: 00:0b:7d:17:81:0c

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

  *-network:1 DISABLED

       description: Ethernet interface

       physical id: 3

       logical name: pan0

       serial: fa:e8:a4:9c:9b:a2

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



wlan0     No scan results



pan0      Interface doesn't support scanning.


 lsb_release -d

Description:	Ubuntu 8.10


 uname -mr

2.6.27-9-generic i686


sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

                                                                         [ OK ]

---

