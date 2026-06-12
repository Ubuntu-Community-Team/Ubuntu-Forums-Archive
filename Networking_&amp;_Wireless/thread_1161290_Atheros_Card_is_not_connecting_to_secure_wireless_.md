---
title: "Atheros Card is not connecting to secure wireless networks."
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by OmnipotentEntity on 2009-05-16
Running Kubuntu 9.04 64-bit, it's an upgrade of 8.10, which was an upgrade of 8.04, which was an upgrade of ... well you get the idea.

I have two wireless networks in my home, one secured WPA2 AES encryption, the other is open.  (mordor and mordor-open respectively)

The wireless card, since upgrading to 9.04, will not connect to my secured wireless network.

I've tried both the ath_pci driver and the ath5k driver, the only difference is the ath5k driver reports better signal strength and has extremely high latency.

Some info about my setup.


sudo lshw -C network

```
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wifi0
       version: 01
       serial: 00:14:6c:bf:f2:1c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.7 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:17:e8:d7:60:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lspci

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
```

lsusb

```
Bus 001 Device 002: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lspci -nn | grep "Wireless"

```
01:07.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
```

ifconfig

```
ath0      Link encap:Ethernet  HWaddr 00:14:6c:bf:f2:1c
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:febf:f21c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3865065 (3.8 MB)  TX bytes:262729 (262.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:e6:5a:5e:f9
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:72310 (72.3 KB)  TX bytes:72310 (72.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-BF-F2-1C-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10754 errors:0 dropped:0 overruns:0 frame:449
          TX packets:1972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:4961640 (4.9 MB)  TX bytes:310266 (310.2 KB)
          Interrupt:19
```

iwconfig 

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"mordor-open"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:2F:0F:0C:6C
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=18/70  Signal level=-69 dBm  Noise level=-87 dBm
          Rx invalid nwid:3881  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod

```
Module                  Size  Used by                                                                                                                                              
wlan_scan_sta          21888  1                                                                                                                                                    
ath_rate_sample        21120  1                                                                                                                                                    
ath_pci               108400  0                                                                                                                                                    
wlan                  232736  4 wlan_scan_sta,ath_rate_sample,ath_pci                                                                                                              
ath_hal               225904  3 ath_rate_sample,ath_pci                                                                                                                            
arc4                   10240  0                                                                                                                                                    
ecb                    11392  0                                                                                                                                                    
lbm_cw_mac80211       258872  0                                                                                                                                                    
lbm_cw_cfg80211        84920  1 lbm_cw_mac80211                                                                                                                                    
led_class              13064  0                                                                                                                                                    
binfmt_misc            18572  1                                                                                                                                                    
bridge                 63904  0                                                                                                                                                    
stp                    11140  1 bridge                                                                                                                                             
bnep                   22912  2                                                                                                                                                    
vboxnetflt            110316  0                                                                                                                                                    
vboxdrv              1704748  1 vboxnetflt                                                                                                                                         
autofs4                38408  1                                                                                                                                                    
video                  29204  0                                                                                                                                                    
output                 11648  1 video
input_polldev          12688  0
reiserfs              253952  1
sbp2                   34700  0
lp                     19588  0
snd_intel8x0           44456  2
snd_ac97_codec        133848  1 snd_intel8x0
ac97_bus               10368  1 snd_ac97_codec
snd_usb_audio         108832  1
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_dummy          11524  0
snd_pcm                99592  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_seq_oss            41984  0
snd_usb_lib            27392  1 snd_usb_audio
snd_seq_midi           15744  0
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            33920  2 snd_usb_lib,snd_seq_midi
uvcvideo               69512  0
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep              16776  1 snd_usb_audio
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
usbhid                 47040  0
k8temp                 13440  0
snd                    78792  19 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device,snd_hwdep
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_intel8x0,snd_pcm
ppdev                  16904  0
i2c_nforce2            16136  0
nvidia               8123768  36
pcspkr                 11136  0
parport_pc             45096  1
parport                49584  3 lp,ppdev,parport_pc
floppy                 75816  0
ohci1394               42036  0
forcedeth              68368  0
ieee1394              108288  2 sbp2,ohci1394
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

lsb_release

```
Description:    Ubuntu 9.04
```

uname -mr

```
2.6.28-12-generic x86_64
```

dmesg

```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800                                                                                                                              
[    0.000000] Initializing cgroup subsys cpuset                                                                                                                                   
[    0.000000] Initializing cgroup subsys cpu                                                                                                                                      
[    0.000000] Linux version 2.6.28-12-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 (Ubuntu 2.6.28-12.43-generic)                                                                                                                                                                                   
[    0.000000] Command line: root=UUID=c3f335d4-2671-4dbc-a8f8-5051d8c230df ro quiet splash                                                                                         
[    0.000000] KERNEL supported cpus:                                                                                                                                               
[    0.000000]   Intel GenuineIntel                                                                                                                                                 
[    0.000000]   AMD AuthenticAMD                                                                                                                                                   
[    0.000000]   Centaur CentaurHauls                                                                                                                                               
[    0.000000] BIOS-provided physical RAM map:                                                                                                                                      
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)                                                                                                             
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfff0000 (usable)                                                                                                             
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)                                                                                                           
[    0.000000]  BIOS-e820: 00000000cfff3000 - 00000000d0000000 (ACPI data)                                                                                                          
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)                                                                                                             
[    0.000000] DMI 2.3 present.                                                                                                                                                     
[    0.000000] last_pfn = 0x1b0000 max_arch_pfn = 0x3ffffffff                                                                                                                       
[    0.000000] last_pfn = 0xcfff0 max_arch_pfn = 0x3ffffffff                                                                                                                        
[    0.000000] Scanning 2 areas for low memory corruption                                                                                                                           
[    0.000000] modified physical RAM map:                                                                                                                                           
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)                                                                                                              
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)                                                                                                              
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)                                                                                                              
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000100000 - 00000000cfff0000 (usable)                                                                                                              
[    0.000000]  modified: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)                                                                                                            
[    0.000000]  modified: 00000000cfff3000 - 00000000d0000000 (ACPI data)                                                                                                           
[    0.000000]  modified: 00000000d0000000 - 00000000e0000000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000100000000 - 00000001b0000000 (usable)                                                                                                              
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfff0000                                                                                                               
[    0.000000]  0000000000 - 00cfe00000 page 2M                                                                                                                                     
[    0.000000]  00cfe00000 - 00cfff0000 page 4k                                                                                                                                     
[    0.000000] kernel direct mapping tables up to cfff0000 @ 10000-16000                                                                                                            
[    0.000000] last_map_addr: cfff0000 end: cfff0000                                                                                                                                
[    0.000000] init_memory_mapping: 0000000100000000-00000001b0000000                                                                                                               
[    0.000000]  0100000000 - 01b0000000 page 2M                                                                                                                                     
[    0.000000] kernel direct mapping tables up to 1b0000000 @ 14000-1c000                                                                                                           
[    0.000000] last_map_addr: 1b0000000 end: 1b0000000                                                                                                                              
[    0.000000] RAMDISK: 37856000 - 37fef949                                                                                                                                         
[    0.000000] ACPI: RSDP 000F6630, 0014 (r0 Nvidia)                                                                                                                                
[    0.000000] ACPI: RSDT CFFF3000, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)                                                                                                
[    0.000000] ACPI: FACP CFFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)                                                                                                
[    0.000000] ACPI: DSDT CFFF30C0, 42D0 (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)                                                                                                
[    0.000000] ACPI: FACS CFFF0000, 0040                                                                                                                                            
[    0.000000] ACPI: SSDT CFFF7440, 030E (r1 PTLTD  POWERNOW        1  LTP        1)                                                                                                
[    0.000000] ACPI: MCFG CFFF7780, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)                                                                                                
[    0.000000] ACPI: APIC CFFF73C0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)                                                                                                
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                                                                  
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 01b0000000]                                                                                                         
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                                        
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]                                                                                        
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]                                                                                        
[    0.000000]   #3 [0037856000 - 0037fef949]          RAMDISK ==> [0037856000 - 0037fef949]                                                                                        
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]                                                                                        
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]                                                                                        
[    0.000000]   #6 [0000014000 - 0000017000]          PGTABLE ==> [0000014000 - 0000017000]                                                                                        
[    0.000000] found SMP MP-table at [ffff8800000f4cc0] 000f4cc0                                                                                                                    
[    0.000000]  [ffffe20000000000-ffffe20005ffffff] PMD -> [ffff880028200000-ffff88002e1fffff] on node 0                                                                            
[    0.000000] Zone PFN ranges:                                                                                                                                                     
[    0.000000]   DMA      0x00000000 -> 0x00001000                                                                                                                                  
[    0.000000]   DMA32    0x00001000 -> 0x00100000                                                                                                                                  
[    0.000000]   Normal   0x00100000 -> 0x001b0000                                                                                                                                  
[    0.000000] Movable zone start PFN for each node                                                                                                                                 
[    0.000000] early_node_map[5] active PFN ranges                                                                                                                                  
[    0.000000]     0: 0x00000000 -> 0x00000001                                                                                                                                      
[    0.000000]     0: 0x00000006 -> 0x00000008                                                                                                                                      
[    0.000000]     0: 0x00000010 -> 0x00000092                                                                                                                                      
[    0.000000]     0: 0x00000100 -> 0x000cfff0                                                                                                                                      
[    0.000000]     0: 0x00100000 -> 0x001b0000                                                                                                                                      
[    0.000000] On node 0 totalpages: 1572725                                                                                                                                        
[    0.000000]   DMA zone: 56 pages used for memmap                                                                                                                                 
[    0.000000]   DMA zone: 2535 pages reserved                                                                                                                                      
[    0.000000]   DMA zone: 1382 pages, LIFO batch:0                                                                                                                                 
[    0.000000]   DMA32 zone: 14280 pages used for memmap                                                                                                                            
[    0.000000]   DMA32 zone: 833576 pages, LIFO batch:31                                                                                                                            
[    0.000000]   Normal zone: 9856 pages used for memmap                                                                                                                            
[    0.000000]   Normal zone: 711040 pages, LIFO batch:31                                                                                                                           
[    0.000000]   Movable zone: 0 pages used for memmap                                                                                                                              
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.                                                                                                                 
[    0.000000] If you got timer trouble try acpi_use_timer_override                                                                                                                 
[    0.000000] Detected use of extended apic ids on hypertransport bus                                                                                                              
[    0.000000] ACPI: PM-Timer IO Port: 0x1008                                                                                                                                       
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                                                                  
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                                                                                                                   
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                                                                                                                   
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])                                                                                                                    
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])                                                                                                                    
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])                                                                                                              
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23                                                                                                        
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                                                                             
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.                                                                                                                               
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                                                                          
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)                                                                                                         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)                                                                                                         
[    0.000000] ACPI: IRQ9 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ14 used by override.                                                                                                                                        
[    0.000000] ACPI: IRQ15 used by override.                                                                                                                                        
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                                                                                  
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                                                                                                                                 
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000                                                                                                    
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000                                                                                                    
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000cfff0000 - 00000000cfff3000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000cfff3000 - 00000000d0000000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000e0000000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fec00000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000                                                                                                    
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:1ec00000)                                                                                               
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data                                                                                                                       
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1                                                                                                                            
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1545998                                                                                         
[    0.000000] Kernel command line: root=UUID=c3f335d4-2671-4dbc-a8f8-5051d8c230df ro quiet splash                                                                                  
[    0.000000] Initializing CPU#0                                                                                                                                                   
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)                                                                                                                
[    0.000000] Fast TSC calibration using PIT                                                                                                                                       
[    0.000000] Detected 3015.578 MHz processor.                                                                                                                                     
[    0.004000] spurious 8259A interrupt: IRQ7.                                                                                                                                      
[    0.004000] Console: colour VGA+ 80x25                                                                                                                                           
[    0.004000] console [tty0] enabled                                                                                                                                               
[    0.004000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)                                                                                                  
[    0.004000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)                                                                                                    
[    0.004000] allocated 70778880 bytes of page_cgroup                                                                                                                              
[    0.004000] please try cgroup_disable=memory option if you don't want                                                                                                            
[    0.004000] Scanning for low memory corruption every 60 seconds                                                                                                                  
[    0.004000] Checking aperture...                                                                                                                                                 
[    0.004000] No AGP bridge found                                                                                                                                                  
[    0.004000] Node 0: aperture @ 20000000 size 32 MB                                                                                                                               
[    0.004000] Aperture pointing to e820 RAM. Ignoring.                                                                                                                             
[    0.004000] Your BIOS doesn't leave a aperture memory hole                                                                                                                       
[    0.004000] Please enable the IOMMU option in the BIOS setup                                                                                                                     
[    0.004000] This costs you 64 MB of RAM                                                                                                                                          
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000                                                                                                                     
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000                                                                                                    
[    0.004000] Memory: 6026724k/7077888k available (4743k kernel code, 786988k absent, 263204k reserved, 2525k data, 532k init)                                                     
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                                                                              
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6031.15 BogoMIPS (lpj=12062312)                                                           
[    0.004022] Security Framework initialized                                                                                                                                       
[    0.004027] SELinux:  Disabled at boot.                                                                                                                                          
[    0.004039] AppArmor: AppArmor initialized                                                                                                                                       
[    0.004045] Mount-cache hash table entries: 256                                                                                                                                  
[    0.004132] Initializing cgroup subsys ns                                                                                                                                        
[    0.004135] Initializing cgroup subsys cpuacct                                                                                                                                   
[    0.004137] Initializing cgroup subsys memory                                                                                                                                    
[    0.004139] Initializing cgroup subsys freezer                                                                                                                                   
[    0.004149] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                                                                                    
[    0.004150] CPU: L2 Cache: 1024K (64 bytes/line)                                                                                                                                 
[    0.004151] tseg: 0000000000                                                                                                                                                     
[    0.004162] CPU: Physical Processor ID: 0                                                                                                                                        
[    0.004163] CPU: Processor Core ID: 0                                                                                                                                            
[    0.004165] using C1E aware idle routine                                                                                                                                         
[    0.005313] ACPI: Core revision 20080926                                                                                                                                         
[    0.006372] ACPI: Checking initramfs for custom DSDT                                                                                                                             
[    0.198306] Setting APIC routing to flat                                                                                                                                         
[    0.198630] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1                                                                                                                 
[    0.238322] CPU0: AMD Processor model unknown stepping 03                                                                                                                        
[    0.240001] Booting processor 1 APIC 0x1 ip 0x6000                                                                                                                               
[    0.004000] Initializing CPU#1                                                                                                                                                   
[    0.004000] Calibrating delay using timer specific routine.. 6031.28 BogoMIPS (lpj=12062576)                                                                                     
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                                                                                    
[    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)                                                                                                                                 
[    0.004000] CPU: Physical Processor ID: 0                                                                                                                                        
[    0.004000] CPU: Processor Core ID: 1                                                                                                                                            
[    0.324133] CPU1: AMD Processor model unknown stepping 03                                                                                                                        
[    0.324142] Brought up 2 CPUs                                                                                                                                                    
[    0.324143] Total of 2 processors activated (12062.44 BogoMIPS).                                                                                                                 
[    0.324191] CPU0 attaching sched-domain:                                                                                                                                         
[    0.324192]  domain 0: span 0-1 level CPU                                                                                                                                        
[    0.324194]   groups: 0 1                                                                                                                                                        
[    0.324197] CPU1 attaching sched-domain:                                                                                                                                         
[    0.324198]  domain 0: span 0-1 level CPU                                                                                                                                        
[    0.324199]   groups: 1 0                                                                                                                                                        
[    0.324238] net_namespace: 1400 bytes                                                                                                                                            
[    0.324238] Booting paravirtualized kernel on bare hardware                                                                                                                      
[    0.324238] Time: 18:51:10  Date: 05/16/09                                                                                                                                       
[    0.324238] regulator: core version 0.5                                                                                                                                          
[    0.324238] NET: Registered protocol family 16                                                                                                                                   
[    0.324238] node 0 link 0: io port [1000, fffff]                                                                                                                                 
[    0.324238] TOM: 00000000d0000000 aka 3328M                                                                                                                                      
[    0.324238] node 0 link 0: mmio [d0000000, dfffffff]                                                                                                                             
[    0.324238] node 0 link 0: mmio [feb00000, fec0ffff]                                                                                                                             
[    0.324238] node 0 link 0: mmio [a0000, bffff]                                                                                                                                   
[    0.324238] node 0 link 0: mmio [d0000000, ffb7ffff]                                                                                                                             
[    0.324238] TOM2: 00000001b0000000 aka 6912M                                                                                                                                     
[    0.324238] bus: [00,ff] on node 0 link 0                                                                                                                                        
[    0.324238] bus: 00 index 0 io port: [0, ffff]                                                                                                                                   
[    0.324238] bus: 00 index 1 mmio: [d0000000, ffffffff]                                                                                                                           
[    0.324238] bus: 00 index 2 mmio: [feb00000, fec0ffff]                                                                                                                           
[    0.324238] bus: 00 index 3 mmio: [a0000, bffff]                                                                                                                                 
[    0.324238] bus: 00 index 4 mmio: [1b0000000, fcffffffff]                                                                                                                        
[    0.324238] ACPI: bus type pci registered                                                                                                                                        
[    0.324238] PCI: MCFG configuration 0: base d0000000 segment 0 buses 0 - 255                                                                                                     
[    0.324238] PCI: MCFG area at d0000000 reserved in E820                                                                                                                          
[    0.334184] PCI: Using MMCONFIG at d0000000 - dfffffff                                                                                                                           
[    0.334186] PCI: Using configuration type 1 for base access                                                                                                                      
[    0.334595] ACPI: EC: Look up EC in DSDT                                                                                                                                         
[    0.340168] ACPI: Interpreter enabled                                                                                                                                            
[    0.340170] ACPI: (supports S0 S1 S4 S5)                                                                                                                                         
[    0.340183] ACPI: Using IOAPIC for interrupt routing                                                                                                                             
[    0.344945] ACPI: No dock devices found.                                                                                                                                         
[    0.344952] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                                                                               
[    0.345021] HPET not enabled in BIOS. You might try hpet=force boot option                                                                                                       
[    0.345031] pci 0000:00:01.1: reg 10 io port: [0xec00-0xec1f]                                                                                                                    
[    0.345037] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]                                                                                                                    
[    0.345040] pci 0000:00:01.1: reg 24 io port: [0x1c40-0x1c7f]                                                                                                                    
[    0.345045] pci 0000:00:01.1: PME# supported from D3hot D3cold                                                                                                                   
[    0.345047] pci 0000:00:01.1: PME# disabled                                                                                                                                      
[    0.345060] pci 0000:00:02.0: reg 10 32bit mmio: [0xf4102000-0xf4102fff]                                                                                                         
[    0.345070] pci 0000:00:02.0: supports D1 D2                                                                                                                                     
[    0.345072] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345073] pci 0000:00:02.0: PME# disabled                                                                                                                                      
[    0.345086] pci 0000:00:02.1: reg 10 32bit mmio: [0xfeb00000-0xfeb000ff]                                                                                                         
[    0.345097] pci 0000:00:02.1: supports D1 D2                                                                                                                                     
[    0.345098] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345100] pci 0000:00:02.1: PME# disabled                                                                                                                                      
[    0.345117] pci 0000:00:04.0: reg 10 io port: [0xb800-0xb8ff]                                                                                                                    
[    0.345119] pci 0000:00:04.0: reg 14 io port: [0xbc00-0xbcff]                                                                                                                    
[    0.345121] pci 0000:00:04.0: reg 18 32bit mmio: [0xf4105000-0xf4105fff]                                                                                                         
[    0.345129] pci 0000:00:04.0: supports D1 D2                                                                                                                                     
[    0.345144] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]                                                                                                                    
[    0.345158] pci 0000:00:07.0: reg 10 io port: [0x9f0-0x9f7]                                                                                                                      
[    0.345160] pci 0000:00:07.0: reg 14 io port: [0xbf0-0xbf3]                                                                                                                      
[    0.345162] pci 0000:00:07.0: reg 18 io port: [0x970-0x977]                                                                                                                      
[    0.345164] pci 0000:00:07.0: reg 1c io port: [0xb70-0xb73]                                                                                                                      
[    0.345167] pci 0000:00:07.0: reg 20 io port: [0xd000-0xd00f]                                                                                                                    
[    0.345169] pci 0000:00:07.0: reg 24 32bit mmio: [0xf4100000-0xf4100fff]                                                                                                         
[    0.345182] pci 0000:00:08.0: reg 10 io port: [0x9e0-0x9e7]                                                                                                                      
[    0.345184] pci 0000:00:08.0: reg 14 io port: [0xbe0-0xbe3]                                                                                                                      
[    0.345187] pci 0000:00:08.0: reg 18 io port: [0x960-0x967]                                                                                                                      
[    0.345189] pci 0000:00:08.0: reg 1c io port: [0xb60-0xb63]                                                                                                                      
[    0.345191] pci 0000:00:08.0: reg 20 io port: [0xe400-0xe40f]                                                                                                                    
[    0.345193] pci 0000:00:08.0: reg 24 32bit mmio: [0xf4101000-0xf4101fff]                                                                                                         
[    0.345213] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf4103000-0xf4103fff]                                                                                                         
[    0.345216] pci 0000:00:0a.0: reg 14 io port: [0xe800-0xe807]                                                                                                                    
[    0.345224] pci 0000:00:0a.0: supports D1 D2                                                                                                                                     
[    0.345226] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345227] pci 0000:00:0a.0: PME# disabled                                                                                                                                      
[    0.345242] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345243] pci 0000:00:0b.0: PME# disabled                                                                                                                                      
[    0.345258] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345260] pci 0000:00:0c.0: PME# disabled                                                                                                                                      
[    0.345274] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345275] pci 0000:00:0d.0: PME# disabled                                                                                                                                      
[    0.345290] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.345291] pci 0000:00:0e.0: PME# disabled                                                                                                                                      
[    0.345360] pci 0000:01:07.0: reg 10 32bit mmio: [0xf4000000-0xf400ffff]                                                                                                         
[    0.345397] pci 0000:01:0a.0: reg 10 32bit mmio: [0xf4014000-0xf40147ff]                                                                                                         
[    0.345401] pci 0000:01:0a.0: reg 14 32bit mmio: [0xf4010000-0xf4013fff]                                                                                                         
[    0.345418] pci 0000:01:0a.0: supports D1 D2                                                                                                                                     
[    0.345419] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot                                                                                                                 
[    0.345421] pci 0000:01:0a.0: PME# disabled                                                                                                                                      
[    0.345438] pci 0000:00:09.0: transparent bridge                                                                                                                                 
[    0.345440] pci 0000:00:09.0: bridge 32bit mmio: [0xf4000000-0xf40fffff]                                                                                                         
[    0.345465] pci 0000:00:0b.0: bridge io port: [0x9000-0x9fff]                                                                                                                    
[    0.345490] pci 0000:00:0c.0: bridge io port: [0x8000-0x8fff]                                                                                                                    
[    0.345515] pci 0000:00:0d.0: bridge io port: [0x7000-0x7fff]                                                                                                                    
[    0.345535] pci 0000:05:00.0: reg 10 32bit mmio: [0xf2000000-0xf2ffffff]                                                                                                         
[    0.345541] pci 0000:05:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]                                                                                                         
[    0.345546] pci 0000:05:00.0: reg 1c 64bit mmio: [0xf0000000-0xf1ffffff]                                                                                                         
[    0.345549] pci 0000:05:00.0: reg 24 io port: [0xa000-0xa07f]                                                                                                                    
[    0.345553] pci 0000:05:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]                                                                                                             
[    0.345583] pci 0000:00:0e.0: bridge io port: [0xa000-0xafff]                                                                                                                    
[    0.345585] pci 0000:00:0e.0: bridge 32bit mmio: [0xf0000000-0xf3ffffff]                                                                                                         
[    0.345587] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]                                                                                                    
[    0.345594] bus 00 -> node 0                                                                                                                                                     
[    0.345598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                                                                                  
[    0.345829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]                                                                                                             
[    0.384165] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.384273] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.384381] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 *11 12 14 15)                                                                                                     
[    0.384493] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 7 9 10 11 12 14 15)                                                                                                     
[    0.384603] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.384714] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)                                                                                                     
[    0.384824] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.384937] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)                                                                                                     
[    0.385048] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 *10 11 12 14 15)                                                                                                     
[    0.385158] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.385270] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 *11 12 14 15)                                                                                                     
[    0.385381] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)                                                                                                     
[    0.385491] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.385608] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)                                                                                                     
[    0.385726] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)                                                                                                     
[    0.385842] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.385969] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.                                                                                                              
[    0.386092] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.                                                                                                              
[    0.386214] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0                                                                                                                         
[    0.386337] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0                                                                                                                         
[    0.386416] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.                                                                                                                
[    0.386545] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0                                                                                                                
[    0.386676] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.                                                                                                     
[    0.386804] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0                                                                                                                
[    0.386932] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0                                                                                                                
[    0.387061] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.                                                                                                     
[    0.387189] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0                                                                                                                
[    0.387317] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0                                                                                                                
[    0.387446] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.                                                                                                     
[    0.387581] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0                                                                                                                
[    0.387715] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0                                                                                                                
[    0.387850] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.                                                                                                     
[    0.387928] ACPI: WMI: Mapper loaded                                                                                                                                             
[    0.388056] SCSI subsystem initialized                                                                                                                                           
[    0.388069] libata version 3.00 loaded.                                                                                                                                          
[    0.388069] usbcore: registered new interface driver usbfs                                                                                                                       
[    0.388069] usbcore: registered new interface driver hub                                                                                                                         
[    0.388069] usbcore: registered new device driver usb                                                                                                                            
[    0.388069] PCI: Using ACPI for IRQ routing                                                                                                                                      
[    0.400006] Bluetooth: Core ver 2.13                                                                                                                                             
[    0.400017] NET: Registered protocol family 31                                                                                                                                   
[    0.400017] Bluetooth: HCI device and connection manager initialized                                                                                                             
[    0.400017] Bluetooth: HCI socket layer initialized                                                                                                                              
[    0.400017] NET: Registered protocol family 8                                                                                                                                    
[    0.400017] NET: Registered protocol family 20                                                                                                                                   
[    0.400022] NetLabel: Initializing                                                                                                                                               
[    0.400023] NetLabel:  domain hash size = 128                                                                                                                                    
[    0.400024] NetLabel:  protocols = UNLABELED CIPSOv4                                                                                                                             
[    0.400034] NetLabel:  unlabeled traffic allowed by default                                                                                                                      
[    0.400105] PCI-DMA: Disabling AGP.                                                                                                                                              
[    0.400172] PCI-DMA: aperture base @ 20000000 size 65536 KB                                                                                                                      
[    0.400173] PCI-DMA: using GART IOMMU.                                                                                                                                           
[    0.400176] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture                                                                                                            
[    0.400943] AppArmor: AppArmor Filesystem Enabled                                                                                                                                
[    0.412010] pnp: PnP ACPI init                                                                                                                                                   
[    0.412023] ACPI: bus type pnp registered                                                                                                                                        
[    0.414793] pnp: PnP ACPI: found 13 devices                                                                                                                                      
[    0.414794] ACPI: ACPI bus type pnp unregistered                                                                                                                                 
[    0.414802] system 00:01: ioport range 0x1000-0x107f has been reserved                                                                                                           
[    0.414803] system 00:01: ioport range 0x1080-0x10ff has been reserved                                                                                                           
[    0.414805] system 00:01: ioport range 0x1400-0x147f has been reserved                                                                                                           
[    0.414806] system 00:01: ioport range 0x1480-0x14ff has been reserved                                                                                                           
[    0.414808] system 00:01: ioport range 0x1800-0x187f has been reserved                                                                                                           
[    0.414809] system 00:01: ioport range 0x1880-0x18ff has been reserved                                                                                                           
[    0.414813] system 00:02: ioport range 0x4d0-0x4d1 has been reserved                                                                                                             
[    0.414815] system 00:02: ioport range 0x800-0x87f has been reserved                                                                                                             
[    0.414816] system 00:02: ioport range 0x295-0x314 has been reserved                                                                                                             
[    0.414818] system 00:02: ioport range 0x290-0x294 has been reserved                                                                                                             
[    0.414819] system 00:02: ioport range 0x294-0x297 could not be reserved                                                                                                         
[    0.414824] system 00:0b: iomem range 0xd0000000-0xdfffffff has been reserved                                                                                                    
[    0.414827] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved                                                                                                          
[    0.414829] system 00:0c: iomem range 0xd5800-0xd7fff has been reserved                                                                                                          
[    0.414830] system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved                                                                                                      
[    0.414832] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved                                                                                                      
[    0.414834] system 00:0c: iomem range 0xcfff0000-0xcfffffff could not be reserved                                                                                                
[    0.414835] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved                                                                                                    
[    0.414837] system 00:0c: iomem range 0x0-0x9ffff could not be reserved                                                                                                          
[    0.414838] system 00:0c: iomem range 0x100000-0xcffeffff could not be reserved                                                                                                  
[    0.414840] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved                                                                                                    
[    0.414842] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved                                                                                                    
[    0.419453] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01                                                                                                                  
[    0.419454] pci 0000:00:09.0:   IO window: disabled                                                                                                                              
[    0.419457] pci 0000:00:09.0:   MEM window: 0xf4000000-0xf40fffff                                                                                                                
[    0.419458] pci 0000:00:09.0:   PREFETCH window: disabled                                                                                                                        
[    0.419461] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02                                                                                                                  
[    0.419462] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff                                                                                                                         
[    0.419464] pci 0000:00:0b.0:   MEM window: disabled                                                                                                                             
[    0.419465] pci 0000:00:0b.0:   PREFETCH window: disabled                                                                                                                        
[    0.419467] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03                                                                                                                  
[    0.419469] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff                                                                                                                         
[    0.419471] pci 0000:00:0c.0:   MEM window: disabled                                                                                                                             
[    0.419472] pci 0000:00:0c.0:   PREFETCH window: disabled                                                                                                                        
[    0.419474] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04                                                                                                                  
[    0.419476] pci 0000:00:0d.0:   IO window: 0x7000-0x7fff                                                                                                                         
[    0.419477] pci 0000:00:0d.0:   MEM window: disabled                                                                                                                             
[    0.419479] pci 0000:00:0d.0:   PREFETCH window: disabled                                                                                                                        
[    0.419482] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05                                                                                                                  
[    0.419484] pci 0000:00:0e.0:   IO window: 0xa000-0xafff                                                                                                                         
[    0.419486] pci 0000:00:0e.0:   MEM window: 0xf0000000-0xf3ffffff                                                                                                                
[    0.419487] pci 0000:00:0e.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff                                                                                               
[    0.419493] pci 0000:00:09.0: setting latency timer to 64                                                                                                                        
[    0.419496] pci 0000:00:0b.0: setting latency timer to 64                                                                                                                        
[    0.419499] pci 0000:00:0c.0: setting latency timer to 64                                                                                                                        
[    0.419502] pci 0000:00:0d.0: setting latency timer to 64                                                                                                                        
[    0.419505] pci 0000:00:0e.0: setting latency timer to 64                                                                                                                        
[    0.419507] bus: 00 index 0 io port: [0x00-0xffff]                                                                                                                               
[    0.419508] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]                                                                                                                  
[    0.419510] bus: 01 index 0 mmio: [0x0-0x0]                                                                                                                                      
[    0.419511] bus: 01 index 1 mmio: [0xf4000000-0xf40fffff]                                                                                                                        
[    0.419512] bus: 01 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.419513] bus: 01 index 3 io port: [0x00-0xffff]                                                                                                                               
[    0.419514] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]                                                                                                                  
[    0.419516] bus: 02 index 0 io port: [0x9000-0x9fff]                                                                                                                             
[    0.419517] bus: 02 index 1 mmio: [0x0-0x0]                                                                                                                                      
[    0.419518] bus: 02 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.419519] bus: 02 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.419520] bus: 03 index 0 io port: [0x8000-0x8fff]                                                                                                                             
[    0.419521] bus: 03 index 1 mmio: [0x0-0x0]                                                                                                                                      
[    0.419522] bus: 03 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.419523] bus: 03 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.419524] bus: 04 index 0 io port: [0x7000-0x7fff]                                                                                                                             
[    0.419525] bus: 04 index 1 mmio: [0x0-0x0]                                                                                                                                      
[    0.419526] bus: 04 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.419527] bus: 04 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.419528] bus: 05 index 0 io port: [0xa000-0xafff]                                                                                                                             
[    0.419529] bus: 05 index 1 mmio: [0xf0000000-0xf3ffffff]                                                                                                                        
[    0.419530] bus: 05 index 2 mmio: [0xe0000000-0xefffffff]                                                                                                                        
[    0.419532] bus: 05 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.419538] NET: Registered protocol family 2                                                                                                                                    
[    0.420014] Switched to high resolution mode on CPU 0                                                                                                                            
[    0.420148] Switched to high resolution mode on CPU 1                                                                                                                            
[    0.452049] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)                                                                                                  
[    0.453088] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)                                                                                                
[    0.455289] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                                                                                                         
[    0.455854] TCP: Hash tables configured (established 262144 bind 65536)                                                                                                          
[    0.455856] TCP reno registered                                                                                                                                                  
[    0.464083] NET: Registered protocol family 1                                                                                                                                    
[    0.464167] checking if image is initramfs... it is                                                                                                                              
[    0.852537] Freeing initrd memory: 7782k freed                                                                                                                                   
[    0.856272] audit: initializing netlink socket (disabled)                                                                                                                        
[    0.856284] type=2000 audit(1242499869.856:1): initialized                                                                                                                       
[    0.861834] HugeTLB registered 2 MB page size, pre-allocated 0 pages                                                                                                             
[    0.862621] VFS: Disk quotas dquot_6.5.1                                                                                                                                         
[    0.862654] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                                                                                                            
[    0.863025] fuse init (API version 7.10)                                                                                                                                         
[    0.863071] msgmni has been set to 11788                                                                                                                                         
[    0.863214] alg: No test for stdrng (krng)                                                                                                                                       
[    0.863224] io scheduler noop registered                                                                                                                                         
[    0.863226] io scheduler anticipatory registered                                                                                                                                 
[    0.863227] io scheduler deadline registered                                                                                                                                     
[    0.863251] io scheduler cfq registered (default)                                                                                                                                
[    0.863264] pci 0000:00:00.0: Enabling HT MSI Mapping                                                                                                                            
[    0.888118] pci 0000:00:0b.0: Enabling HT MSI Mapping                                                                                                                            
[    0.888123] pci 0000:00:0b.0: Found enabled HT MSI Mapping                                                                                                                       
[    0.888126] pci 0000:00:0b.0: Linking AER extended capability                                                                                                                    
[    0.888132] pci 0000:00:0c.0: Enabling HT MSI Mapping                                                                                                                            
[    0.888136] pci 0000:00:0c.0: Found enabled HT MSI Mapping                                                                                                                       
[    0.888138] pci 0000:00:0c.0: Linking AER extended capability                                                                                                                    
[    0.888144] pci 0000:00:0d.0: Enabling HT MSI Mapping                                                                                                                            
[    0.888149] pci 0000:00:0d.0: Found enabled HT MSI Mapping                                                                                                                       
[    0.888150] pci 0000:00:0d.0: Linking AER extended capability                                                                                                                    
[    0.888157] pci 0000:00:0e.0: Enabling HT MSI Mapping                                                                                                                            
[    0.888161] pci 0000:00:0e.0: Found enabled HT MSI Mapping                                                                                                                       
[    0.888162] pci 0000:00:0e.0: Linking AER extended capability                                                                                                                    
[    0.888176] pci 0000:05:00.0: Boot video device                                                                                                                                  
[    0.891445] pcieport-driver 0000:00:0b.0: setting latency timer to 64                                                                                                            
[    0.891459] pcieport-driver 0000:00:0b.0: found MSI capability                                                                                                                   
[    0.891469] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X                                                                                                                 
[    0.891473] pci_express 0000:00:0b.0:pcie00: allocate port service                                                                                                               
[    0.891481] pci_express 0000:00:0b.0:pcie03: allocate port service                                                                                                               
[    0.891503] pcieport-driver 0000:00:0c.0: setting latency timer to 64                                                                                                            
[    0.891515] pcieport-driver 0000:00:0c.0: found MSI capability                                                                                                                   
[    0.891522] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X                                                                                                                 
[    0.891526] pci_express 0000:00:0c.0:pcie00: allocate port service                                                                                                               
[    0.891533] pci_express 0000:00:0c.0:pcie03: allocate port service                                                                                                               
[    0.891556] pcieport-driver 0000:00:0d.0: setting latency timer to 64                                                                                                            
[    0.891568] pcieport-driver 0000:00:0d.0: found MSI capability                                                                                                                   
[    0.891575] pcieport-driver 0000:00:0d.0: irq 2301 for MSI/MSI-X                                                                                                                 
[    0.891579] pci_express 0000:00:0d.0:pcie00: allocate port service                                                                                                               
[    0.891586] pci_express 0000:00:0d.0:pcie03: allocate port service                                                                                                               
[    0.891607] pcieport-driver 0000:00:0e.0: setting latency timer to 64                                                                                                            
[    0.891619] pcieport-driver 0000:00:0e.0: found MSI capability                                                                                                                   
[    0.891626] pcieport-driver 0000:00:0e.0: irq 2300 for MSI/MSI-X                                                                                                                 
[    0.891630] pci_express 0000:00:0e.0:pcie00: allocate port service                                                                                                               
[    0.891637] pci_express 0000:00:0e.0:pcie03: allocate port service                                                                                                               
[    0.891663] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                                                                      
[    0.891669] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                                                                          
[    0.891756] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                                                            
[    0.891758] ACPI: Power Button (FF) [PWRF]                                                                                                                                       
[    0.891784] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                                   
[    0.891786] ACPI: Power Button (CM) [PWRB]                                                                                                                                       
[    0.892132] processor ACPI_CPU:00: registered as cooling_device0                                                                                                                 
[    0.892153] processor ACPI_CPU:01: registered as cooling_device1                                                                                                                 
[    0.921084] Linux agpgart interface v0.103                                                                                                                                       
[    0.921090] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                                                                                
[    0.921159] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                                                                 
[    0.921348] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                                                                      
[    0.921803] brd: module loaded                                                                                                                                                   
[    0.922003] loop: module loaded                                                                                                                                                  
[    0.922042] Fixed MDIO Bus: probed                                                                                                                                               
[    0.922045] PPP generic driver version 2.4.2                                                                                                                                     
[    0.922081] input: Macintosh mouse button emulation as /devices/virtual/input/input2                                                                                             
[    0.922097] Driver 'sd' needs updating - please use bus_type methods                                                                                                             
[    0.922103] Driver 'sr' needs updating - please use bus_type methods                                                                                                             
[    0.922217] sata_nv 0000:00:07.0: version 3.5                                                                                                                                    
[    0.922469] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23                                                                                                                    
[    0.922476] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23                                                                                       
[    0.922516] sata_nv 0000:00:07.0: setting latency timer to 64                                                                                                                    
[    0.922582] scsi0 : sata_nv                                                                                                                                                      
[    0.922670] scsi1 : sata_nv                                                                                                                                                      
[    0.922768] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd000 irq 23                                                                                                      
[    0.922770] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd008 irq 23                                                                                                      
[    1.644019] ata1: SATA link down (SStatus 0 SControl 300)                                                                                                                        
[    2.524023] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                                                                                                               
[    2.542923] ata2.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133                                                                                                        
[    2.542925] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)                                                                                                         
[    2.556496] ata2.00: configured for UDMA/133                                                                                                                                     
[    2.556565] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5                                                                                         
[    2.556621] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                                                                              
[    2.556632] sd 1:0:0:0: [sda] Write Protect is off                                                                                                                               
[    2.556633] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                                                            
[    2.556648] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    2.556693] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                                                                              
[    2.556701] sd 1:0:0:0: [sda] Write Protect is off                                                                                                                               
[    2.556703] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                                                            
[    2.556716] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    2.556719]  sda: sda1                                                                                                                                                           
[    2.563008] sd 1:0:0:0: [sda] Attached SCSI disk                                                                                                                                 
[    2.563034] sd 1:0:0:0: Attached scsi generic sg0 type 0                                                                                                                         
[    2.563282] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22                                                                                                                    
[    2.563287] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22                                                                                       
[    2.563315] sata_nv 0000:00:08.0: setting latency timer to 64                                                                                                                    
[    2.563370] scsi2 : sata_nv                                                                                                                                                      
[    2.563430] scsi3 : sata_nv                                                                                                                                                      
[    2.563525] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe400 irq 22                                                                                                      
[    2.563527] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe408 irq 22                                                                                                      
[    3.284018] ata3: SATA link down (SStatus 0 SControl 300)                                                                                                                        
[    4.008019] ata4: SATA link down (SStatus 0 SControl 300)                                                                                                                        
[    4.008076] pata_amd 0000:00:06.0: version 0.3.10                                                                                                                                
[    4.008099] pata_amd 0000:00:06.0: setting latency timer to 64                                                                                                                   
[    4.008179] scsi4 : pata_amd                                                                                                                                                     
[    4.008250] scsi5 : pata_amd                                                                                                                                                     
[    4.008770] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14                                                                                                      
[    4.008771] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15                                                                                                      
[    4.188230] ata5.00: HPA unlocked: 80041151 -> 80043264, native 80043264                                                                                                         
[    4.188232] ata5.00: ATA-6: Maxtor 5T040H4, TAH71DP0, max UDMA/100                                                                                                               
[    4.188234] ata5.00: 80043264 sectors, multi 16: LBA                                                                                                                             
[    4.196230] ata5.01: HPA unlocked: 156299375 -> 156301488, native 156301488                                                                                                      
[    4.196232] ata5.01: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100                                                                                                           
[    4.196234] ata5.01: 156301488 sectors, multi 16: LBA                                                                                                                            
[    4.196247] ata5: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c6c500) ACPI=0x3f01f (20:20:0x1f)                                                                  
[    4.196250] ata5: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c6c500) ACPI=0x3f01f (20:20:0x1f)                                                                  
[    4.212404] ata5.00: configured for UDMA/100                                                                                                                                     
[    4.220303] ata5.01: configured for UDMA/100                                                                                                                                     
[    4.384235] ata6.00: ATAPI: LITE-ON DVDRW SOHW-1693S, KS0B, max UDMA/66                                                                                                          
[    4.384247] ata6: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc6c6c500) ACPI=0x1f01f (30:600:0x13)                                                                 
[    4.400180] ata6.00: configured for UDMA/66                                                                                                                                      
[    4.400658] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 5T040H4   TAH7 PQ: 0 ANSI: 5                                                                                         
[    4.400707] sd 4:0:0:0: [sdb] 80043264 512-byte hardware sectors: (40.9 GB/38.1 GiB)                                                                                             
[    4.400715] sd 4:0:0:0: [sdb] Write Protect is off                                                                                                                               
[    4.400717] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                                                                                            
[    4.400731] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    4.400760] sd 4:0:0:0: [sdb] 80043264 512-byte hardware sectors: (40.9 GB/38.1 GiB)                                                                                             
[    4.400769] sd 4:0:0:0: [sdb] Write Protect is off                                                                                                                               
[    4.400770] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                                                                                            
[    4.400784] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    4.400786]  sdb: sdb1                                                                                                                                                           
[    4.421335] sd 4:0:0:0: [sdb] Attached SCSI disk                                                                                                                                 
[    4.421356] sd 4:0:0:0: Attached scsi generic sg1 type 0                                                                                                                         
[    4.421391] scsi 4:0:1:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5                                                                                         
[    4.421440] sd 4:0:1:0: [sdc] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)                                                                                            
[    4.421448] sd 4:0:1:0: [sdc] Write Protect is off                                                                                                                               
[    4.421449] sd 4:0:1:0: [sdc] Mode Sense: 00 3a 00 00                                                                                                                            
[    4.421463] sd 4:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    4.421493] sd 4:0:1:0: [sdc] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)                                                                                            
[    4.421501] sd 4:0:1:0: [sdc] Write Protect is off                                                                                                                               
[    4.421503] sd 4:0:1:0: [sdc] Mode Sense: 00 3a 00 00                                                                                                                            
[    4.421516] sd 4:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    4.421518]  sdc: sdc1 sdc2                                                                                                                                                      
[    4.461901] sd 4:0:1:0: [sdc] Attached SCSI disk                                                                                                                                 
[    4.461922] sd 4:0:1:0: Attached scsi generic sg2 type 0                                                                                                                         
[    4.462641] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1693S KS0B PQ: 0 ANSI: 5                                                                                         
[    4.466257] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray                                                                                                        
[    4.466259] Uniform CD-ROM driver Revision: 3.20                                                                                                                                 
[    4.466311] sr 5:0:0:0: Attached scsi CD-ROM sr0                                                                                                                                 
[    4.466333] sr 5:0:0:0: Attached scsi generic sg3 type 5                                                                                                                         
[    4.466589] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                                                                           
[    4.466793] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21                                                                                                                    
[    4.466798] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21                                                                                      
[    4.466808] ehci_hcd 0000:00:02.1: setting latency timer to 64                                                                                                                   
[    4.466810] ehci_hcd 0000:00:02.1: EHCI Host Controller                                                                                                                          
[    4.466848] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1                                                                                                 
[    4.466865] ehci_hcd 0000:00:02.1: debug port 1                                                                                                                                  
[    4.466868] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported                                                                                                        
[    4.466879] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000                                                                                                                     
[    4.477014] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00                                                                                                                    
[    4.477058] usb usb1: configuration #1 chosen from 1 choice                                                                                                                      
[    4.477076] hub 1-0:1.0: USB hub found                                                                                                                                           
[    4.477082] hub 1-0:1.0: 10 ports detected                                                                                                                                       
[    4.477154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                                                                               
[    4.477342] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20                                                                                                                    
[    4.477346] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20                                                                                      
[    4.477352] ohci_hcd 0000:00:02.0: setting latency timer to 64                                                                                                                   
[    4.477353] ohci_hcd 0000:00:02.0: OHCI Host Controller                                                                                                                          
[    4.477380] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2                                                                                                 
[    4.477395] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf4102000                                                                                                                     
[    4.534034] usb usb2: configuration #1 chosen from 1 choice                                                                                                                      
[    4.534048] hub 2-0:1.0: USB hub found                                                                                                                                           
[    4.534054] hub 2-0:1.0: 10 ports detected                                                                                                                                       
[    4.534110] uhci_hcd: USB Universal Host Controller Interface driver                                                                                                             
[    4.534152] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1                                                                                                               
[    4.534154] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                                       
[    4.534206] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                                                                             
[    4.545031] mice: PS/2 mouse device common for all mice                                                                                                                          
[    4.581052] rtc_cmos 00:04: RTC can wake from S4                                                                                                                                 
[    4.581076] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0                                                                                                                
[    4.581096] rtc0: alarms up to one year, y3k, 242 bytes nvram                                                                                                                    
[    4.581132] device-mapper: uevent: version 1.0.3                                                                                                                                 
[    4.581221] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com                                                                                     
[    4.581385] device-mapper: multipath: version 1.0.5 loaded                                                                                                                       
[    4.581386] device-mapper: multipath round-robin: version 1.0.0 loaded                                                                                                           
[    4.581563] cpuidle: using governor ladder                                                                                                                                       
[    4.581565] cpuidle: using governor menu                                                                                                                                         
[    4.581832] TCP cubic registered                                                                                                                                                 
[    4.581874] NET: Registered protocol family 10                                                                                                                                   
[    4.582117] lo: Disabled Privacy Extensions                                                                                                                                      
[    4.582293] NET: Registered protocol family 17                                                                                                                                   
[    4.582307] Bluetooth: L2CAP ver 2.11                                                                                                                                            
[    4.582308] Bluetooth: L2CAP socket layer initialized                                                                                                                            
[    4.582309] Bluetooth: SCO (Voice Link) ver 0.6                                                                                                                                  
[    4.582310] Bluetooth: SCO socket layer initialized                                                                                                                              
[    4.582353] Bluetooth: RFCOMM socket layer initialized                                                                                                                           
[    4.582358] Bluetooth: RFCOMM TTY layer initialized                                                                                                                              
[    4.582358] Bluetooth: RFCOMM ver 1.10                                                                                                                                           
[    4.582394] powernow-k8: Found 1 AMD Processor model unknown processors (2 cpu cores) (version 2.20.00)                                                                          
[    4.582447] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0x8                                                                                                                     
[    4.582448] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0xa                                                                                                                     
[    4.582450] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xc                                                                                                                     
[    4.582451] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xe                                                                                                                     
[    4.582452] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0x10                                                                                                                     
[    4.582453] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10                                                                                                                     
[    4.582454] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10                                                                                                                     
[    4.582455] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12                                                                                                                     
[    4.582553] registered taskstats version 1                                                                                                                                       
[    4.582649]   Magic number: 9:444:898                                                                                                                                            
[    4.582722] rtc_cmos 00:04: setting system clock to 2009-05-16 18:51:14 UTC (1242499874)                                                                                         
[    4.582724] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                                                                                 
[    4.582725] EDD information not available.                                                                                                                                       
[    4.582753] Freeing unused kernel memory: 532k freed                                                                                                                             
[    4.583003] Write protecting the kernel read-only data: 6684k                                                                                                                    
[    4.599271] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                                                                   
[    4.778248] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.                                                                                                  
[    4.779258] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23                                                                                                                    
[    4.779262] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23                                                                                     
[    4.779266] forcedeth 0000:00:0a.0: setting latency timer to 64                                                                                                                  
[    4.779303] nv_probe: set workaround bit for reversed mac addr                                                                                                                   
[    4.789022] usb 1-9: new high speed USB device using ehci_hcd and address 2                                                                                                      
[    4.790777] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18                                                                                                                    
[    4.790786] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18                                                                                      
[    4.840514] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f4014000-f40147ff]  Max Packet=[2048]  IR/IT contexts=[4/8]                                                 
[    4.854534] Floppy drive(s): fd0 is 1.44M                                                                                                                                        
[    4.871913] FDC 0 is a post-1991 82077                                                                                                                                           
[    5.056450] usb 1-9: configuration #1 chosen from 1 choice                                                                                                                       
[    5.296553] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:e6:5a:5e:f9                                                                                      
[    5.296556] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3                                                                                                      
[    5.351052] PM: Starting manual resume from disk                                                                                                                                 
[    5.351054] PM: Resume from partition 8:34                                                                                                                                       
[    5.351055] PM: Checking hibernation image.                                                                                                                                      
[    5.351202] PM: Resume from disk failed.                                                                                                                                         
[    5.386297] kjournald starting.  Commit interval 5 seconds                                                                                                                       
[    5.386305] EXT3-fs: mounted filesystem with ordered data mode.                                                                                                                  
[    5.417024] usb 2-10: new low speed USB device using ohci_hcd and address 2                                                                                                      
[    5.630091] usb 2-10: configuration #1 chosen from 1 choice                                                                                                                      
[    6.117089] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000b5c968]                                                                                                      
[    9.471126] udev: starting version 141                                                                                                                                           
[   10.034684] parport_pc 00:09: reported by Plug and Play ACPI                                                                                                                     
[   10.034723] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]                                                                                                                  
[   10.091459] input: PC Speaker as /devices/platform/pcspkr/input/input4                                                                                                           
[   10.800719] nvidia: module license 'NVIDIA' taints kernel.                                                                                                                       
[   10.828438] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00                                                                                                                   
[   10.828450] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40                                                                                                                   
[   10.852490] ppdev: user-space parallel port driver                                                                                                                               
[   11.055107] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18                                                                                        
[   11.055114] nvidia 0000:05:00.0: setting latency timer to 64                                                                                                                     
[   11.056325] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009                                                                                 
[   11.100563] usbcore: registered new interface driver hiddev                                                                                                                      
[   11.108385] input: Logitech Trackball as /devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.0/input/input5                                                                        
[   11.118472] Linux video capture interface: v2.00                                                                                                                                 
[   11.142455] generic-usb 0003:046D:C404.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:02.0-10/input0                                               
[   11.142475] usbcore: registered new interface driver usbhid                                                                                                                      
[   11.142477] usbhid: v2.6:USB HID core driver                                                                                                                                     
[   11.174641] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)                                                                                                                
[   11.180304] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:02.1/usb1/1-9/1-9:1.0/input/input6                                                                      
[   11.193144] usbcore: registered new interface driver uvcvideo                                                                                                                    
[   11.193161] USB Video Class driver (v0.1.0)                                                                                                                                      
[   11.305761] usbcore: registered new interface driver snd-usb-audio                                                                                                               
[   11.325134] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22                                                                                                                    
[   11.325138] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22                                                                                     
[   11.325207] Intel ICH 0000:00:04.0: setting latency timer to 64                                                                                                                  
[   11.648024] intel8x0_measure_ac97_clock: measured 53750 usecs (2640 samples)                                                                                                     
[   11.648026] intel8x0: clocking to 46909                                                                                                                                          
[   11.704714] lp0: using parport0 (interrupt-driven).                                                                                                                              
[   11.786487] Adding 6859744k swap on /dev/sdc2.  Priority:-1 extents:1 across:6859744k                                                                                            
[   12.321529] EXT3 FS on sdb1, internal journal                                                                                                                                    
[   43.247893] ReiserFS: sda1: found reiserfs format "3.6" with standard journal                                                                                                    
[   43.247908] ReiserFS: sda1: using ordered data mode                                                                                                                              
[   43.252909] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30               
[   43.253778] ReiserFS: sda1: checking transaction log (sda1)                                                                                                                      
[   43.257636] ReiserFS: sda1: Using r5 hash to sort names                                                                                                                          
[   43.306636] kjournald starting.  Commit interval 5 seconds                                                                                                                       
[   43.306855] EXT3 FS on sdc1, internal journal                                                                                                                                    
[   43.306859] EXT3-fs: mounted filesystem with ordered data mode.                                                                                                                  
[   44.743796] type=1505 audit(1242499914.658:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2952                                                    
[   44.743908] type=1505 audit(1242499914.658:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2952                                                          
[   44.743943] type=1505 audit(1242499914.658:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2952                            
[   44.743973] type=1505 audit(1242499914.658:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2952                                 
[   44.774667] type=1505 audit(1242499914.690:6): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2957                                                       
[   44.866242] type=1505 audit(1242499914.782:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2961                                           
[   44.866401] type=1505 audit(1242499914.782:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2961                                                          
[   44.887561] type=1505 audit(1242499914.802:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2965                                                        
[   56.841721] vboxdrv: Trying to deactivate the NMI watchdog permanently...                                                                                                        
[   56.841724] vboxdrv: Successfully done.                                                                                                                                          
[   56.841725] vboxdrv: Found 2 processor cores.                                                                                                                                    
[   56.842784] VBoxDrv: dbg - g_abExecMemory=ffffffffa0a7caa0                                                                                                                       
[   56.842799] vboxdrv: fAsync=1 offMin=0x176d52 offMax=0x176d52                                                                                                                    
[   56.842846] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.                                                                                                  
[   56.842847] vboxdrv: Successfully loaded version 2.1.4 (interface 0x000a0009).                                                                                                   
[   57.047486] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0c1b940                                                                                                                    
[   57.921779] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                                                                                                         
[   57.921781] Bluetooth: BNEP filters: protocol multicast                                                                                                                          
[   57.956036] Bridge firewalling registered                                                                                                                                        
[   62.091589] eth0: no link during initialization.                                                                                                                                 
[   62.093078] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                                         
[   81.916028] Clocksource tsc unstable (delta = -101374819 ns)                                                                                                                     
[  212.953156] cfg80211: Using static regulatory domain info                                                                                                                        
[  212.953162] cfg80211: Regulatory domain: US                                                                                                                                      
[  212.953165]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                                                                                   
[  212.953171]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)                                                                                                        
[  212.953175]  (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                                                                                        
[  212.953179]  (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                                                                                        
[  212.953183]  (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                                                                                        
[  212.953187]  (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)                                                                                                        
[  212.953191]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)                                                                                                        
[  212.955931] cfg80211: Calling CRDA for country: US                                                                                                                               
[  213.066199] cfg80211: Regulatory domain changed to country: US                                                                                                                   
[  213.066207]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                                                                                   
[  213.066213]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)                                                                                                        
[  213.066217]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)                                                                                                        
[  213.066222]  (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                                                                        
[  213.066226]  (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                                                                                        
[  213.066230]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)                                                                                                        
[  213.080772] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19                                                                                                                    
[  213.080791] ath5k 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19                                                                                         
[  213.080949] ath5k 0000:01:07.0: registered as 'phy0'                                                                                                                             
[  213.251716] phy0: Selected rate control algorithm 'minstrel'                                                                                                                     
[  213.310565] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)                                                                                                         
[  213.319299] udev: renamed network interface wlan0 to ath0                                                                                                                        
[  218.168389] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  219.525130] ath0: direct probe to AP ffff880196815ac0 try 1
[  219.607364] ath0 direct probe responded
[  219.607369] ath0: authenticate with AP ffff880196815ac0
[  219.711849] ath0: authenticated
[  219.711857] ath0: associate with AP ffff880196815ac0
[  219.909038] ath0: associate with AP ffff880196815ac0
[  220.109040] ath0: associate with AP ffff880196815ac0
[  220.309037] ath0: association with AP ffff880196815ac0 timed out
[  364.847986] ath0: authenticate with AP ffff880196815ac0
[  364.862967] ath0: authenticated
[  364.862973] ath0: associate with AP ffff880196815ac0
[  365.061034] ath0: associate with AP ffff880196815ac0
[  365.261038] ath0: associate with AP ffff880196815ac0
[  365.461061] ath0: association with AP ffff880196815ac0 timed out
[  377.677680] ath0: direct probe to AP ffff880196815ac0 try 1
[  377.681363] ath0: direct probe to AP ffff880196815ac0 try 1
[  377.695108] ath0 direct probe responded
[  377.695115] ath0: authenticate with AP ffff880196815ac0
[  377.861246] ath0: authenticated
[  377.861254] ath0: associate with AP ffff880196815ac0
[  377.864549] ath0: RX AssocResp from ffff8801a857302a (capab=0x421 status=0 aid=3)
[  377.864554] ath0: associated
[  377.872168] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  388.605028] ath0: no IPv6 routers present
[  390.795953] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1203.820040] ath0: deauthenticating by local choice (reason=3)
[ 1204.210529] ath5k 0000:01:07.0: PCI INT A disabled
[ 1208.663841] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1208.686213] wlan: 0.9.4
[ 1208.704223] ath_pci: 0.9.4
[ 1208.704297] ath_pci 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[ 1209.287851] ath_rate_sample: 1.2 (0.9.4)
[ 1209.290116] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 1209.290126] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1209.290143] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1209.290154] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 1209.290161] wifi0: mac 7.9 phy 4.5 radio 5.6
[ 1209.290168] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 1209.290171] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 1209.290175] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 1209.290178] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 1209.290181] wifi0: Use hw queue 8 for CAB traffic
[ 1209.290184] wifi0: Use hw queue 9 for beacons
[ 1209.325559] wifi0: Atheros 5212: mem=0xf4000000, irq=19
[ 1224.744025] ath0: no IPv6 routers present
```

---

### Post by nothingspecial on 2009-05-16
After an awful lot of messing about simply adding ath5k to /etc/modules fixed it for me. Hope it does for you.

---

### Post by OmnipotentEntity on 2009-05-16
As I mentioned in OP, I've already tried the ath5k driver.

---

### Post by nothingspecial on 2009-05-16
That`s what I`d been using and it worked untill today, but I hadn`t added it to /etc/modules. It wasn`t in there.

---

### Post by OmnipotentEntity on 2009-05-16
I went ahead and tried that, rebooted, no dice.

Any other ideas?

---

### Post by sandrogalli on 2010-01-31
I have the exact same hardware (AR5001x) and have the exact same issue attempting to authenticate to WPA2 networks using 9.10. Looks like it might be a ubuntu specific bug...

---

### Post by SuperSonic4 on 2010-01-31
Is WPA supplicant installed?

---

