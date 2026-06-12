---
title: "wlan0 can't be enabled (SIOCSIFFLAGS: No such file or directory), Cat5 NIC not  found"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by patricio2626 on 2010-10-05
Hi all,

 I just installed Ubuntu 10.4 on my Dell Inspiron N7010, and am having trouble networking.  

ifconfig -s

shows my loopback interface only, and

ifconfig -a

shows my loopback, as well as my wlan0 interface:

Link encap:Ethernet  HWaddr 00:23:15:22:47:c4
BROADCAST MULTICAST MTU:1500 Metrick1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0B)

so, when I try to bring wlan0 up:

me@my-pc:~$sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

Also,
me@my-pc:~4 iwconfig
lo   no wireless extensions.
wlan0   IEEE 802.11abgn ESSID: off/any
           Mode: Managed Access Point: Not-Associated Tx-Power=15 dBm
           Retry long limit:7 RTS thr: off Fragment thr: off
           Power Management: off

If I left-click on the wireless icon, I see, above 'VPN Connections',  the string, 'device not ready'.  If I hover over it, I get the tooltip,  'no network connection'.  Right-clicking shows networking, wireless, and  notifications enabled, and 'Connection Information' is grayed-out.  

System -> Administration -> Hardware drivers shows 'No proprietary  drivers are in use on this system', but again, I have no Internet  access, so I'm not sure what would load if I did.

The above sentence brings me to my next point:  I have a hardwired NIC  on the computer, and ifconfig does not show it at all, and no magic  happens when I plug an Ethernet cable into the NIC.  I, therefore, have  no connectivity at all.  

Other debugging:

