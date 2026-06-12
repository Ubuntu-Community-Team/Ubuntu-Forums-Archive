---
title: "My Cinema-U3000 Hybrid USB,I don't have a file /dev/video0, how to start the analog"
date: 2015-10-29
forum: Multimedia Software
---

### Post by ecomp2015 on 2015-10-29
Good day
I purchased the next tuner which should go to linux-ie analogue television, so yes

I bought the tuner
My Cinema-U3000 Hybrid

I managed to poke around a bit in the Internet


My question
I managed to start dvb-t in the program kaffeine
ubuntu mate 15.04 x86
ubuntu mate 15.04 x64
Debian mate

but not umi&#281; to start My Cinema-U3000 Hybrid USB in the tvtime program

1.
The same I don't have a file / dev/video 0

I don't know how to create / dv/video 0 for my device My Cinema-U3000 Hybrid USB

I am calling for help

parameters below

root@ecomp:/home/ecomp# tvtime -d /dev/video0
```

root@ecomp:/home/ecomp# tvtime -d /dev/video0
Uruchomione tvtime 1.0.2.
Czytanie konfiguracji z /etc/tvtime/tvtime.xml
Czytanie konfiguracji z /root/.tvtime/tvtime.xml
/root/.tvtime/stationlist.xml: No existing PAL station list "custom".
videoinput: Cannot open capture device /dev/video0: Nie ma takiego pliku ani katalogu
Dziekujemy za u&#380;ywanie tvtime.
root@ecomp:/home/ecomp# 


```

root@ecomp:/home/ecomp#  ls -l /dev/video* 

```

root@ecomp:/home/ecomp#  ls -l /dev/video* 
ls: nie ma dost&#281;pu do /dev/video*: Nie ma takiego pliku ani katalogu
root@ecomp:/home/ecomp# 


```


root@ecomp:/home/ecomp# lspci
```


root@ecomp:/home/ecomp# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
root@ecomp:/home/ecomp# 


```

root@ecomp:/home/ecomp# lspci -n
```


root@ecomp:/home/ecomp# lspci -n
00:00.0 0600: 8086:0104 (rev 09)
00:01.0 0604: 8086:0101 (rev 09)
00:02.0 0300: 8086:0116 (rev 09)
00:16.0 0780: 8086:1c3a (rev 04)
00:1a.0 0c03: 8086:1c2d (rev 05)
00:1b.0 0403: 8086:1c20 (rev 05)
00:1c.0 0604: 8086:1c10 (rev b5)
00:1c.1 0604: 8086:1c12 (rev b5)
00:1c.5 0604: 8086:1c1a (rev b5)
00:1d.0 0c03: 8086:1c26 (rev 05)
00:1f.0 0601: 8086:1c49 (rev 05)
00:1f.2 0101: 8086:1c01 (rev 05)
00:1f.3 0c05: 8086:1c22 (rev 05)
00:1f.5 0101: 8086:1c09 (rev 05)
01:00.0 0300: 10de:0df4 (rev a1)
03:00.0 0280: 168c:002b (rev 01)
04:00.0 0200: 1969:1083 (rev c0)
root@ecomp:/home/ecomp# 



```

root@ecomp:/home/ecomp# ls /dev | grep video
```

root@ecomp:/home/ecomp# ls /dev | grep video
root@ecomp:/home/ecomp# 


```

root@ecomp:/home/ecomp# xawtv -hwscan
```

root@ecomp:/home/ecomp# xawtv -hwscan
This is xawtv-3.103, running on Linux/x86_64 (3.19.0-31-generic)
looking for available devices
port 73-104
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

port 105-105
    type : Xvideo, image scaler
    name : Intel(R) Video Sprite

root@ecomp:/home/ecomp# 


```

root@ecomp:/home/ecomp# xawtv -c /dev/video0
```

root@ecomp:/home/ecomp# xawtv -c /dev/video0
This is xawtv-3.103, running on Linux/x86_64 (3.19.0-31-generic)
xinerama 0: 1600x900+0+0
v4l2: open /dev/video0: Nie ma takiego pliku ani katalogu
vid-open: failed: libv4l
no video grabber device available
root@ecomp:/home/ecomp# 


```


root@ecomp:/home/ecomp# mplayer tv://
```

root@ecomp:/home/ecomp# mplayer tv://
MPlayer2 2.0-728-g2c378c7-4 (C) 2000-2012 MPlayer Team
Cannot open file '/root/.mplayer/input.conf': No such file or directory
Failed to open /root/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.

Playing tv://.
Detected file format: TV
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: unable to open '/dev/video0': No such file or directory
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.
Opening as detected format "TV" failed.
Failed to recognize file format.


Exiting... (End of file)
root@ecomp:/home/ecomp# 


```

root@ecomp:/home/ecomp# amixer scontents
```

root@ecomp:/home/ecomp# amixer scontents
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 57 [66%] [-22.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [-0.20dB]
  Front Right: Playback 254 [100%] [-0.20dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',16
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 19 [61%] [12.00dB] [on]
  Front Right: Capture 19 [61%] [12.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
root@ecomp:/home/ecomp# 


```

root@ecomp:/home/ecomp# dmesg
```


root@ecomp:/home/ecomp# dmesg
[    0.000000] CPU0 microcode updated early to revision 0x29, date = 2013-06-12
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-31-generic (buildd@lcy01-07) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 (Ubuntu 3.19.0-31.36-generic 3.19.8-ckt7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=7e0c7dfc-c670-410b-ab54-fa8c4c6768bf ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x00000000aacf5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aacf6000-0x00000000aacf8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aacf9000-0x00000000aacfafff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aacfb000-0x00000000aad8dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aad8e000-0x00000000aad8efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aad8f000-0x00000000aadb7fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aadb8000-0x00000000aadb9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aadba000-0x00000000aade7fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aade8000-0x00000000aaf18fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aaf19000-0x00000000aafe7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000aafe8000-0x00000000aaffcfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aaffd000-0x00000000aaffffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ab000000-0x00000000af9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff980000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000014fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: ASUSTeK Computer Inc. N73SV/N73SV, BIOS N73SV.306 08/18/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x14fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF8000000 write-back
[    0.000000]   3 base 0A8000000 mask FFC000000 write-back
[    0.000000]   4 base 0AB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 base 140000000 mask FF0000000 write-back
[    0.000000]   7 base 14FE00000 mask FFFE00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2688MB, range: 64MB, type WB
[    0.000000] reg 4, base: 2736MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 1GB, type WB
[    0.000000] reg 6, base: 5GB, range: 256MB, type WB
[    0.000000] reg 7, base: 5374MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4014M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2688MB, range: 32MB, type WB
[    0.000000] reg 4, base: 2720MB, range: 16MB, type WB
[    0.000000] reg 5, base: 4GB, range: 1GB, type WB
[    0.000000] reg 6, base: 5GB, range: 256MB, type WB
[    0.000000] reg 7, base: 5374MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xab000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xaaffd max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcc50-0x000fcc5f] mapped at [ffff8800000fcc50]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x14fc00000-0x14fdfffff]
[    0.000000]  [mem 0x14fc00000-0x14fdfffff] page 2M
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x140000000-0x14fbfffff]
[    0.000000]  [mem 0x140000000-0x14fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x120000000-0x13fffffff]
[    0.000000]  [mem 0x120000000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x3fffffff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x40200000-0xaacf5fff]
[    0.000000]  [mem 0x40200000-0xaabfffff] page 2M
[    0.000000]  [mem 0xaac00000-0xaacf5fff] page 4k
[    0.000000] BRK [0x01fea000, 0x01feafff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xaacf9000-0xaacfafff]
[    0.000000]  [mem 0xaacf9000-0xaacfafff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaad8e000-0xaad8efff]
[    0.000000]  [mem 0xaad8e000-0xaad8efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaadb8000-0xaadb9fff]
[    0.000000]  [mem 0xaadb8000-0xaadb9fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaade8000-0xaaf18fff]
[    0.000000]  [mem 0xaade8000-0xaaf18fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaafe8000-0xaaffcfff]
[    0.000000]  [mem 0xaafe8000-0xaaffcfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
[    0.000000]  [mem 0x100000000-0x11fffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35838000-0x36c13fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0430 000024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 0x00000000AAFFEE18 000064 (v01 _ASUS_ NoteBook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 0x00000000AAF9BD98 0000F4 (v04 _ASUS_ NoteBook 06222004 MSFT 00010013)
[    0.000000] ACPI: DSDT 0x00000000AAF7C018 00D922 (v01 _ASUS_ NoteBook 00000000 INTL 20091112)
[    0.000000] ACPI: FACS 0x00000000AAFE5E40 000040
[    0.000000] ACPI: FACS 0x00000000AAFE5D40 000040
[    0.000000] ACPI: APIC 0x00000000AAFFDF18 0000CC (v02 _ASUS_ NoteBook 06222004 MSFT 00010013)
[    0.000000] ACPI: HPET 0x00000000AAFE6D18 000038 (v01 _ASUS_ NoteBook 06222004 AMI. 00000003)
[    0.000000] ACPI: ECDT 0x00000000AAFE5B18 0000C1 (v01 _ASUS_ NoteBook 06222004 AMI  00000000)
[    0.000000] ACPI: MCFG 0x00000000AAFE6C98 00003C (v01 _ASUS_ NoteBook 06222004 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x00000000AAF7B018 000925 (v01 PmRef  Cpu0Ist  00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000AAF7A018 000996 (v01 PmRef  CpuPm    00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000AAF5EA98 00031E (v01 IdeRef IdeTable 00001000 INTL 20091112)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000014fdfffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x14fdf8000-0x14fdfcfff]
[    0.000000]  [ffffea0000000000-ffffea00053fffff] PMD -> [ffff88014b400000-ffff88014f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x14fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0xaacf5fff]
[    0.000000]   node   0: [mem 0xaacf9000-0xaacfafff]
[    0.000000]   node   0: [mem 0xaad8e000-0xaad8efff]
[    0.000000]   node   0: [mem 0xaadb8000-0xaadb9fff]
[    0.000000]   node   0: [mem 0xaade8000-0xaaf18fff]
[    0.000000]   node   0: [mem 0xaafe8000-0xaaffcfff]
[    0.000000]   node   0: [mem 0x100000000-0x14fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x14fdfffff]
[    0.000000] On node 0 totalpages: 1026015
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 158 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10858 pages used for memmap
[    0.000000]   DMA32 zone: 694849 pages, LIFO batch:31
[    0.000000]   Normal zone: 5112 pages used for memmap
[    0.000000]   Normal zone: 327168 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xaba00000-0xaf9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40000000-0x401fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xaacf6000-0xaacf8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaacfb000-0xaad8dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xaad8f000-0xaadb7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaadba000-0xaade7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaaf19000-0xaafe7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaaffd000-0xaaffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xab000000-0xaf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xe3ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe4000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff97ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff980000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffd7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffd80000-0xffffffff]
[    0.000000] e820: [mem 0xafa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88014fa00000 s87104 r8192 d31680 u131072
[    0.000000] pcpu-alloc: s87104 r8192 d31680 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1009823
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=7e0c7dfc-c670-410b-ab54-fa8c4c6768bf ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3932932K/4104060K available (8004K kernel code, 1234K rwdata, 3764K rodata, 1408K init, 1300K bss, 171128K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=16.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=16
[    0.000000] NR_IRQS:16640 nr_irqs:552 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-15.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1995.425 MHz processor
[    0.000042] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.85 BogoMIPS (lpj=7981700)
[    0.000045] pid_max: default: 32768 minimum: 301
[    0.000052] ACPI: Core revision 20141107
[    0.012350] ACPI: All ACPI Tables successfully acquired
[    0.012389] Security Framework initialized
[    0.012411] AppArmor: AppArmor initialized
[    0.012412] Yama: becoming mindful.
[    0.012755] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013724] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.014341] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.014348] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.014565] Initializing cgroup subsys memory
[    0.014571] Initializing cgroup subsys devices
[    0.014574] Initializing cgroup subsys freezer
[    0.014576] Initializing cgroup subsys net_cls
[    0.014578] Initializing cgroup subsys blkio
[    0.014580] Initializing cgroup subsys perf_event
[    0.014583] Initializing cgroup subsys net_prio
[    0.014585] Initializing cgroup subsys hugetlb
[    0.014611] CPU: Physical Processor ID: 0
[    0.014612] CPU: Processor Core ID: 0
[    0.014617] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.014620] mce: CPU supports 9 MCE banks
[    0.014635] CPU0: Thermal monitoring enabled (TM1)
[    0.014642] process: using mwait in idle threads
[    0.014646] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.014772] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
[    0.021792] ftrace: allocating 30117 entries in 118 pages
[    0.039387] Switched APIC routing to physical flat.
[    0.039807] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079479] smpboot: CPU0: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz (fam: 06, model: 2a, stepping: 07)
[    0.079487] TSC deadline timer enabled
[    0.079518] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.079542] ... version:                3
[    0.079543] ... bit width:              48
[    0.079544] ... generic registers:      4
[    0.079545] ... value mask:             0000ffffffffffff
[    0.079546] ... max period:             0000ffffffffffff
[    0.079548] ... fixed-purpose events:   3
[    0.079549] ... event mask:             000000070000000f
[    0.080589] x86: Booting SMP configuration:
[    0.080591] .... node  #0, CPUs:        #1
[    0.091919] CPU1 microcode updated early to revision 0x29, date = 2013-06-12
[    0.094173] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.094287]   #2
[    0.105614] CPU2 microcode updated early to revision 0x29, date = 2013-06-12
[    0.107837]   #3
[    0.131319] CPU3 microcode updated early to revision 0x29, date = 2013-06-12
[    0.133538]   #4  #5  #6  #7
[    0.221069] x86: Booted up 1 node, 8 CPUs
[    0.221073] smpboot: Total of 8 processors activated (31926.80 BogoMIPS)
[    0.229554] devtmpfs: initialized
[    0.232300] evm: security.selinux
[    0.232302] evm: security.SMACK64
[    0.232303] evm: security.SMACK64EXEC
[    0.232304] evm: security.SMACK64TRANSMUTE
[    0.232305] evm: security.SMACK64MMAP
[    0.232306] evm: security.ima
[    0.232307] evm: security.capability
[    0.232370] PM: Registering ACPI NVS region [mem 0xaaf19000-0xaafe7fff] (847872 bytes)
[    0.232574] pinctrl core: initialized pinctrl subsystem
[    0.232695] RTC time:  7:56:30, date: 10/29/15
[    0.232819] NET: Registered protocol family 16
[    0.233300] cpuidle: using governor ladder
[    0.237298] cpuidle: using governor menu
[    0.237435] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.237437] ACPI: bus type PCI registered
[    0.237439] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.237535] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.237538] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.237639] PCI: Using configuration type 1 for base access
[    0.241857] ACPI: Added _OSI(Module Device)
[    0.241859] ACPI: Added _OSI(Processor Device)
[    0.241861] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.241862] ACPI: Added _OSI(Processor Aggregator Device)
[    0.243765] ACPI : EC: EC description table is found, configuring boot EC
[    0.245760] ACPI: Executed 1 blocks of module-level executable AML code
[    0.248852] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.302119] ACPI: Dynamic OEM Table Load:
[    0.302128] ACPI: SSDT 0xFFFF88014A0CB000 000694 (v01 PmRef  Cpu0Cst  00003001 INTL 20091112)
[    0.302820] ACPI: Dynamic OEM Table Load:
[    0.302826] ACPI: SSDT 0xFFFF88014A10BC00 000303 (v01 PmRef  ApIst    00003000 INTL 20091112)
[    0.303437] ACPI: Dynamic OEM Table Load:
[    0.303442] ACPI: SSDT 0xFFFF88014A0D3400 000119 (v01 PmRef  ApCst    00003000 INTL 20091112)
[    0.305123] ACPI: Interpreter enabled
[    0.305135] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.305151] ACPI: (supports S0 S1 S3 S4 S5)
[    0.305153] ACPI: Using IOAPIC for interrupt routing
[    0.305180] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.424303] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.424311] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.424316] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.424957] PCI host bridge to bus 0000:00
[    0.424960] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.424963] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.424965] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.424967] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.424969] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.424971] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.424973] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.424975] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.424976] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.424978] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.424980] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
[    0.424982] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.424991] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.425099] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.425139] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.425187] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.425237] pci 0000:00:02.0: [8086:0116] type 00 class 0x030000
[    0.425250] pci 0000:00:02.0: reg 0x10: [mem 0xdd400000-0xdd7fffff 64bit]
[    0.425257] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.425262] pci 0000:00:02.0: reg 0x20: [io  0xe000-0xe03f]
[    0.425395] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.425420] pci 0000:00:16.0: reg 0x10: [mem 0xdf609000-0xdf60900f 64bit]
[    0.425505] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.425610] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.425633] pci 0000:00:1a.0: reg 0x10: [mem 0xdf607000-0xdf6073ff]
[    0.425732] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.425799] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.425850] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.425869] pci 0000:00:1b.0: reg 0x10: [mem 0xdf600000-0xdf603fff 64bit]
[    0.425952] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.426046] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.426137] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.426232] pci 0000:00:1c.1: [8086:1c12] type 01 class 0x060400
[    0.426322] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.426421] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.426511] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.426613] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.426636] pci 0000:00:1d.0: reg 0x10: [mem 0xdf606000-0xdf6063ff]
[    0.426735] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.426799] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.426848] pci 0000:00:1f.0: [8086:1c49] type 00 class 0x060100
[    0.427042] pci 0000:00:1f.2: [8086:1c01] type 00 class 0x01018f
[    0.427059] pci 0000:00:1f.2: reg 0x10: [io  0xe110-0xe117]
[    0.427068] pci 0000:00:1f.2: reg 0x14: [io  0xe100-0xe103]
[    0.427077] pci 0000:00:1f.2: reg 0x18: [io  0xe0f0-0xe0f7]
[    0.427085] pci 0000:00:1f.2: reg 0x1c: [io  0xe0e0-0xe0e3]
[    0.427094] pci 0000:00:1f.2: reg 0x20: [io  0xe0d0-0xe0df]
[    0.427103] pci 0000:00:1f.2: reg 0x24: [io  0xe0c0-0xe0cf]
[    0.427217] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.427235] pci 0000:00:1f.3: reg 0x10: [mem 0xdf605000-0xdf6050ff 64bit]
[    0.427257] pci 0000:00:1f.3: reg 0x20: [io  0xe040-0xe05f]
[    0.427359] pci 0000:00:1f.5: [8086:1c09] type 00 class 0x010185
[    0.427376] pci 0000:00:1f.5: reg 0x10: [io  0xe0b0-0xe0b7]
[    0.427384] pci 0000:00:1f.5: reg 0x14: [io  0xe0a0-0xe0a3]
[    0.427393] pci 0000:00:1f.5: reg 0x18: [io  0xe090-0xe097]
[    0.427402] pci 0000:00:1f.5: reg 0x1c: [io  0xe080-0xe083]
[    0.427411] pci 0000:00:1f.5: reg 0x20: [io  0xe070-0xe07f]
[    0.427419] pci 0000:00:1f.5: reg 0x24: [io  0xe060-0xe06f]
[    0.427592] pci 0000:01:00.0: [10de:0df4] type 00 class 0x030000
[    0.427601] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.427609] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.427618] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.427623] pci 0000:01:00.0: reg 0x24: [io  0xd000-0xd07f]
[    0.427629] pci 0000:01:00.0: reg 0x30: [mem 0xdd000000-0xdd07ffff pref]
[    0.427686] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.433398] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.433406] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.433413] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.433422] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.433550] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.433555] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.433559] pci 0000:00:1c.0:   bridge window [mem 0xdec00000-0xdf5fffff]
[    0.433566] pci 0000:00:1c.0:   bridge window [mem 0xd3700000-0xd40fffff 64bit pref]
[    0.433661] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.433694] pci 0000:03:00.0: reg 0x10: [mem 0xde200000-0xde20ffff 64bit]
[    0.433857] pci 0000:03:00.0: supports D1
[    0.433859] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.433895] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.441406] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.441415] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.441424] pci 0000:00:1c.1:   bridge window [mem 0xde200000-0xdebfffff]
[    0.441437] pci 0000:00:1c.1:   bridge window [mem 0xd2c00000-0xd35fffff 64bit pref]
[    0.441585] pci 0000:04:00.0: [1969:1083] type 00 class 0x020000
[    0.441619] pci 0000:04:00.0: reg 0x10: [mem 0xdd800000-0xdd83ffff 64bit]
[    0.441635] pci 0000:04:00.0: reg 0x18: [io  0xa000-0xa07f]
[    0.441782] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.441820] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.449413] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    0.449423] pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
[    0.449432] pci 0000:00:1c.5:   bridge window [mem 0xdd800000-0xde1fffff]
[    0.449445] pci 0000:00:1c.5:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.505617] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.505678] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 10 11 12 14 15)
[    0.505733] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 10 11 12 14 15)
[    0.505787] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.505841] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.505896] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.505951] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 10 11 12 14 15)
[    0.506005] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 10 11 12 14 15)
[    0.506135] ACPI: Enabled 1 GPEs in block 00 to 3F
[    0.506193] ACPI : EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.506298] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.506300] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.506305] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.506307] vgaarb: loaded
[    0.506308] vgaarb: bridge control possible 0000:01:00.0
[    0.506309] vgaarb: no bridge control possible 0000:00:02.0
[    0.506564] SCSI subsystem initialized
[    0.506608] libata version 3.00 loaded.
[    0.506637] ACPI: bus type USB registered
[    0.506658] usbcore: registered new interface driver usbfs
[    0.506669] usbcore: registered new interface driver hub
[    0.506694] usbcore: registered new device driver usb
[    0.506848] PCI: Using ACPI for IRQ routing
[    0.508470] PCI: pci_cache_line_size set to 64 bytes
[    0.508527] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.508529] e820: reserve RAM buffer [mem 0xaacf6000-0xabffffff]
[    0.508531] e820: reserve RAM buffer [mem 0xaacfb000-0xabffffff]
[    0.508534] e820: reserve RAM buffer [mem 0xaad8f000-0xabffffff]
[    0.508536] e820: reserve RAM buffer [mem 0xaadba000-0xabffffff]
[    0.508537] e820: reserve RAM buffer [mem 0xaaf19000-0xabffffff]
[    0.508539] e820: reserve RAM buffer [mem 0xaaffd000-0xabffffff]
[    0.508541] e820: reserve RAM buffer [mem 0x14fe00000-0x14fffffff]
[    0.508670] NetLabel: Initializing
[    0.508672] NetLabel:  domain hash size = 128
[    0.508673] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.508689] NetLabel:  unlabeled traffic allowed by default
[    0.508766] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.508772] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.510818] Switched to clocksource hpet
[    0.517179] AppArmor: AppArmor Filesystem Enabled
[    0.517258] pnp: PnP ACPI init
[    0.517399] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.517402] system 00:00: [io  0x1000-0x100f] has been reserved
[    0.517405] system 00:00: [io  0xffff] has been reserved
[    0.517407] system 00:00: [io  0xffff] has been reserved
[    0.517409] system 00:00: [io  0x0400-0x0453] could not be reserved
[    0.517411] system 00:00: [io  0x0458-0x047f] has been reserved
[    0.517414] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.517416] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.517420] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.517459] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.517508] system 00:02: [io  0x0454-0x0457] has been reserved
[    0.517511] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.517580] pnp 00:03: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.517626] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.571089] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.571092] system 00:05: [mem 0xfed10000-0xfed17fff] could not be reserved
[    0.571094] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.571097] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.571099] system 00:05: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.571101] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.571104] system 00:05: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.571106] system 00:05: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.571108] system 00:05: [mem 0xff000000-0xffffffff] could not be reserved
[    0.571110] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.571113] system 00:05: [mem 0xafa00000-0xafa00fff] has been reserved
[    0.571116] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.571176] system 00:06: [mem 0xafa00000-0xafa00fff] has been reserved
[    0.571179] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.571317] system 00:07: [mem 0x20000000-0x201fffff] has been reserved
[    0.571319] system 00:07: [mem 0x40000000-0x401fffff] has been reserved
[    0.571322] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.571337] pnp: PnP ACPI: found 8 devices
[    0.577956] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.577960] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.577963] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.577967] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.577970] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.577974] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.577980] pci 0000:00:1c.0:   bridge window [mem 0xdec00000-0xdf5fffff]
[    0.577984] pci 0000:00:1c.0:   bridge window [mem 0xd3700000-0xd40fffff 64bit pref]
[    0.577991] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.577995] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.578000] pci 0000:00:1c.1:   bridge window [mem 0xde200000-0xdebfffff]
[    0.578005] pci 0000:00:1c.1:   bridge window [mem 0xd2c00000-0xd35fffff 64bit pref]
[    0.578012] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    0.578016] pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
[    0.578021] pci 0000:00:1c.5:   bridge window [mem 0xdd800000-0xde1fffff]
[    0.578026] pci 0000:00:1c.5:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.578034] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.578036] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.578039] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.578040] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.578043] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.578044] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.578046] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.578048] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.578050] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.578052] pci_bus 0000:00: resource 13 [mem 0xafa00000-0xfeafffff]
[    0.578054] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    0.578056] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.578058] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdd0fffff]
[    0.578060] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.578063] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.578065] pci_bus 0000:02: resource 1 [mem 0xdec00000-0xdf5fffff]
[    0.578067] pci_bus 0000:02: resource 2 [mem 0xd3700000-0xd40fffff 64bit pref]
[    0.578069] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.578071] pci_bus 0000:03: resource 1 [mem 0xde200000-0xdebfffff]
[    0.578073] pci_bus 0000:03: resource 2 [mem 0xd2c00000-0xd35fffff 64bit pref]
[    0.578075] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    0.578077] pci_bus 0000:04: resource 1 [mem 0xdd800000-0xde1fffff]
[    0.578079] pci_bus 0000:04: resource 2 [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.578111] NET: Registered protocol family 2
[    0.578318] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.578413] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.578485] TCP: Hash tables configured (established 32768 bind 32768)
[    0.578505] TCP: reno registered
[    0.578513] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.578533] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.578603] NET: Registered protocol family 1
[    0.578622] pci 0000:00:02.0: Video device with shadowed ROM
[    0.830921] PCI: CLS 64 bytes, default 64
[    0.830976] Trying to unpack rootfs image as initramfs...
[    1.217934] Freeing initrd memory: 20336K (ffff880035838000 - ffff880036c14000)
[    1.217946] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.217948] software IO TLB [mem 0xa6cf6000-0xaacf6000] (64MB) mapped at [ffff8800a6cf6000-ffff8800aacf5fff]
[    1.218319] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    1.218387] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x29
[    1.218395] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x29
[    1.218403] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x29
[    1.218412] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x29
[    1.218421] microcode: CPU4 sig=0x206a7, pf=0x10, revision=0x29
[    1.218431] microcode: CPU5 sig=0x206a7, pf=0x10, revision=0x29
[    1.218439] microcode: CPU6 sig=0x206a7, pf=0x10, revision=0x29
[    1.218446] microcode: CPU7 sig=0x206a7, pf=0x10, revision=0x29
[    1.218508] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.218540] Scanning for low memory corruption every 60 seconds
[    1.219069] futex hash table entries: 4096 (order: 6, 262144 bytes)
[    1.219107] Initialise system trusted keyring
[    1.219130] audit: initializing netlink subsys (disabled)
[    1.219145] audit: type=2000 audit(1446105390.188:1): initialized
[    1.219504] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.221236] zpool: loaded
[    1.221239] zbud: loaded
[    1.221430] VFS: Disk quotas dquot_6.5.2
[    1.221477] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.222000] fuse init (API version 7.23)
[    1.222161] Key type big_key registered
[    1.222551] Key type asymmetric registered
[    1.222554] Asymmetric key parser 'x509' registered
[    1.222605] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.222663] io scheduler noop registered
[    1.222667] io scheduler deadline registered (default)
[    1.222704] io scheduler cfq registered
[    1.223345] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.223365] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.223397] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.223399] vesafb: scrolling: redraw
[    1.223401] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.229602] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90004800000, using 3072k, total 3072k
[    1.229729] Console: switching to colour frame buffer device 128x48
[    1.229747] fb0: VESA VGA frame buffer device
[    1.229774] intel_idle: MWAIT substates: 0x21120
[    1.229776] intel_idle: v0.4 model 0x2A
[    1.229777] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.230221] ACPI: AC Adapter [AC0] (on-line)
[    1.230349] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.231395] ACPI: Lid Switch [LID]
[    1.231450] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.231454] ACPI: Sleep Button [SLPB]
[    1.231497] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.231500] ACPI: Power Button [PWRF]
[    1.232540] thermal LNXTHERM:00: registered as thermal_zone0
[    1.232542] ACPI: Thermal Zone [TZ00] (62 C)
[    1.232591] GHES: HEST is not enabled!
[    1.232607] ACPI: Battery Slot [BAT0] (battery absent)
[    1.232737] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.234545] Linux agpgart interface v0.103
[    1.236102] brd: module loaded
[    1.236836] loop: module loaded
[    1.237002] ata_piix 0000:00:1f.2: version 2.13
[    1.237109] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.390567] ata_piix 0000:00:1f.2: SCR access via SIDPR is available but doesn't work
[    1.391083] scsi host0: ata_piix
[    1.391320] scsi host1: ata_piix
[    1.391382] ata1: SATA max UDMA/133 cmd 0xe110 ctl 0xe100 bmdma 0xe0d0 irq 19
[    1.391385] ata2: SATA max UDMA/133 cmd 0xe0f0 ctl 0xe0e0 bmdma 0xe0d8 irq 19
[    1.391492] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.546524] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    1.546851] scsi host2: ata_piix
[    1.547045] scsi host3: ata_piix
[    1.547105] ata3: SATA max UDMA/133 cmd 0xe0b0 ctl 0xe0a0 bmdma 0xe070 irq 19
[    1.547107] ata4: SATA max UDMA/133 cmd 0xe090 ctl 0xe080 bmdma 0xe078 irq 19
[    1.547232] libphy: Fixed MDIO Bus: probed
[    1.547236] tun: Universal TUN/TAP device driver, 1.6
[    1.547237] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.547311] PPP generic driver version 2.4.2
[    1.547397] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.547404] ehci-pci: EHCI PCI platform driver
[    1.547527] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.547534] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.547548] ehci-pci 0000:00:1a.0: debug port 2
[    1.551437] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.551452] ehci-pci 0000:00:1a.0: irq 16, io mem 0xdf607000
[    1.558501] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.558543] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.558545] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.558547] usb usb1: Product: EHCI Host Controller
[    1.558549] usb usb1: Manufacturer: Linux 3.19.0-31-generic ehci_hcd
[    1.558551] usb usb1: SerialNumber: 0000:00:1a.0
[    1.558679] hub 1-0:1.0: USB hub found
[    1.558687] hub 1-0:1.0: 2 ports detected
[    1.558891] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.558897] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.558911] ehci-pci 0000:00:1d.0: debug port 2
[    1.562817] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.562832] ehci-pci 0000:00:1d.0: irq 23, io mem 0xdf606000
[    1.574490] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.574530] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.574533] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.574534] usb usb2: Product: EHCI Host Controller
[    1.574537] usb usb2: Manufacturer: Linux 3.19.0-31-generic ehci_hcd
[    1.574538] usb usb2: SerialNumber: 0000:00:1d.0
[    1.574664] hub 2-0:1.0: USB hub found
[    1.574670] hub 2-0:1.0: 2 ports detected
[    1.574765] ata1.01: ATAPI: HL-DT-ST DVDRAM GT51N, AS00, max UDMA/133
[    1.574772] ehci-platform: EHCI generic platform driver
[    1.574784] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.574789] ohci-pci: OHCI PCI platform driver
[    1.574805] ohci-platform: OHCI generic platform driver
[    1.574815] uhci_hcd: USB Universal Host Controller Interface driver
[    1.574877] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.576399] i8042: Detected active multiplexing controller, rev 1.1
[    1.577210] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.577214] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.577244] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.577268] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.577292] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.577489] mousedev: PS/2 mouse device common for all mice
[    1.577824] rtc_cmos 00:01: RTC can wake from S4
[    1.577994] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.578023] rtc_cmos 00:01: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.578034] i2c /dev entries driver
[    1.578107] device-mapper: uevent: version 1.0.3
[    1.578191] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.578215] Intel P-state driver initializing.
[    1.578487] Consider also installing thermald for improved thermal control.
[    1.578497] ledtrig-cpu: registered to indicate activity on CPUs
[    1.578666] PCCT header not found.
[    1.578668] ACPI PCC probe failed.
[    1.578764] TCP: cubic registered
[    1.578865] NET: Registered protocol family 10
[    1.579043] NET: Registered protocol family 17
[    1.579055] Key type dns_resolver registered
[    1.579486] Loading compiled-in X.509 certificates
[    1.580382] Loaded X.509 cert 'Magrathea: Glacier signing key: b4ba13d5cec93e1af4b34d36da1bd4fcffa54410'
[    1.580395] registered taskstats version 1
[    1.582381] Key type trusted registered
[    1.589970] Key type encrypted registered
[    1.589977] AppArmor: AppArmor sha1 policy hashing enabled
[    1.589980] ima: No TPM chip found, activating TPM-bypass!
[    1.590003] evm: HMAC attrs: 0x1
[    1.590443]   Magic number: 3:835:926
[    1.590601] rtc_cmos 00:01: setting system clock to 2015-10-29 07:56:31 UTC (1446105391)
[    1.590722] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.590724] EDD information not available.
[    1.590824] PM: Hibernation image not present or could not be loaded.
[    1.590828] ata1.01: configured for UDMA/133
[    1.595345] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GT51N     AS00 PQ: 0 ANSI: 5
[    1.615053] sr 0:0:1:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.615060] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.615226] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.615246] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.615321] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.725466] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
[    1.725469] Write protecting the kernel read-only data: 12288k
[    1.725812] Freeing unused kernel memory: 176K (ffff8800017d4000 - ffff880001800000)
[    1.725995] Freeing unused kernel memory: 332K (ffff880001bad000 - ffff880001c00000)
[    1.735561] random: systemd-udevd urandom read with 2 bits of entropy available
[    1.787776] atl1c 0000:04:00.0: version 1.0.1.1-NAPI
[    1.870496] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.886453] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.002934] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.002944] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.003261] hub 1-1:1.0: USB hub found
[    2.003347] hub 1-1:1.0: 6 ports detected
[    2.018924] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.018935] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.019303] hub 2-1:1.0: USB hub found
[    2.019368] hub 2-1:1.0: 6 ports detected
[    2.214397] tsc: Refined TSC clocksource calibration: 1995.467 MHz
[    2.274382] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.290361] usb 2-1.1: new low-speed USB device number 3 using ehci-pci
[    2.367626] usb 1-1.1: New USB device found, idVendor=0cf3, idProduct=3005
[    2.367636] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.386520] usb 2-1.1: New USB device found, idVendor=0101, idProduct=0007
[    2.386531] usb 2-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.386537] usb 2-1.1: Product: USB OPTICAL MOUSE 
[    2.390254] hidraw: raw HID events driver (C) Jiri Kosina
[    2.394195] usbcore: registered new interface driver usbhid
[    2.394197] usbhid: USB HID core driver
[    2.395633] input: USB OPTICAL MOUSE  as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:0101:0007.0001/input/input12
[    2.395733] hid-generic 0003:0101:0007.0001: input,hidraw0: USB HID v1.11 Mouse [USB OPTICAL MOUSE ] on usb-0000:00:1d.0-1.1/input0
[    2.438216] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
[    2.458203] usb 2-1.2: new low-speed USB device number 4 using ehci-pci
[    2.561040] usb 2-1.2: New USB device found, idVendor=1a2c, idProduct=0023
[    2.561042] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.561043] usb 2-1.2: Product: USB Keykoard
[    2.561045] usb 2-1.2: Manufacturer: USB
[    2.563706] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:1A2C:0023.0002/input/input13
[    2.568788] usb 1-1.2: New USB device found, idVendor=13d3, idProduct=5122
[    2.568790] usb 1-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.568791] usb 1-1.2: Product: USB2.0 UVC 2M WebCam
[    2.568793] usb 1-1.2: Manufacturer: USB2.0 UVC 2M WebCam
[    2.568794] usb 1-1.2: SerialNumber: USB2.0 UVC 2M WebCam
[    2.592431] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201)
[    2.618289] hid-generic 0003:1A2C:0023.0002: input,hidraw1: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:1d.0-1.2/input0
[    2.620415] psmouse serio4: elantech: Synaptics capabilities query result 0x78, 0x14, 0x0b.
[    2.620698] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:1A2C:0023.0003/input/input14
[    2.674287] hid-generic 0003:1A2C:0023.0003: input,hidraw2: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1d.0-1.2/input1
[    2.727027] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
[    2.746220] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[    3.214395] Switched to clocksource tsc
[    4.371420] usb 2-1.3: New USB device found, idVendor=14cd, idProduct=6116
[    4.371431] usb 2-1.3: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[    4.371437] usb 2-1.3: Product: USB Mass Storage Device
[    4.371442] usb 2-1.3: Manufacturer: Generic     
[    4.371446] usb 2-1.3: SerialNumber: 116AC2101219
[    4.374656] usb-storage 2-1.3:1.0: USB Mass Storage device detected
[    4.374912] scsi host4: usb-storage 2-1.3:1.0
[    4.374987] usbcore: registered new interface driver usb-storage
[    4.376293] usbcore: registered new interface driver uas
[    4.441573] usb 2-1.4: new high-speed USB device number 6 using ehci-pci
[    4.535272] usb 2-1.4: New USB device found, idVendor=0b05, idProduct=1736
[    4.535274] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.535275] usb 2-1.4: Product: U3000 Hybrid
[    4.535277] usb 2-1.4: Manufacturer: ASUSTeK
[    4.535278] usb 2-1.4: SerialNumber: 7404100033
[    5.374006] scsi 4:0:0:0: Direct-Access        Mass  Storage Device        PQ: 0 ANSI: 0
[    5.374302] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    5.374927] sd 4:0:0:0: [sda] 1465149166 512-byte logical blocks: (750 GB/698 GiB)
[    5.375536] sd 4:0:0:0: [sda] Write Protect is off
[    5.375539] sd 4:0:0:0: [sda] Mode Sense: 03 00 00 00
[    5.376156] sd 4:0:0:0: [sda] No Caching mode page found
[    5.376160] sd 4:0:0:0: [sda] Assuming drive cache: write through
[    5.478751]  sda: sda1 sda3 < sda5 sda6 sda7 sda8 >
[    5.481894] sd 4:0:0:0: [sda] Attached SCSI disk
[    6.326245] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.826722] random: nonblocking pool is initialized
[    7.457690] systemd[1]: Inserted module 'autofs4'
[    7.575263] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    7.575434] systemd[1]: Detected architecture x86-64.
[    7.591474] systemd[1]: Set hostname to <ecomp>.
[    8.975046] systemd[1]: Reached target Remote File Systems (Pre).
[    8.975057] systemd[1]: Starting Remote File Systems (Pre).
[    8.975085] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    8.975091] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[    8.975118] systemd[1]: Created slice Root Slice.
[    8.975126] systemd[1]: Starting Root Slice.
[    8.975148] systemd[1]: Listening on Delayed Shutdown Socket.
[    8.975154] systemd[1]: Starting Delayed Shutdown Socket.
[    8.975228] systemd[1]: Created slice User and Session Slice.
[    8.975235] systemd[1]: Starting User and Session Slice.
[    8.975301] systemd[1]: Listening on Journal Audit Socket.
[    8.975308] systemd[1]: Starting Journal Audit Socket.
[    8.975330] systemd[1]: Listening on fsck to fsckd communication Socket.
[    8.975337] systemd[1]: Starting fsck to fsckd communication Socket.
[    8.975369] systemd[1]: Listening on Journal Socket.
[    8.975381] systemd[1]: Starting Journal Socket.
[    8.975445] systemd[1]: Created slice System Slice.
[    8.975458] systemd[1]: Starting System Slice.
[    8.975863] systemd[1]: Starting Increase datagram queue length...
[    8.976342] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    8.976774] systemd[1]: Started Braille Device Support.
[    8.976958] systemd[1]: Starting Braille Device Support...
[    8.976984] systemd[1]: Reached target Slices.
[    8.976995] systemd[1]: Starting Slices.
[    8.977437] systemd[1]: Mounting Huge Pages File System...
[    8.977884] systemd[1]: Mounting Debug File System...
[    8.978317] systemd[1]: Starting Nameserver information manager...
[    9.162550] systemd[1]: Starting Load Kernel Modules...
[    9.162966] systemd[1]: Starting Uncomplicated firewall...
[    9.163034] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    9.163049] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[    9.163475] systemd[1]: Started Read required files in advance.
[    9.163531] systemd[1]: Starting Read required files in advance...
[    9.163946] systemd[1]: Starting LSB: controls configuration of serial ports...
[    9.164409] systemd[1]: Starting Setup Virtual Console...
[    9.164430] systemd[1]: Reached target Encrypted Volumes.
[    9.164444] systemd[1]: Starting Encrypted Volumes.
[    9.164619] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    9.164630] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[    9.390161] systemd[1]: Started Set Up Additional Binary Formats.
[    9.390673] systemd[1]: Mounting POSIX Message Queue File System...
[    9.390734] systemd[1]: Listening on udev Control Socket.
[    9.390751] systemd[1]: Starting udev Control Socket.
[    9.390786] systemd[1]: Listening on udev Kernel Socket.
[    9.390794] systemd[1]: Starting udev Kernel Socket.
[    9.391227] systemd[1]: Starting udev Coldplug all Devices...
[    9.391286] systemd[1]: Listening on Journal Socket (/dev/log).
[    9.391300] systemd[1]: Starting Journal Socket (/dev/log).
[    9.392142] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    9.392314] systemd[1]: Started Uncomplicated firewall.
[    9.392463] systemd[1]: Started Setup Virtual Console.
[    9.392925] systemd[1]: Starting Create Static Device Nodes in /dev...
[    9.531524] systemd[1]: Mounted Huge Pages File System.
[    9.531578] systemd[1]: Mounted Debug File System.
[    9.531607] systemd[1]: Mounted POSIX Message Queue File System.
[    9.531821] systemd[1]: Started Increase datagram queue length.
[    9.539787] systemd[1]: Listening on Syslog Socket.
[    9.539797] systemd[1]: Starting Syslog Socket.
[    9.540225] systemd[1]: Starting Journal Service...
[    9.613366] systemd[1]: Started Nameserver information manager.
[    9.851139] systemd[1]: Started udev Coldplug all Devices.
[    9.851643] systemd[1]: Starting udev Wait for Complete Device Initialization...
[    9.974539] lp: driver loaded but no devices found
[   10.035368] ppdev: user-space parallel port driver
[   10.294598] systemd[1]: Started Load Kernel Modules.
[   10.295091] systemd[1]: Mounting FUSE Control File System...
[   10.295514] systemd[1]: Starting Apply Kernel Variables...
[   10.295575] systemd[1]: Mounted Configuration File System.
[   10.297084] systemd[1]: Mounted FUSE Control File System.
[   10.475012] systemd[1]: Started Journal Service.
[   13.380166] wmi: Mapper loaded
[   13.777518] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20141107/utaddress-258)
[   13.777525] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.777528] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000549 (\SBGP) (20141107/utaddress-258)
[   13.777531] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[   13.777534] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.777535] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000549 (\SBGP) (20141107/utaddress-258)
[   13.777537] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[   13.777539] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.777540] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000549 (\SBGP) (20141107/utaddress-258)
[   13.777543] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[   13.777545] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.777546] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   13.829515] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.205951] asus_wmi: ASUS WMI generic driver loaded
[   14.324274] asus_wmi: Initialization: 0x1
[   14.324402] asus_wmi: SFUN value: 0x1a0af7
[   14.324846] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input15
[   14.328831] asus_wmi: Backlight controlled by ACPI video driver
[   14.437874] drm: module verification failed: signature and/or  required key missing - tainting kernel
[   14.439847] [drm] Initialized drm 1.1.0 20060810
[   14.684127] AVX version of gcm_enc/dec engaged.
[   14.684130] AES CTR mode by8 optimization enabled
[   14.694245] ttm: disagrees about version of symbol drm_vma_offset_manager_init
[   14.694248] ttm: Unknown symbol drm_vma_offset_manager_init (err -22)
[   14.694254] ttm: disagrees about version of symbol drm_mm_remove_node
[   14.694255] ttm: Unknown symbol drm_mm_remove_node (err -22)
[   14.694274] ttm: disagrees about version of symbol drm_mm_takedown
[   14.694275] ttm: Unknown symbol drm_mm_takedown (err -22)
[   14.694293] ttm: disagrees about version of symbol drm_vma_offset_add
[   14.694294] ttm: Unknown symbol drm_vma_offset_add (err -22)
[   14.694362] ttm: disagrees about version of symbol drm_mm_clean
[   14.694364] ttm: Unknown symbol drm_mm_clean (err -22)
[   14.694373] ttm: disagrees about version of symbol drm_vma_offset_manager_destroy
[   14.694374] ttm: Unknown symbol drm_vma_offset_manager_destroy (err -22)
[   14.694378] ttm: disagrees about version of symbol drm_mm_init
[   14.694379] ttm: Unknown symbol drm_mm_init (err -22)
[   14.694388] ttm: disagrees about version of symbol drm_vma_offset_lookup_locked
[   14.694389] ttm: Unknown symbol drm_vma_offset_lookup_locked (err -22)
[   14.694397] ttm: disagrees about version of symbol drm_mm_insert_node_in_range_generic
[   14.694398] ttm: Unknown symbol drm_mm_insert_node_in_range_generic (err -22)
[   14.694401] ttm: disagrees about version of symbol drm_mm_debug_table
[   14.694402] ttm: Unknown symbol drm_mm_debug_table (err -22)
[   14.694421] ttm: disagrees about version of symbol drm_vma_offset_remove
[   14.694423] ttm: Unknown symbol drm_vma_offset_remove (err -22)
[   14.889944] cfg80211: Calling CRDA to update world regulatory domain
[   15.148638] [drm] Memory usable by graphics device = 2048M
[   15.148642] checking generic (b0000000 300000) vs hw (b0000000 10000000)
[   15.148643] fb: switching to inteldrmfb from VESA VGA
[   15.148672] Console: switching to colour dummy device 80x25
[   15.148724] [drm] Replacing VGA console driver
[   15.170311] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   15.170319] [drm] Driver supports precise vblank timestamp query.
[   15.170430] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.194498] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   15.195651] acpi device:4e: registered as cooling_device8
[   15.195718] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:4a/LNXVIDEO:00/input/input16
[   15.196333] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.197461] acpi device:50: registered as cooling_device9
[   15.197528] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input17
[   15.197602] [drm] Initialized i915 1.6.0 20150130 for 0000:00:02.0 on minor 0
[   15.204542] media: Linux media interface: v0.10
[   15.211636] fbcon: inteldrmfb (fb0) is primary device
[   15.211696] Console: switching to colour frame buffer device 200x56
[   15.211718] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   15.211720] i915 0000:00:02.0: registered panic notifier
[   15.346645] Linux video capture interface: v2.00
[   15.346648] WARNING: You are using an experimental version of the media stack.
    As the driver is backported to an older kernel, it doesn't offer
    enough quality for its usage in production.
    Use it with care.
Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
    79f5b6ae960d380c829fb67d5dadcd1d025d2775 [media] c8sectpfe: Remove select on CONFIG_FW_LOADER_USER_HELPER_FALLBACK
    eab2b7612d2bce0b06873e24899a8455a04bb915 [media] DocBook media: update copyright/version numbers
    520e82d44b6d74d35d296ba6ceb990552ce9fb82 [media] ivtv: Convert to get_user_pages_unlocked()
[   15.585306] Bluetooth: Core ver 2.20
[   15.585319] NET: Registered protocol family 31
[   15.585320] Bluetooth: HCI device and connection manager initialized
[   15.585324] Bluetooth: HCI socket layer initialized
[   15.585326] Bluetooth: L2CAP socket layer initialized
[   15.585330] Bluetooth: SCO socket layer initialized
[   15.637262] sound hdaudioC0D0: autoconfig: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:speaker
[   15.637265] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.637267] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   15.637269] sound hdaudioC0D0:    mono: mono_out=0x0
[   15.637270] sound hdaudioC0D0:    dig-out=0x1e/0x0
[   15.637271] sound hdaudioC0D0:    inputs:
[   15.637273] sound hdaudioC0D0:      Internal Mic=0x19
[   15.637275] sound hdaudioC0D0:      Mic=0x18
[   15.650579] videobuf2_memops: Unknown symbol put_vaddr_frames (err 0)
[   15.650592] videobuf2_memops: Unknown symbol get_vaddr_frames (err 0)
[   15.650601] videobuf2_memops: Unknown symbol frame_vector_destroy (err 0)
[   15.650609] videobuf2_memops: Unknown symbol frame_vector_create (err 0)
[   15.808488] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   15.808626] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[   15.809264] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[   15.836266] usbcore: registered new interface driver btusb
[   16.100757] ath: phy0: Set BT/WLAN RX diversity capability
[   16.150044] ath: EEPROM regdomain: 0x60
[   16.150047] ath: EEPROM indicates we should expect a direct regpair map
[   16.150049] ath: Country alpha2 being used: 00
[   16.150050] ath: Regpair used: 0x60
[   16.255964] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.256239] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90004860000, irq=17
[   16.323935] intel_rapl: Found RAPL domain package
[   16.323940] intel_rapl: Found RAPL domain core
[   16.323942] intel_rapl: Found RAPL domain uncore
[   17.251245] WARNING: You are using an experimental version of the media stack.
    As the driver is backported to an older kernel, it doesn't offer
    enough quality for its usage in production.
    Use it with care.
Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
    79f5b6ae960d380c829fb67d5dadcd1d025d2775 [media] c8sectpfe: Remove select on CONFIG_FW_LOADER_USER_HELPER_FALLBACK
    eab2b7612d2bce0b06873e24899a8455a04bb915 [media] DocBook media: update copyright/version numbers
    520e82d44b6d74d35d296ba6ceb990552ce9fb82 [media] ivtv: Convert to get_user_pages_unlocked()
[   17.323782] WARNING: You are using an experimental version of the media stack.
    As the driver is backported to an older kernel, it doesn't offer
    enough quality for its usage in production.
    Use it with care.
Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
    79f5b6ae960d380c829fb67d5dadcd1d025d2775 [media] c8sectpfe: Remove select on CONFIG_FW_LOADER_USER_HELPER_FALLBACK
    eab2b7612d2bce0b06873e24899a8455a04bb915 [media] DocBook media: update copyright/version numbers
    520e82d44b6d74d35d296ba6ceb990552ce9fb82 [media] ivtv: Convert to get_user_pages_unlocked()
[   17.381367] cfg80211: World regulatory domain updated:
[   17.381370] cfg80211:  DFS Master region: unset
[   17.381372] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   17.381374] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   17.381376] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   17.381377] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   17.381379] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   17.381381] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   17.381383] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   17.381384] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   17.381386] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   17.618901] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in warm state.
[   17.619003] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   17.619168] DVB: registering new adapter (Asus My Cinema-U3000Hybrid)
[   18.014688] usb 2-1.4: DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   18.094524] xc2028 8-0061: creating new instance
[   18.094535] xc2028 8-0061: type set to XCeive xc2028/xc3028 tuner
[   18.205200] Registered IR keymap rc-dib0700-rc5
[   18.205304] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/rc/rc0/input21
[   18.205379] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/rc/rc0
[   18.205580] dvb-usb: schedule remote query interval to 50 msecs.
[   18.205582] dvb-usb: Asus My Cinema-U3000Hybrid successfully initialized and connected.
[   18.205738] usbcore: registered new interface driver dvb_usb_dib0700
[   18.348062] xc2028 8-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   18.961850] Adding 5528572k swap on /dev/sda8.  Priority:-1 extents:1 across:5528572k FS
[   20.431677] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.808529] systemd-journald[279]: Received request to flush runtime journal from PID 1
[   22.885465] audit: type=1400 audit(1446105412.796:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=689 comm="apparmor_parser"
[   22.885472] audit: type=1400 audit(1446105412.796:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=689 comm="apparmor_parser"
[   22.973847] audit: type=1400 audit(1446105412.888:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=689 comm="apparmor_parser"
[   22.973855] audit: type=1400 audit(1446105412.888:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=689 comm="apparmor_parser"
[   22.973867] audit: type=1400 audit(1446105412.888:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=689 comm="apparmor_parser"
[   22.973871] audit: type=1400 audit(1446105412.888:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=689 comm="apparmor_parser"
[   23.309167] audit: type=1400 audit(1446105413.220:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=689 comm="apparmor_parser"
[   23.309175] audit: type=1400 audit(1446105413.220:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=689 comm="apparmor_parser"
[   23.309180] audit: type=1400 audit(1446105413.220:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=689 comm="apparmor_parser"
[   23.309184] audit: type=1400 audit(1446105413.220:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=689 comm="apparmor_parser"
[   25.566273] cgroup: new mount options do not match the existing superblock, will be ignored
[   30.964570] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.964573] Bluetooth: BNEP filters: protocol multicast
[   30.964576] Bluetooth: BNEP socket layer initialized
[   31.409330] Bluetooth: RFCOMM TTY layer initialized
[   31.409338] Bluetooth: RFCOMM socket layer initialized
[   31.409345] Bluetooth: RFCOMM ver 1.11
[   32.226872] atl1c 0000:04:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   48.188535] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.194684] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   48.251849] Ebtables v2.0 registered
[   48.492214] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   48.596560] device virbr0-nic entered promiscuous mode
[   48.706758] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   48.733544] virbr0: port 1(virbr0-nic) entered listening state
[   48.733558] virbr0: port 1(virbr0-nic) entered listening state
[   48.826355] virbr0: port 1(virbr0-nic) entered disabled state
[   63.667321] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
root@ecomp:/home/ecomp# 



```