pb@pb-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 1 8
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 1 8
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 57)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
pb@pb-pc:~$ lsusb
Bus 002 Device 004: ID 8086:0188 Intel Corp. 
Bus 002 Device 003: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6480 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pb@pb-pc:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203310  1 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               56990  0 
i915                  285076  3 
dell_wmi                1793  0 
iwlagn                105694  0 
videodev               34361  1 uvcvideo
drm_kms_helper         29297  1 i915
snd                    54148  17  snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
iwlcore               105922  1 iwlagn
led_class               2864  1 iwlcore
dell_laptop             6856  0 
soundcore               6620  1 snd
psmouse                63245  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
dcdbas                  5422  1 dell_laptop
mac80211              205146  2 iwlagn,iwlcore
cfg80211              126517  3 iwlagn,iwlcore,mac80211
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  1 
ahci                   32200  2 
pb@pb-pc:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203310  1 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               56990  0 
i915                  285076  3 
dell_wmi                1793  0 
iwlagn                105694  0 
videodev               34361  1 uvcvideo
drm_kms_helper         29297  1 i915
snd                    54148  17  snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
iwlcore               105922  1 iwlagn
led_class               2864  1 iwlcore
dell_laptop             6856  0 
soundcore               6620  1 snd
psmouse                63245  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
dcdbas                  5422  1 dell_laptop
mac80211              205146  2 iwlagn,iwlcore
cfg80211              126517  3 iwlagn,iwlcore,mac80211
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  1 
ahci                   32200  2 
pb@pb-pc:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc  version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28  06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bb27c000 - 00000000bb282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb282000 - 00000000bb3e6000 (usable)
[    0.000000]  BIOS-e820: 00000000bb3e6000 - 00000000bb40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb40f000 - 00000000bb46f000 (usable)
[    0.000000]  BIOS-e820: 00000000bb46f000 - 00000000bb470000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb470000 - 00000000bb4f1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb4f1000 - 00000000bb70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb70f000 - 00000000bb717000 (usable)
[    0.000000]  BIOS-e820: 00000000bb717000 - 00000000bb71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb71f000 - 00000000bb77e000 (usable)
[    0.000000]  BIOS-e820: 00000000bb77e000 - 00000000bb79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb79f000 - 00000000bb7e2000 (usable)
[    0.000000]  BIOS-e820: 00000000bb7e2000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  BIOS-e820: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0605000 - 00000000f0606000 (reserved)
[    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000017c000000 (usable)
[    0.000000]  BIOS-e820: 0000000180000000 - 00000001bc000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbb800 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask F80000000 write-back
[    0.000000]   4 base 180000000 mask FC0000000 write-back
[    0.000000]   5 base 1BC000000 mask FFC000000 uncachable
[    0.000000]   6 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bb27c000 (usable)
[    0.000000]  modified: 00000000bb27c000 - 00000000bb282000 (reserved)
[    0.000000]  modified: 00000000bb282000 - 00000000bb3e6000 (usable)
[    0.000000]  modified: 00000000bb3e6000 - 00000000bb40f000 (reserved)
[    0.000000]  modified: 00000000bb40f000 - 00000000bb46f000 (usable)
[    0.000000]  modified: 00000000bb46f000 - 00000000bb470000 (reserved)
[    0.000000]  modified: 00000000bb470000 - 00000000bb4f1000 (ACPI NVS)
[    0.000000]  modified: 00000000bb4f1000 - 00000000bb70f000 (reserved)
[    0.000000]  modified: 00000000bb70f000 - 00000000bb717000 (usable)
[    0.000000]  modified: 00000000bb717000 - 00000000bb71f000 (reserved)
[    0.000000]  modified: 00000000bb71f000 - 00000000bb77e000 (usable)
[    0.000000]  modified: 00000000bb77e000 - 00000000bb79f000 (ACPI NVS)
[    0.000000]  modified: 00000000bb79f000 - 00000000bb7e2000 (usable)
[    0.000000]  modified: 00000000bb7e2000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  modified: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  modified: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000f0605000 - 00000000f0606000 (reserved)
[    0.000000]  modified: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 000000017c000000 (usable)
[    0.000000]  modified: 0000000180000000 - 00000001bc000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37859000 - 37fef801
[    0.000000] Allocated new RAMDISK: 008e0000 - 01076801
[    0.000000] Move RAMDISK from 0000000037859000 - 0000000037fef800 to 008e0000 - 01076800
[    0.000000] ACPI: RSDP 000f6fa0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bb7f4697 00074 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP bb7e4000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bb7e5000 0A35F (v02 Intel  CALPELLA 06040000 INTL 20060912)
[    0.000000] ACPI: FACS bb79bfc0 00040
[    0.000000] ACPI: HPET bb7fec0a 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bb7fec42 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bb7fec7e 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bb7fed02 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SPCR bb7fed2a 00050 (v01 PTLTD  $UCRTBL$ 06040000 PTL  00000001)
[    0.000000] ACPI: SLIC bb7fed7a 00176 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bb7feef0 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: ASF! bb7fef60 000A0 (v16   CETP     CETP 06040000 PTL  00000001)
[    0.000000] ACPI: SSDT bb7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2112MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df170]              BRK ==> [00008dc000 - 00008df170]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 0001076801]      NEW RAMDISK ==> [00008e0000 - 0001076801]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7080] f7080
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bb800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bb27c
[    0.000000]     0: 0x000bb282 -> 0x000bb3e6
[    0.000000]     0: 0x000bb40f -> 0x000bb46f
[    0.000000]     0: 0x000bb70f -> 0x000bb717
[    0.000000]     0: 0x000bb71f -> 0x000bb77e
[    0.000000]     0: 0x000bb79f -> 0x000bb7e2
[    0.000000]     0: 0x000bb7ff -> 0x000bb800
[    0.000000] On node 0 totalpages: 767107
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1078000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3960 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4225 pages used for memmap
[    0.000000]   HighMem zone: 535660 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 761106
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic  root=UUID=9e5e1bbe-8a5c-467b-8575-f12bd13bf21a ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15360000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bb800)
[    0.000000] Memory: 3011384k/3072000k available (4679k kernel code, 55952k reserved, 2116k data, 660k init, 2159540k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 25 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 26 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 27 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 8 timers in total, 4 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2526.845 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.69 BogoMIPS (lpj=10107380)
[    0.000014] Security Framework initialized
[    0.000028] AppArmor: AppArmor initialized
[    0.000032] Mount-cache hash table entries: 512
[    0.000114] Initializing cgroup subsys ns
[    0.000117] Initializing cgroup subsys cpuacct
[    0.000120] Initializing cgroup subsys memory
[    0.000124] Initializing cgroup subsys devices
[    0.000125] Initializing cgroup subsys freezer
[    0.000126] Initializing cgroup subsys net_cls
[    0.000140] CPU: Physical Processor ID: 0
[    0.000141] CPU: Processor Core ID: 0
[    0.000144] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000146] CPU: L2 cache: 256K
[    0.000146] CPU: L3 cache: 3072K
[    0.000149] mce: CPU supports 9 MCE banks
[    0.000158] CPU0: Thermal monitoring handled by SMI
[    0.000161] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6
[    0.000167] using mwait in idle threads.
[    0.000171] Performance Events: Westmere events, Intel PMU driver.
[    0.000176] ... version:                3
[    0.000177] ... bit width:              48
[    0.000178] ... generic registers:      4
[    0.000180] ... value mask:             0000ffffffffffff
[    0.000181] ... max period:             000000007fffffff
[    0.000182] ... fixed-purpose events:   3
[    0.000183] ... event mask:             000000070000000f
[    0.000186] Checking 'hlt' instruction... OK.
[    0.018001] ACPI: Core revision 20090903
[    0.046774] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.046777] ftrace: allocating 21780 entries in 43 pages
[    0.052698] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.053096] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.092756] CPU0: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz stepping 05
[    0.199842] Booting processor 1 APIC 0x4 ip 0x6000
[    0.210060] Initializing CPU#1
[    0.287708] CPU: Physical Processor ID: 0
[    0.287709] CPU: Processor Core ID: 2
[    0.287712] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.287713] CPU: L2 cache: 256K
[    0.287713] CPU: L3 cache: 3072K
[    0.287723] CPU1: Thermal monitoring handled by SMI
[    0.287726] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6
[    0.287825] CPU1: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz stepping 05
[    0.287837] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.307923] Booting processor 2 APIC 0x1 ip 0x6000
[    0.318069] Initializing CPU#2
[    0.395652] CPU: Physical Processor ID: 0
[    0.395653] CPU: Processor Core ID: 0
[    0.395656] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.395658] CPU: L2 cache: 256K
[    0.395659] CPU: L3 cache: 3072K
[    0.395669] CPU2: Thermal monitoring handled by SMI
[    0.395673] CPU 2 MCA banks SHD:2 SHD:3 SHD:5 SHD:6
[    0.395711] CPU2: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz stepping 05
[    0.395727] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.415810] Booting processor 3 APIC 0x5 ip 0x6000
[    0.425956] Initializing CPU#3
[    0.503595] CPU: Physical Processor ID: 0
[    0.503596] CPU: Processor Core ID: 2
[    0.503599] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.503600] CPU: L2 cache: 256K
[    0.503600] CPU: L3 cache: 3072K
[    0.503611] CPU3: Thermal monitoring handled by SMI
[    0.503613] CPU 3 MCA banks SHD:2 SHD:3 SHD:5 SHD:6
[    0.503690] CPU3: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz stepping 05
[    0.503704] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.523712] Brought up 4 CPUs
[    0.523713] Total of 4 processors activated (20216.25 BogoMIPS).
[    0.525245] CPU0 attaching sched-domain:
[    0.525249]  domain 0: span 0,2 level SIBLING
[    0.525251]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    0.525255]   domain 1: span 0-3 level MC
[    0.525256]    groups: 0,2 (cpu_power = 1171 8 1,3 (cpu_power = 1171 8
[    0.525263] CPU1 attaching sched-domain:
[    0.525264]  domain 0: span 1,3 level SIBLING
[    0.525265]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    0.525268]   domain 1: span 0-3 level MC
[    0.525270]    groups: 1,3 (cpu_power = 1171 8 0,2 (cpu_power = 1171 8
[    0.525274] CPU2 attaching sched-domain:
[    0.525275]  domain 0: span 0,2 level SIBLING
[    0.525276]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    0.525280]   domain 1: span 0-3 level MC
[    0.525281]    groups: 0,2 (cpu_power = 1171 8 1,3 (cpu_power = 1171 8
[    0.525285] CPU3 attaching sched-domain:
[    0.525286]  domain 0: span 1,3 level SIBLING
[    0.525287]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    0.525290]   domain 1: span 0-3 level MC
[    0.525292]    groups: 1,3 (cpu_power = 1171 8 0,2 (cpu_power = 1171 8
[    0.525518] devtmpfs: initialized
[    0.525787] regulator: core version 0.5
[    0.525813] Time:  8:56:42  Date: 10/05/10
[    0.525843] NET: Registered protocol family 16
[    0.525919] Trying to unpack rootfs image as initramfs...
[    0.525928] EISA bus registered
[    0.525935] ACPI: bus type pci registered
[    0.525987] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.525990] PCI: MCFG area at e0000000 reserved in E820
[    0.525991] PCI: Using MMCONFIG for extended config space
[    0.525992] PCI: Using configuration type 1 for base access
[    0.526581] bio: create slab <bio-0> at 0
[    0.527474] ACPI: EC: Look up EC in DSDT
[    0.533312] ACPI: BIOS _OSI(Linux) query ignored
[    0.535346] ACPI: Interpreter enabled
[    0.535353] ACPI: (supports S0 S3 S4 S5)
[    0.535371] ACPI: Using IOAPIC for interrupt routing
[    0.541813] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.541868] ACPI: Power Resource [FN00] (off)
[    0.541906] ACPI: Power Resource [FN01] (off)
[    0.542178] ACPI: No dock devices found.
[    0.543027] _OSC invalid UUID
[    0.543029] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.543094] pci 0000:00:02.0: reg 10 64bit mmio: [0xf0000000-0xf03fffff]
[    0.543099] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.543102] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.543187] pci 0000:00:16.0: reg 10 64bit mmio: [0xf0806800-0xf080680f]
[    0.543243] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.543249] pci 0000:00:16.0: PME# disabled
[    0.543317] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf0807000-0xf08073ff]
[    0.543380] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.543384] pci 0000:00:1a.0: PME# disabled
[    0.543436] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0600000-0xf0603fff]
[    0.543491] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.543496] pci 0000:00:1b.0: PME# disabled
[    0.543587] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.543591] pci 0000:00:1c.0: PME# disabled
[    0.543679] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.543683] pci 0000:00:1c.1: PME# disabled
[    0.543773] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.543777] pci 0000:00:1c.5: PME# disabled
[    0.543841] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf0807400-0xf08077ff]
[    0.543905] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.543909] pci 0000:00:1d.0: PME# disabled
[    0.544125] pci 0000:00:1f.2: reg 10 io port: [0x1840-0x1847]
[    0.544132] pci 0000:00:1f.2: reg 14 io port: [0x1814-0x1817]
[    0.544139] pci 0000:00:1f.2: reg 18 io port: [0x1818-0x181f]
[    0.544146] pci 0000:00:1f.2: reg 1c io port: [0x1810-0x1813]
[    0.544153] pci 0000:00:1f.2: reg 20 io port: [0x1820-0x183f]
[    0.544160] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf0806000-0xf08067ff]
[    0.544203] pci 0000:00:1f.2: PME# supported from D3hot
[    0.544207] pci 0000:00:1f.2: PME# disabled
[    0.544244] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf0807800-0xf08078ff]
[    0.544261] pci 0000:00:1f.3: reg 20 io port: [0x1860-0x187f]
[    0.544326] pci 0000:00:1f.6: reg 10 64bit mmio: [0xf0605000-0xf0605fff]
[    0.544761] pci 0000:03:00.0: reg 10 64bit mmio: [0xf0500000-0xf0501fff]
[    0.545176] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.545197] pci 0000:03:00.0: PME# disabled
[    0.545363] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0500000-0xf05fffff]
[    0.545435] pci 0000:04:00.0: reg 10 64bit mmio: [0xf0400000-0xf043ffff]
[    0.545445] pci 0000:04:00.0: reg 18 io port: [0x2000-0x207f]
[    0.545523] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545529] pci 0000:04:00.0: PME# disabled
[    0.545598] pci 0000:00:1c.5: bridge io port: [0x2000-0x2fff]
[    0.545603] pci 0000:00:1c.5: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    0.545660] pci 0000:00:1e.0: transparent bridge
[    0.545693] pci_bus 0000:00: on NUMA node 0
[    0.545698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.545904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.546062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.546173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.546282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.546422] _OSC invalid UUID
[    0.550699] ACPI: PCI Root Bridge [CPBG] (0000:ff)
[    0.550811] pci_bus 0000:ff: on NUMA node 0
[    0.551011] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.551109] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.551206] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.551303] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.551399] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.551497] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.551600] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.551700] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.551791] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.551798] vgaarb: loaded
[    0.551883] SCSI subsystem initialized
[    0.551983] libata version 3.00 loaded.
[    0.552037] usbcore: registered new interface driver usbfs
[    0.552046] usbcore: registered new interface driver hub
[    0.552064] usbcore: registered new device driver usb
[    0.552164] ACPI: WMI: Mapper loaded
[    0.552166] PCI: Using ACPI for IRQ routing
[    0.552349] NetLabel: Initializing
[    0.552350] NetLabel:  domain hash size = 128
[    0.552351] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.552361] NetLabel:  unlabeled traffic allowed by default
[    0.552395] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 0, 0
[    0.552400] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.555586] hpet: hpet2 irq 24 for MSI
[    0.555741] hpet: hpet3 irq 25 for MSI
[    0.559676] hpet: hpet4 irq 26 for MSI
[    0.559826] hpet: hpet5 irq 27 for MSI
[    0.559843] Switching to clocksource tsc
[    0.561659] AppArmor: AppArmor Filesystem Enabled
[    0.561673] pnp: PnP ACPI init
[    0.561686] ACPI: bus type pnp registered
[    0.569500] pnp: PnP ACPI: found 11 devices
[    0.569502] ACPI: ACPI bus type pnp unregistered
[    0.569505] PnPBIOS: Disabled by ACPI PNP
[    0.569515] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.569517] system 00:05: ioport range 0x500-0x50f has been reserved
[    0.569519] system 00:05: ioport range 0x600-0x603 has been reserved
[    0.569520] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.569522] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.569524] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.569525] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.569527] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.569532] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.569534] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.569536] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.569537] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.569539] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.569541] system 00:09: iomem range 0xfeaff000-0xfeafffff has been reserved
[    0.569543] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.569545] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.569547] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.569548] system 00:09: iomem range 0xff000000-0xffffffff has been reserved
[    0.569550] system 00:09: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.604219] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.604224] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.604230] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.604234] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.604242] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.604244] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.604250] pci 0000:00:1c.1:   MEM window: 0xf0500000-0xf05fffff
[    0.604255] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
[    0.604262] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.604264] pci 0000:00:1c.5:   IO window: 0x2000-0x2fff
[    0.604270] pci 0000:00:1c.5:   MEM window: 0xf0400000-0xf04fffff
[    0.604275] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    0.604282] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.604283] pci 0000:00:1e.0:   IO window: disabled
[    0.604288] pci 0000:00:1e.0:   MEM window: disabled
[    0.604292] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.604313]   alloc irq_desc for 16 on node -1
[    0.604314]   alloc kstat_irqs on node -1
[    0.604320] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.604325] pci 0000:00:1c.0: setting latency timer to 64
[    0.604335]   alloc irq_desc for 17 on node -1
[    0.604336]   alloc kstat_irqs on node -1
[    0.604339] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.604343] pci 0000:00:1c.1: setting latency timer to 64
[    0.604353] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.604357] pci 0000:00:1c.5: setting latency timer to 64
[    0.604365] pci 0000:00:1e.0: setting latency timer to 64
[    0.604370] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.604371] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.604373] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.604375] pci_bus 0000:02: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.604376] pci_bus 0000:02: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.604378] pci_bus 0000:03: resource 0 io:  [0x4000-0x4fff]
[    0.604379] pci_bus 0000:03: resource 1 mem: [0xf0500000-0xf05fffff]
[    0.604381] pci_bus 0000:03: resource 2 pref mem [0xc0400000-0xc05fffff]
[    0.604383] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.604384] pci_bus 0000:04: resource 1 mem: [0xf0400000-0xf04fffff]
[    0.604386] pci_bus 0000:04: resource 2 pref mem [0xc0600000-0xc07fffff]
[    0.604387] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.604389] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.604390] pci_bus 0000:ff: resource 0 io:  [0x00-0xffff]
[    0.604392] pci_bus 0000:ff: resource 1 mem: [0x000000-0xffffffff]
[    0.604424] NET: Registered protocol family 2
[    0.604492] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.604684] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.604934] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.605052] TCP: Hash tables configured (established 131072 bind 65536)
[    0.605054] TCP reno registered
[    0.605102] NET: Registered protocol family 1
[    0.605114] pci 0000:00:02.0: Boot video device
[    0.605185] Simple Boot Flag at 0x36 set to 0x1
[    0.605379] cpufreq-nforce2: No nForce2 chipset.
[    0.605398] Scanning for low memory corruption every 60 seconds
[    0.605480] audit: initializing netlink socket (disabled)
[    0.605487] type=2000 audit(1286269001.439:1): initialized
[    0.612977] highmem bounce pool size: 64 pages
[    0.612981] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.613955] VFS: Disk quotas dquot_6.5.2
[    0.613992] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.614364] fuse init (API version 7.13)
[    0.614418] msgmni has been set to 1665
[    0.614599] alg: No test for stdrng (krng)
[    0.614639] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.614642] io scheduler noop registered
[    0.614643] io scheduler anticipatory registered
[    0.614644] io scheduler deadline registered
[    0.614669] io scheduler cfq registered (default)
[    0.614801]   alloc irq_desc for 28 on node -1
[    0.614803]   alloc kstat_irqs on node -1
[    0.614814] pcieport 0000:00:1c.0: irq 28 for MSI/MSI-X
[    0.614824] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.614950]   alloc irq_desc for 29 on node -1
[    0.614951]   alloc kstat_irqs on node -1
[    0.614958] pcieport 0000:00:1c.1: irq 29 for MSI/MSI-X
[    0.614968] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.615091]   alloc irq_desc for 30 on node -1
[    0.615092]   alloc kstat_irqs on node -1
[    0.615099] pcieport 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.615108] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.615182] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.615305] _OSC invalid UUID
[    0.615389] _OSC invalid UUID
[    0.615469] _OSC invalid UUID
[    0.615560] _OSC invalid UUID
[    0.615643] _OSC invalid UUID
[    0.615721] _OSC invalid UUID
[    0.615736] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.615814] ACPI: AC Adapter [ADP1] (on-line)
[    0.615861] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.615863] ACPI: Power Button [PWRB]
[    0.615888] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.615890] ACPI: Sleep Button [SLPB]
[    0.615916] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.616553] ACPI: Lid Switch [LID0]
[    0.616587] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.616589] ACPI: Power Button [PWRF]
[    0.616689] fan PNP0C0B:00: registered as cooling_device0
[    0.616692] ACPI: Fan [FAN0] (off)
[    0.616766] fan PNP0C0B:01: registered as cooling_device1
[    0.616770] ACPI: Fan [FAN1] (off)
[    0.617542] ACPI: SSDT bb71a918 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.618109] ACPI: SSDT bb718018 008B0 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.618549] Monitor-Mwait will be used to enter C-1 state
[    0.618572] Monitor-Mwait will be used to enter C-2 state
[    0.618591] Monitor-Mwait will be used to enter C-3 state
[    0.618625] processor LNXCPU:00: registered as cooling_device2
[    0.619078] ACPI: SSDT bb719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.619447] ACPI: SSDT bb717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.620072] processor LNXCPU:01: registered as cooling_device3
[    0.620886] processor LNXCPU:02: registered as cooling_device4
[    0.623756] processor LNXCPU:03: registered as cooling_device5
[    0.626365] thermal LNXTHERM:01: registered as thermal_zone0
[    0.626370] ACPI: Thermal Zone [TZ00] (27 C)
[    0.626953] thermal LNXTHERM:02: registered as thermal_zone1
[    0.626958] ACPI: Thermal Zone [TZ01] (0 C)
[    0.627041] isapnp: Scanning for PnP cards...
[    0.629662] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.630846] brd: module loaded
[    0.631283] loop: module loaded
[    0.631351] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.631735] Fixed MDIO Bus: probed
[    0.631765] PPP generic driver version 2.4.2
[    0.631791] tun: Universal TUN/TAP device driver, 1.6
[    0.631792] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.631853] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.631876] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.631887] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.631891] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.631924] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.631959] ehci_hcd 0000:00:1a.0: debug port 2
[    0.635931] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.635958] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0807000
[    0.651625] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.651734] usb usb1: configuration #1 chosen from 1 choice
[    0.651760] hub 1-0:1.0: USB hub found
[    0.651768] hub 1-0:1.0: 3 ports detected
[    0.651826]   alloc irq_desc for 23 on node -1
[    0.651828]   alloc kstat_irqs on node -1
[    0.651835] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.651852] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.651856] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.651886] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.651915] ehci_hcd 0000:00:1d.0: debug port 2
[    0.655881] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.655898] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0807400
[    0.671610] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.671700] usb usb2: configuration #1 chosen from 1 choice
[    0.671725] hub 2-0:1.0: USB hub found
[    0.671731] hub 2-0:1.0: 3 ports detected
[    0.671785] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.671800] uhci_hcd: USB Universal Host Controller Interface driver
[    0.671880] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    0.677476] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.677485] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.677554] mice: PS/2 mouse device common for all mice
[    0.677687] rtc_cmos 00:06: RTC can wake from S4
[    0.677726] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.677757] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.677845] device-mapper: uevent: version 1.0.3
[    0.677947] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.678026] device-mapper: multipath: version 1.1.0 loaded
[    0.678029] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.678124] EISA: Probing bus 0 at eisa.0
[    0.678132] Cannot allocate resource for EISA slot 1
[    0.678134] Cannot allocate resource for EISA slot 2
[    0.678136] Cannot allocate resource for EISA slot 3
[    0.678137] Cannot allocate resource for EISA slot 4
[    0.678154] EISA: Detected 0 cards.
[    0.678392] cpuidle: using governor ladder
[    0.678577] cpuidle: using governor menu
[    0.678960] TCP cubic registered
[    0.679095] NET: Registered protocol family 10
[    0.679474] lo: Disabled Privacy Extensions
[    0.679745] NET: Registered protocol family 17
[    0.680978] Using IPI No-Shortcut mode
[    0.681037] PM: Resume from disk failed.
[    0.681047] registered taskstats version 1
[    0.681512]   Magic number: 14:137:927
[    0.681606] rtc_cmos 00:06: setting system clock to 2010-10-05 08:56:42 UTC (1286269002)
[    0.681609] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.681611] EDD information not available.
[    0.682425] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.686698] Freeing initrd memory: 7770k freed
[    0.699473] ACPI: Battery Slot [BAT0] (battery present)
[    0.996525] isapnp: No Plug & Play device found
[    0.996539] Freeing unused kernel memory: 660k freed
[    0.996784] Write protecting the kernel text: 4680k
[    0.996813] Write protecting the kernel read-only data: 1840k
[    1.008712] udev: starting version 151
[    1.024221] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.038697] ahci 0000:00:1f.2: version 3.0
[    1.038718]   alloc irq_desc for 19 on node -1
[    1.038720]   alloc kstat_irqs on node -1
[    1.038728] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.038771]   alloc irq_desc for 31 on node -1
[    1.038772]   alloc kstat_irqs on node -1
[    1.038784] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    1.038830] ahci: SSS flag set, parallel bus scan disabled
[    1.038874] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.038878] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.038884] ahci 0000:00:1f.2: setting latency timer to 64
[    1.053720] scsi0 : ahci
[    1.054832] scsi1 : ahci
[    1.054933] scsi2 : ahci
[    1.055615] scsi3 : ahci
[    1.055720] scsi4 : ahci
[    1.055823] scsi5 : ahci
[    1.055875] ata1: SATA max UDMA/133 abar m2048@0xf0806000 port 0xf0806100 irq 31
[    1.055879] ata2: SATA max UDMA/133 abar m2048@0xf0806000 port 0xf0806180 irq 31
[    1.055881] ata3: DUMMY
[    1.055882] ata4: DUMMY
[    1.055885] ata5: SATA max UDMA/133 abar m2048@0xf0806000 port 0xf0806300 irq 31
[    1.055887] ata6: DUMMY
[    1.155896] usb 1-1: configuration #1 chosen from 1 choice
[    1.155973] hub 1-1:1.0: USB hub found
[    1.156066] hub 1-1:1.0: 6 ports detected
[    1.267676] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.375694] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.381944] ata1.00: ATA-8: SAMSUNG HM641JI, 2AJ10001, max UDMA/133
[    1.381949] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.388244] ata1.00: configured for UDMA/133
[    1.400343] usb 2-1: configuration #1 chosen from 1 choice
[    1.400546] hub 2-1:1.0: USB hub found
[    1.400703] hub 2-1:1.0: 8 ports detected
[    1.407884] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM641JI  2AJ1 PQ: 0 ANSI: 5
[    1.408006] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.408085] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.408142] sd 0:0:0:0: [sda] Write Protect is off
[    1.408144] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.408163] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.408254]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.449354] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.476761] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
[    1.608500] usb 1-1.4: configuration #1 chosen from 1 choice
[    1.679634] usb 2-1.1: new high speed USB device using ehci_hcd and address 3
[    2.111627] usb 2-1.1: configuration #1 chosen from 1 choice
[    2.116904] Initializing USB Mass Storage driver...
[    2.117044] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.117164] usbcore: registered new interface driver usb-storage
[    2.117166] USB Mass Storage support registered.
[    2.117171] usb-storage: device found at 3
[    2.117172] usb-storage: waiting for device to settle before scanning
[    2.135224] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.139571] ata2.00: ATAPI: PLDS DVDRW/BDROM DS-4E1S, ED15, max UDMA/100, ATAPI AN
[    2.141576] ata2.00: configured for UDMA/100
[    2.164964] scsi 1:0:0:0: CD-ROM            PLDS     DVDRWBD DS-4E1S  ED15 PQ: 0 ANSI: 5
[    2.168162] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    2.168166] Uniform CD-ROM driver Revision: 3.20
[    2.168279] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.168333] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.187236] usb 2-1.5: new high speed USB device using ehci_hcd and address 4
[    2.280163] usb 2-1.5: configuration #1 chosen from 1 choice
[    2.491999] ata5: SATA link down (SStatus 0 SControl 300)
[    3.018655] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.112387] usb-storage: device scan complete
[    7.113177] scsi 6:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[    7.113527] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.114403] sd 6:0:0:0: [sdb] 63176704 512-byte logical blocks: (32.3 GB/30.1 GiB)
[    7.115020] sd 6:0:0:0: [sdb] Write Protect is off
[    7.115024] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[    7.115028] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.117638] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.117643]  sdb: sdb1
[    7.245599] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.245605] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   11.534589] udev: starting version 151
[   11.543457] lp: driver loaded but no devices found
[   11.615364] Linux agpgart interface v0.103
[   11.638357] agpgart-intel 0000:00:00.0: Intel IGDNG/M Chipset
[   11.639109] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   11.654851] cfg80211: Calling CRDA to update world regulatory domain
[   11.668658] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.696580] [drm] Initialized drm 1.1.0 20060810
[   11.701238] cfg80211: World regulatory domain updated:
[   11.701241]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.701244]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.701247]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.701250]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.701253]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.701256]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.718041] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   11.774296] Linux video capture interface: v2.00
[   11.782264] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   11.789972] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   11.789975] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.790074] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.790105] iwlagn 0000:03:00.0: setting latency timer to 64
[   11.790169] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[   11.797402] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.797411] i915 0000:00:02.0: setting latency timer to 64
[   11.801193] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6480)
[   11.805953]   alloc irq_desc for 32 on node -1
[   11.805957]   alloc kstat_irqs on node -1
[   11.805975] i915 0000:00:02.0: irq 32 for MSI/MSI-X
[   11.805994] [drm] set up 31M of stolen space
[   11.813839] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   11.813907]   alloc irq_desc for 33 on node -1
[   11.813908]   alloc kstat_irqs on node -1
[   11.813927] iwlagn 0000:03:00.0: irq 33 for MSI/MSI-X
[   11.821857] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.827901] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7
[   11.827951] usbcore: registered new interface driver uvcvideo
[   11.827954] USB Video Class driver (v0.1.0)
[   11.905087] type=1505 audit(1286283413.727:2):  operation="profile_load" pid=685 name="/sbin/dhclient3"
[   11.905538] type=1505 audit(1286283413.727:3):   operation="profile_load" pid=685  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.905792] type=1505 audit(1286283413.727:4):   operation="profile_load" pid=685  name="/usr/lib/connman/scripts/dhclient-script"
[   12.409481] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   12.424882] fb0: inteldrmfb frame buffer device
[   12.424885] registered panic notifier
[   12.426373] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   12.426400] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.426421] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.426848]   alloc irq_desc for 22 on node -1
[   12.426851]   alloc kstat_irqs on node -1
[   12.426859] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.426898] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.428330] vga16fb: initializing
[   12.428333] vga16fb: mapped to 0xc00a0000
[   12.428336] vga16fb: not registering due to another framebuffer present
[   12.453139] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   12.547927] hda_codec: ALC269: BIOS auto-probing.
[   12.548404] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   12.737654] Console: switching to colour frame buffer device 200x56
[   12.913233] type=1505 audit(1286283414.735:5):  operation="profile_load" pid=882 name="/usr/share/gdm/guest-session/Xsession"
[   12.914218] type=1505 audit(1286283414.739:6):  operation="profile_replace" pid=883 name="/sbin/dhclient3"
[   12.914598] type=1505 audit(1286283414.739:7):   operation="profile_replace" pid=883  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.914804] type=1505 audit(1286283414.739:1 8:   operation="profile_replace" pid=883  name="/usr/lib/connman/scripts/dhclient-script"
[   12.916850] type=1505 audit(1286283414.739:9):  operation="profile_load" pid=884 name="/usr/bin/evince"
[   12.921649] type=1505 audit(1286283414.743:10):  operation="profile_load" pid=884 name="/usr/bin/evince-previewer"
[   12.924651] type=1505 audit(1286283414.747:11):  operation="profile_load" pid=884 name="/usr/bin/evince-thumbnailer"
[   13.315749] ppdev: user-space parallel port driver
[   13.505816] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   13.601424] iwlagn 0000:03:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   13.601430] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   13.602658] iwlagn 0000:03:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   13.602663] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   13.604158] iwlagn 0000:03:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   13.604162] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   13.605199] iwlagn 0000:03:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   13.605203] iwlagn 0000:03:00.0: Could not read microcode: -2
[   13.612554] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   13.613633] iwlagn 0000:03:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   13.613636] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   13.614782] iwlagn 0000:03:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   13.614785] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   13.615764] iwlagn 0000:03:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   13.615767] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   13.616849] iwlagn 0000:03:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   13.616852] iwlagn 0000:03:00.0: Could not read microcode: -2
[   13.800400] CPU0 attaching NULL sched-domain.
[   13.800404] CPU1 attaching NULL sched-domain.
[   13.800406] CPU2 attaching NULL sched-domain.
[   13.800407] CPU3 attaching NULL sched-domain.
[   13.828568] CPU0 attaching sched-domain:
[   13.828574]  domain 0: span 0,2 level SIBLING
[   13.828578]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   13.828590]   domain 1: span 0-3 level MC
[   13.828592]    groups: 0,2 (cpu_power = 1171 8 1,3 (cpu_power = 1171 8
[   13.828597] CPU1 attaching sched-domain:
[   13.828598]  domain 0: span 1,3 level SIBLING
[   13.828600]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   13.828603]   domain 1: span 0-3 level MC
[   13.828604]    groups: 1,3 (cpu_power = 1171 8 0,2 (cpu_power = 1171 8
[   13.828608] CPU2 attaching sched-domain:
[   13.828609]  domain 0: span 0,2 level SIBLING
[   13.828611]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   13.828614]   domain 1: span 0-3 level MC
[   13.828615]    groups: 0,2 (cpu_power = 1171 8 1,3 (cpu_power = 1171 8
[   13.828619] CPU3 attaching sched-domain:
[   13.828620]  domain 0: span 1,3 level SIBLING
[   13.828621]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   13.828625]   domain 1: span 0-3 level MC
[   13.828626]    groups: 1,3 (cpu_power = 1171 8 0,2 (cpu_power = 1171 8
[   15.787456] CPU0 attaching NULL sched-domain.
[   15.787461] CPU1 attaching NULL sched-domain.
[   15.787463] CPU2 attaching NULL sched-domain.
[   15.787464] CPU3 attaching NULL sched-domain.
[   15.886768] CPU0 attaching sched-domain:
[   15.886772]  domain 0: span 0,2 level SIBLING
[   15.886774]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   15.886777]   domain 1: span 0-3 level MC
[   15.886779]    groups: 0,2 (cpu_power = 1171 8 1,3 (cpu_power = 1171 8
[   15.886785] CPU1 attaching sched-domain:
[   15.886786]  domain 0: span 1,3 level SIBLING
[   15.886788]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   15.886791]   domain 1: span 0-3 level MC
[   15.886792]    groups: 1,3 (cpu_power = 1171 8 0,2 (cpu_power = 1171 8
[   15.886796] CPU2 attaching sched-domain:
[   15.886797]  domain 0: span 0,2 level SIBLING
[   15.886799]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   15.886802]   domain 1: span 0-3 level MC
[   15.886803]    groups: 0,2 (cpu_power = 1171 8 1,3 (cpu_power = 1171 8
[   15.886807] CPU3 attaching sched-domain:
[   15.886808]  domain 0: span 1,3 level SIBLING
[   15.886810]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   15.886813]   domain 1: span 0-3 level MC
[   15.886814]    groups: 1,3 (cpu_power = 1171 8 0,2 (cpu_power = 1171 8
[   68.047439] ISO 9660 Extensions: Microsoft Joliet Level 3
[   68.204020] ISO 9660 Extensions: RRIP_1991A
pb@pb-pc:~$ sudo lshw -C network
[sudo] password for pb: 
  *-network DISABLED      
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 57
       serial: 00:23:15:22:47:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:f0500000-f0501fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=121 8
pb@pb-pc:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
pb@pb-pc:~$ uname -mr
2.6.32-24-generic i686




Any ideas, ladies/gents?  Thanks in advance!

---

### Post by patricio2626 on 2010-10-05
Sorry, guys, this has been resolved.  I manually downloaded and installed the linux-backports-modules-wireless-lucid-generic packages.  Then, I was able to use my hardwired NIC, and I could then see that I had a software block on my wireless, which I lifted by:

rfkill unblock all
[B]
[/B]

---