root@ecomp:/home/ecomp# lsmod
```


root@ecomp:/home/ecomp# lsmod
Module                  Size  Used by
rc_dib0700_rc5         16384  0 
tuner_xc2028           32768  1 
dib7000p               36864  1 
dvb_usb_dib0700       151552  0 
dib9000                40960  1 dvb_usb_dib0700
dib7000m               24576  1 dvb_usb_dib0700
dib0090                40960  1 dvb_usb_dib0700
dib0070                20480  1 dvb_usb_dib0700
dib3000mc              20480  1 dvb_usb_dib0700
dibx000_common         20480  5 dib9000,dvb_usb_dib0700,dib3000mc,dib7000m,dib7000p
dvb_usb                32768  1 dvb_usb_dib0700
dvb_core              126976  3 dib9000,dvb_usb,dib7000p
rc_core                28672  4 dvb_usb,dvb_usb_dib0700,rc_dib0700_rc5
xt_CHECKSUM            16384  1 
iptable_mangle         16384  1 
ipt_MASQUERADE         16384  3 
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1 
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2 
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1 
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2 
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6 
bridge                110592  0 
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0 
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0 
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1 
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
rfcomm                 69632  8 
bnep                   20480  2 
binfmt_misc            20480  1 
arc4                   16384  2 
ath9k                 147456  0 
intel_rapl             20480  0 
btusb                  40960  0 
snd_hda_codec_hdmi     53248  1 
ath9k_common           32768  1 ath9k
videobuf2_v4l2         28672  0 
iosf_mbi               16384  1 intel_rapl
ath9k_hw              458752  2 ath9k_common,ath9k
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_codec_realtek    86016  1 
videobuf2_core         40960  1 videobuf2_v4l2
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
x86_pkg_temp_thermal    16384  0 
v4l2_common            16384  1 videobuf2_v4l2
snd_hda_intel          36864  4 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
intel_powerclamp       20480  0 
videodev              155648  2 v4l2_common,videobuf2_v4l2
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
mac80211              724992  1 ath9k
media                  24576  1 videodev
snd_hwdep              20480  1 snd_hda_codec
i915                 1081344  2 
coretemp               16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm_intel             151552  0 
snd_seq_midi           16384  0 
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
kvm                   483328  1 kvm_intel
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper        126976  1 i915
crct10dif_pclmul       16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
drm                   344064  4 i915,drm_kms_helper
asus_nb_wmi            24576  0 
crc32_pclmul           16384  0 
asus_wmi               24576  1 asus_nb_wmi
ghash_clmulni_intel    16384  0 
snd                    90112  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 asus_wmi
aesni_intel           172032  0 
mei_me                 20480  0 
i2c_algo_bit           16384  1 i915
mxm_wmi                16384  0 
mei                    90112  1 mei_me
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
lpc_ich                24576  0 
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
joydev                 20480  0 
ablk_helper            16384  1 aesni_intel
serio_raw              16384  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
video                  20480  2 i915,asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
uas                    24576  0 
usb_storage            69632  6 uas
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
psmouse               118784  0 
atl1c                  49152  0 
pata_acpi              16384  0 
root@ecomp:/home/ecomp# 



```

root@ecomp:/home/ecomp# lsusb
```

root@ecomp:/home/ecomp# lsusb
Bus 002 Device 004: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 002 Device 003: ID 1a2c:0023 China Resource Semico Co., Ltd 
Bus 002 Device 006: ID 0101:0007  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:5122 IMC Networks 
Bus 001 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ecomp:/home/ecomp# 


```


tvtime starting is writing not moge to find devices /dev/video0
he cannot reconstruct the device /dev/video 0

I am doing I am searching everywhere, and if only to start the analogue signal from the cable TV


how to start analogue television in tvtime in the device My Cinema-U3000 Hybrid USB

and how to create / dev/video 0 for the device My Cinema-U3000 Hybrid USB
he is thanking for help

---

### Post by ecomp2015 on 2015-10-30
I welcome
I did the further step, so I did this way

```

$ hg clone http://linuxtv.org/hg/v4l-dvb
$ cd v4l-dvb
$ make

```

here for me a mistake is jumping out
```

root@ecomp:/home/ecomp/v4l-dvb# make
make -C /home/ecomp/v4l-dvb/v4l 
make[1]: Wej&#347;cie do katalogu '/home/ecomp/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 3.9.0
File not found: /lib/modules/3.9.0-31-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** Brak regu&#322; do zrobienia obiektu '.config', wymaganego przez '.myconfig'. Stop.
make[1]: Opuszczenie katalogu '/home/ecomp/v4l-dvb/v4l'
Makefile:27: polecenia dla obiektu 'all' nie powiod&#322;y si&#281;
make: *** [all] B&#322;&#261;d 2
root@ecomp:/home/ecomp/v4l-dvb# 

```

I don't know what to do is searching the Internet, but without the result with detecting the mistake
and he wishes transitions to the further step

```

# make install
# modprobe -v dvb-usb-dib0700

```

2.
how to check, whether my the card is serving tvtime

3.
how to check has which my of carat television Asus we cinema u3000 hybrid under usb the chipset and other parameters, because I don't know what drivers to search for

please for the help to solving a problem he thanks

---

### Post by blm-ubunet on 2015-10-31
Can you unplug & then re-plug the tuner stick & so get a cold start firmware loading sequence?
Then post the tail end of dmesg (from the unplug event to the end) ..

It is likely that the analogue tuner is **not** functional in Linux.
[http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T](http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T)
AFAICT This device does not have a mpeg2 encoder so it would become a frame grabber & require mpeg encoding to run on CPU (to record).
Large parts of the world have switched off (or are switching off) analogue OTA.

---

### Post by ecomp2015 on 2015-11-08
I sold the tuner u3000 Asus and I bought other tuner terratec cinergy hybrid t usb xs

I am closing the subject thanks

---

