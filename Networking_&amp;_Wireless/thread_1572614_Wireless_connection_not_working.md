---
title: "Wireless connection not working"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by rmforum on 2010-09-11
Hi,

I'm recent to Ubuntu and have just installed version 10.04 32bits desktop version along side my Windows XP.

My wireless internet connection works perfectly under Windows XP as this thread can prove it, but it does not work on Ubuntu.

When checking the connections on Ubuntu I see:

Wireless Network - disconnected
 


Here's some of the displays that I have done:

**ifconfig**
```

 eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c3:b8:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

  
``` **ifconfig wlan0**

  ```

 wlan0     Link encap:Ethernet  HWaddr 00:14:a5:69:55:f9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  
```[FONT=&quot]
**lspci**
[/FONT]```

 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
  
```**lsmod**
```

 Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp_modem        9103  0 
snd_atiixp             12446  2 
snd_ac97_codec        100646  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674824  3 
ttm                    49943  1 radeon
b43                   163523  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 radeon
mac80211              205146  1 b43
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54148  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ati_agp                 5094  0 
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_atiixp_modem,snd_atiixp,snd_pcm
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28820  0 
i2c_piix4               8335  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  1 
usbhid                 36110  0 
8139too                18545  0 
8139cp                 16186  0 
hid                    67032  1 usbhid
mii                     4381  2 8139too,8139cp
ssb                    38671  1 b43
pata_atiixp             3148  2
  
``` **sudo lshw -C network**

  ```

   *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:c3:b8:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:69:55:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

  
```One other note; on Windows the Wireless Security I'm using is WPA-PSK but in Linux I  do not have this so I assume WPA & WPA2 personal is the closest?


Any help will be greatly appreciated!


Cheers!

---

### Post by MaindotC on 2010-09-11
> **rmforum said:**
> Ok, obviously as you can see, wlan0 has not been assigned an IP address.  You need an IP address in order to communicate on an IP network (which is what you are likely using).
> ```

 wlan0     Link encap:Ethernet  HWaddr 00:14:a5:69:55:f9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  
```Here's your wireless card - google this line:```

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```These are the modules that are being used for your card to operate.  Last I checked there is a problem with b43 and I think it has to be blacklisted and a different one has to be used.  I'm not precisely sure but that should get you on the right track:```
b43                   163523  0 
mac80211              205146  1 b43
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
ssb                    38671  1 b43
```Here we see once again the card is correctly identified and it even tells you the driver it is using```

   *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
```This looks to have to do with the problem.  Again, you'll find out more you google:```
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:69:55:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```For further configuration instructions, consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and there's even a doc on the [b43 driver and AirForceOne card](https://help.ubuntu.com/community/WifiDocs/Driver/b43).

The network protection thing will be addressed once you get the proper driver installed.  Good luck!

---

### Post by DjSesso on 2010-09-11
do an "apt-get install broadcom-wl" and then check to see that the "wl" module is loading. NOT the b43. 

If you have problems with the b43 adding itself. I think i did a "rmmod b43" before installing the broadcom-wl. Mine works fine after this.

---

### Post by MaindotC on 2010-09-11
I knew that blasted b43 was a problem!  It's "rmmod" btw.  But if you want to keep it from loading every time you boot you need to blacklist it in /etc/modprobe.d/blacklist.conf.

---

### Post by rmforum on 2010-09-11
When doing the "apt-get install broadcom-wl" I'm getting:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package broadcom-wl



Any idea where I can find this?

---

### Post by MaindotC on 2010-09-11
Just type in the Synaptic search box "broadcom".  The package is actually named broadcom-sta-common which will install the other files, or you can download it directly [here](http://www.broadcom.com/support/802.11/linux_sta.php).

---

### Post by rmforum on 2010-09-11
Ok, I've managed that to work, thanks!

Now I have another problem; My laptop doesn't seem to be able to connect to the wireless router. Is WPA & WPA2 Personal the same as WPA-PSK (the one that I use in Windows)?

---

### Post by rmforum on 2010-09-11
Ok, this may sound strange but I've deleted the wireless connection and created a new one... this time it worked! Go figure!

Anyway, thanks a lot for all your help!

---

### Post by MaindotC on 2010-09-11
It worked because you have something called a [keyring](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) that stores information about the network to which you connected in hopes of reducing time to connect to that network in the future.  When you deleted the network, you deleted any settings it contained that pertained to that network, which were probably misconfigured by the improper driver previously.

This is good to know in the future if you're having difficulty connecting to a network you normally can connect without a problem.  Delete the network information and re-enter it just as you did.

---

### Post by rmforum on 2010-09-12
Thanks for your expertise!

Today I'm having another strange problem. Ubuntu today doesn't seem to be able to detect the presence of my laptop's wireless device. It's working fine under Windows XP but not with Ubuntu.

Here's the data I've collected:

 1) HP Pavillion DV5052EA


2) lspci -nn | grep 'Wireless'

```
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```3) 

a) ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c3:b8:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1512 (1.5 KB)  TX bytes:1512 (1.5 KB)

```
b) iwconfig wlan0
```

wlan0     No such device

```
4) lsmod
```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp             12446  2 
snd_atiixp_modem        9103  5 
snd_ac97_codec        100646  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                674824  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162409  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd                    54148  23 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ati_agp                 5094  0 
video                  17375  0 
output                  1871  1 video
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,ati_agp
k8temp                  3024  0 
shpchp                 28820  0 
i2c_piix4               8335  0 
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_atiixp,snd_atiixp_modem,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
8139too                18545  0 
8139cp                 16186  0 
hid                    67032  1 usbhid
mii                     4381  2 8139too,8139cp
ssb                    38671  0 
pata_atiixp             3148  2 

  
```



 5) dmesg
  ```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000077ea0000 - 0000000077eac000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077eac000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x77ea0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-CFFFF uncachable
[    0.000000]   D0000-D5FFF write-back
[    0.000000]   D6000-D6FFF uncachable
[    0.000000]   D7000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0078000000 mask FFF8000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000077ea0000 (usable)
[    0.000000]  modified: 0000000077ea0000 - 0000000077eac000 (ACPI data)
[    0.000000]  modified: 0000000077eac000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  modified: 0000000077f00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37856000 - 37fefbd1
[    0.000000] Allocated new RAMDISK: 008e2000 - 0107bbd1
[    0.000000] Move RAMDISK from 0000000037856000 - 0000000037fefbd0 to 008e2000 - 0107bbd0
[    0.000000] ACPI: RSDP 000f7c40 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 77ea3ed4 00034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 77eabe3b 00074 (v01 HP     Piranha  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 77ea3f08 07F33 (v01     HP     309B 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 77eacfc0 00040
[    0.000000] ACPI: SSDT 77eabeaf 000CF (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 77eabf7e 00046 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 77eabfc4 0003C (v01 HP     PORSCHE  06040000 LOHR 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1030MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008de000 - 00008e1128]              BRK ==> [00008de000 - 00008e1128]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e2000 - 000107bbd1]      NEW RAMDISK ==> [00008e2000 - 000107bbd1]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7c70] f7c70
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00077ea0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077ea0
[    0.000000] On node 0 totalpages: 491067
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c107d000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2062 pages used for memmap
[    0.000000]   HighMem zone: 261780 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x82
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487229
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=bacf6a12-8079-4327-822a-5b1d84c0d62d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9823360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00077ea0)
[    0.000000] Memory: 1921636k/1964672k available (4679k kernel code, 41736k reserved, 2124k data, 660k init, 1055368k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1791.069 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3582.13 BogoMIPS (lpj=7164276)
[    0.004029] Security Framework initialized
[    0.004062] AppArmor: AppArmor initialized
[    0.004071] Mount-cache hash table entries: 512
[    0.004229] Initializing cgroup subsys ns
[    0.004233] Initializing cgroup subsys cpuacct
[    0.004238] Initializing cgroup subsys memory
[    0.004248] Initializing cgroup subsys devices
[    0.004251] Initializing cgroup subsys freezer
[    0.004253] Initializing cgroup subsys net_cls
[    0.004277] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004280] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004285] mce: CPU supports 5 MCE banks
[    0.004306] Performance Events: AMD PMU driver.
[    0.004314] ... version:                0
[    0.004316] ... bit width:              48
[    0.004318] ... generic registers:      4
[    0.004321] ... value mask:             0000ffffffffffff
[    0.004323] ... max period:             00007fffffffffff
[    0.004325] ... fixed-purpose events:   0
[    0.004328] ... event mask:             000000000000000f
[    0.004332] Checking 'hlt' instruction... OK.
[    0.020793] SMP alternatives: switching to UP code
[    0.027561] Freeing SMP alternatives: 19k freed
[    0.027584] ACPI: Core revision 20090903
[    0.040011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040023] ftrace: allocating 21780 entries in 43 pages
[    0.048078] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048426] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.088122] CPU0: AMD Turion(tm) 64 Mobile Technology ML-32 stepping 02
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (3582.13 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  9:14:50  Date: 09/12/10
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.092001] PCI: MCFG area at e0000000 reserved in E820
[    0.092001] PCI: Using MMCONFIG for extended config space
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092001] bio: create slab <bio-0> at 0
[    0.092001] ACPI: EC: Look up EC in DSDT
[    0.093268] ACPI: Interpreter enabled
[    0.093282] ACPI: (supports S0 S3 S4 S5)
[    0.093301] ACPI: Using IOAPIC for interrupt routing
[    0.152505] ACPI: EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
[    0.152655] ACPI: No dock devices found.
[    0.153748] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.153873] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.153877] pci 0000:00:05.0: PME# disabled
[    0.153946] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0000000-0xc0000fff]
[    0.154056] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0001000-0xc0001fff]
[    0.154175] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0002000-0xc0002fff]
[    0.154245] pci 0000:00:13.2: supports D1 D2
[    0.154248] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.154253] pci 0000:00:13.2: PME# disabled
[    0.154312] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.154322] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0003000-0xc00033ff]
[    0.154359] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.154425] pci 0000:00:14.1: reg 10 io port: [0x8430-0x8437]
[    0.154435] pci 0000:00:14.1: reg 14 io port: [0x8424-0x8427]
[    0.154444] pci 0000:00:14.1: reg 18 io port: [0x8428-0x842f]
[    0.154453] pci 0000:00:14.1: reg 1c io port: [0x8420-0x8423]
[    0.154463] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.154660] pci 0000:00:14.5: reg 10 32bit mmio: [0xc0003400-0xc00034ff]
[    0.154767] pci 0000:00:14.6: reg 10 32bit mmio: [0xc0003800-0xc00038ff]
[    0.154946] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.154951] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.154956] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.154967] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.154977] pci 0000:01:05.0: supports D1 D2
[    0.154995] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.154998] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.155003] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.155061] pci 0000:00:05.0: bridge io port: [0x00-0xfff]
[    0.155065] pci 0000:00:05.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.155109] pci 0000:06:02.0: reg 10 32bit mmio: [0xc0200000-0xc0201fff]
[    0.155222] pci 0000:06:06.0: reg 10 io port: [0xa000-0xa0ff]
[    0.155233] pci 0000:06:06.0: reg 14 32bit mmio: [0xc0202000-0xc02020ff]
[    0.155304] pci 0000:06:06.0: supports D1 D2
[    0.155306] pci 0000:06:06.0: PME# supported from D1 D2 D3hot D3cold
[    0.155312] pci 0000:06:06.0: PME# disabled
[    0.155373] pci 0000:00:14.4: transparent bridge
[    0.155382] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.155388] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.155406] pci_bus 0000:00: on NUMA node 0
[    0.155410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.155498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.155575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.155660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.157552] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.157648] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.157742] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.157836] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.157932] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.158028] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.158123] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.158219] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.158329] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.158333] vgaarb: loaded
[    0.158465] SCSI subsystem initialized
[    0.158545] libata version 3.00 loaded.
[    0.158620] usbcore: registered new interface driver usbfs
[    0.158633] usbcore: registered new interface driver hub
[    0.158661] usbcore: registered new device driver usb
[    0.158824] ACPI: WMI: Mapper loaded
[    0.158827] PCI: Using ACPI for IRQ routing
[    0.158834] pci 0000:00:05.0: BAR 13: can't allocate resource
[    0.158836] pci 0000:00:05.0: BAR 14: can't allocate resource
[    0.158997] NetLabel: Initializing
[    0.158999] NetLabel:  domain hash size = 128
[    0.159001] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.159015] NetLabel:  unlabeled traffic allowed by default
[    0.159069] Switching to clocksource tsc
[    0.160001] AppArmor: AppArmor Filesystem Enabled
[    0.160001] pnp: PnP ACPI init
[    0.160001] ACPI: bus type pnp registered
[    0.160150] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.184938] pnp: PnP ACPI: found 10 devices
[    0.184940] ACPI: ACPI bus type pnp unregistered
[    0.184945] PnPBIOS: Disabled by ACPI PNP
[    0.184960] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.184964] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.184968] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.184977] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.184981] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.184984] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.184988] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.184991] system 00:08: ioport range 0x870-0x87f has been reserved
[    0.184995] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.184998] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.185002] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.185005] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.185009] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.185013] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.185016] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.185020] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.185024] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.185027] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.185031] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.185037] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.185041] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.219758] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.219761] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.219765] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.219770] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.219775] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.219777] pci 0000:00:05.0:   IO window: disabled
[    0.219780] pci 0000:00:05.0:   MEM window: disabled
[    0.219783] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.219788] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06
[    0.219792] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.219800] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.219805] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.219825] pci 0000:00:05.0: setting latency timer to 64
[    0.219838] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.219841] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.219844] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.219847] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.219851] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xcfffffff]
[    0.219854] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
[    0.219857] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    0.219860] pci_bus 0000:06: resource 0 io:  [0xa000-0xafff]
[    0.219863] pci_bus 0000:06: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.219866] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.219870] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.219915] NET: Registered protocol family 2
[    0.220024] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.220450] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.221531] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.222128] TCP: Hash tables configured (established 131072 bind 65536)
[    0.222132] TCP reno registered
[    0.222261] NET: Registered protocol family 1
[    0.222279] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.222284] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.222357] pci 0000:01:05.0: Boot video device
[    0.222613] cpufreq-nforce2: No nForce2 chipset.
[    0.222644] Scanning for low memory corruption every 60 seconds
[    0.222786] audit: initializing netlink socket (disabled)
[    0.222805] type=2000 audit(1284282889.220:1): initialized
[    0.234117] Trying to unpack rootfs image as initramfs...
[    0.249209] highmem bounce pool size: 64 pages
[    0.249217] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.250818] VFS: Disk quotas dquot_6.5.2
[    0.250887] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.251505] fuse init (API version 7.13)
[    0.251594] msgmni has been set to 1693
[    0.257137] alg: No test for stdrng (krng)
[    0.257255] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.257258] io scheduler noop registered
[    0.257261] io scheduler anticipatory registered
[    0.257263] io scheduler deadline registered
[    0.257304] io scheduler cfq registered (default)
[    0.257447] pcieport 0000:00:05.0: setting latency timer to 64
[    0.257498] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.257522] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.259481] ACPI: AC Adapter [ACAD] (on-line)
[    0.259552] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.259603] ACPI: Lid Switch [LID]
[    0.259649] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.259652] ACPI: Power Button [PWRB]
[    0.259712] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.259715] ACPI: Power Button [PWRF]
[    0.259769] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input3
[    0.259772] ACPI: Sleep Button [SLPF]
[    0.259913] Marking TSC unstable due to TSC halts in idle
[    0.259991] processor LNXCPU:00: registered as cooling_device0
[    0.264227] Switching to clocksource acpi_pm
[    0.296595] ACPI: Invalid active0 threshold
[    0.301916] thermal LNXTHERM:01: registered as thermal_zone0
[    0.301931] ACPI: Thermal Zone [THRM] (0 C)
[    0.303614] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.303943]   alloc irq_desc for 17 on node -1
[    0.303946]   alloc kstat_irqs on node -1
[    0.303955] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.303963] serial 0000:00:14.6: PCI INT B disabled
[    0.305037] brd: module loaded
[    0.305542] loop: module loaded
[    0.305647] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.305791]   alloc irq_desc for 16 on node -1
[    0.305793]   alloc kstat_irqs on node -1
[    0.305800] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.305852] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.306168] Fixed MDIO Bus: probed
[    0.306203] PPP generic driver version 2.4.2
[    0.306244] tun: Universal TUN/TAP device driver, 1.6
[    0.306247] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.306327] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.306344]   alloc irq_desc for 19 on node -1
[    0.306346]   alloc kstat_irqs on node -1
[    0.306352] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.306376] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.306407] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.306480] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    0.312252] isapnp: Scanning for PnP cards...
[    0.317825] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.317975] usb usb1: configuration #1 chosen from 1 choice
[    0.318008] hub 1-0:1.0: USB hub found
[    0.318023] hub 1-0:1.0: 8 ports detected
[    0.318118] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.318144] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.318168] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.318211] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.318235] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    0.380293] usb usb2: configuration #1 chosen from 1 choice
[    0.380338] hub 2-0:1.0: USB hub found
[    0.380357] hub 2-0:1.0: 4 ports detected
[    0.380433] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.380458] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.380503] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.380533] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    0.464612] ACPI: Battery Slot [BAT1] (battery present)
[    0.468537] usb usb3: configuration #1 chosen from 1 choice
[    0.468572] hub 3-0:1.0: USB hub found
[    0.468591] hub 3-0:1.0: 4 ports detected
[    0.468667] uhci_hcd: USB Universal Host Controller Interface driver
[    0.468777] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.499679] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.499695] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.504297] mice: PS/2 mouse device common for all mice
[    0.504484] rtc_cmos 00:04: RTC can wake from S4
[    0.504538] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.504575] rtc0: alarms up to one month, 114 bytes nvram
[    0.504740] device-mapper: uevent: version 1.0.3
[    0.508236] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.508331] device-mapper: multipath: version 1.1.0 loaded
[    0.508336] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.508951] EISA: Probing bus 0 at eisa.0
[    0.508960] Cannot allocate resource for EISA slot 1
[    0.508990] Cannot allocate resource for EISA slot 8
[    0.508992] EISA: Detected 0 cards.
[    0.511555] cpuidle: using governor ladder
[    0.511613] cpuidle: using governor menu
[    0.512180] TCP cubic registered
[    0.512337] NET: Registered protocol family 10
[    0.512816] lo: Disabled Privacy Extensions
[    0.513151] NET: Registered protocol family 17
[    0.513196] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (1 cpu cores) (version 2.20.00)
[    0.513233] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[    0.513237] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[    0.513240] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[    0.513279] powernow-k8: ph2 null fid transition 0xa
[    0.513301] Using IPI No-Shortcut mode
[    0.513405] PM: Resume from disk failed.
[    0.513418] registered taskstats version 1
[    0.513689]   Magic number: 10:41:222
[    0.513800] rtc_cmos 00:04: setting system clock to 2010-09-12 09:14:50 UTC (1284282890)
[    0.513803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.513806] EDD information not available.
[    0.522092] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.751684] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.753156] Freeing initrd memory: 7782k freed
[    0.892749] isapnp: No Plug & Play device found
[    0.892766] Freeing unused kernel memory: 660k freed
[    0.893606] Write protecting the kernel text: 4680k
[    0.893643] Write protecting the kernel read-only data: 1844k
[    0.915400] udev: starting version 151
[    0.925948] usb 1-4: configuration #1 chosen from 1 choice
[    0.926237] hub 1-4:1.0: USB hub found
[    0.926576] hub 1-4:1.0: 4 ports detected
[    1.136544] scsi0 : pata_atiixp
[    1.142995] scsi1 : pata_atiixp
[    1.144357] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.144361] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.148169]   alloc irq_desc for 21 on node -1
[    1.148174]   alloc kstat_irqs on node -1
[    1.148184] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.200315] usb 1-4.3: new low speed USB device using ehci_hcd and address 3
[    1.208096] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    1.294809] usb 1-4.3: configuration #1 chosen from 1 choice
[    1.312619] ata1.00: ATA-7: FUJITSU MHV2080AT PL, 008300A1, max UDMA/100
[    1.312624] ata1.00: 156301488 sectors, multi 16: LBA 
[    1.328575] ata1.00: configured for UDMA/100
[    1.328717] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0083 PQ: 0 ANSI: 5
[    1.328893] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.329264] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.329312] sd 0:0:0:0: [sda] Write Protect is off
[    1.329315] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.329340] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.329487]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.429317] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.492607] ata2.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HQ04, max MWDMA2
[    1.508561] ata2.00: configured for MWDMA2
[    1.514531] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HQ04 PQ: 0 ANSI: 5
[    1.526357] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.526361] Uniform CD-ROM driver Revision: 3.20
[    1.526477] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.526541] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.533164] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.533203] 8139cp 0000:06:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.546339] 8139too Fast Ethernet driver 0.9.28
[    1.546399]   alloc irq_desc for 22 on node -1
[    1.546402]   alloc kstat_irqs on node -1
[    1.546410] 8139too 0000:06:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.548626] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:c3:b8:2f, IRQ 22
[    1.550726] usbcore: registered new interface driver hiddev
[    1.553489] input: HID 04b3:3107 as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input6
[    1.553610] generic-usb 0003:04B3:3107.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:3107] on usb-0000:00:13.2-4.3/input0
[    1.553641] usbcore: registered new interface driver usbhid
[    1.553644] usbhid: v2.6:USB HID core driver
[    2.118776] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   14.578913] Adding 997368k swap on /dev/sda7.  Priority:-1 extents:1 across:997368k 
[   14.605021] udev: starting version 151
[   14.678078] lp: driver loaded but no devices found
[   14.878776] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   14.894057] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.052400] Linux agpgart interface v0.103
[   15.128898] acpi device:10: registered as cooling_device1
[   15.129071] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:0e/LNXVIDEO:00/input/input7
[   15.129141] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.293849] type=1505 audit(1284279305.278:2):  operation="profile_load" pid=513 name="/sbin/dhclient3"
[   15.294172] type=1505 audit(1284279305.278:3):  operation="profile_load" pid=513 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.294353] type=1505 audit(1284279305.278:4):  operation="profile_load" pid=513 name="/usr/lib/connman/scripts/dhclient-script"
[   15.308565] [drm] Initialized drm 1.1.0 20060810
[   15.519011] [drm] radeon defaulting to kernel modesetting.
[   15.519018] [drm] radeon kernel modesetting enabled.
[   15.519109] radeon 0000:01:05.0: power state changed by ACPI to D0
[   15.519119] radeon 0000:01:05.0: power state changed by ACPI to D0
[   15.519129] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.527172] [drm] radeon: Initializing kernel modesetting.
[   15.528130] [drm] register mmio base: 0xC0100000
[   15.528134] [drm] register mmio size: 65536
[   15.528593] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   15.529468] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   15.529616] [drm] Generation 2 PCI interface, using max accessible memory
[   15.529620] [drm] radeon: VRAM 128M
[   15.529622] [drm] radeon: VRAM from 0x78000000 to 0x7FFFFFFF
[   15.529624] [drm] radeon: GTT 32M
[   15.529627] [drm] radeon: GTT from 0x80000000 to 0x81FFFFFF
[   15.529755] [drm] radeon: irq initialized.
[   15.530187] [drm] Detected VRAM RAM=128M, BAR=128M
[   15.530193] [drm] RAM width 128bits DDR
[   15.539082] [TTM] Zone  kernel: Available graphics memory: 437812 kiB.
[   15.539086] [TTM] Zone highmem: Available graphics memory: 965496 kiB.
[   15.539109] [drm] radeon: 128M of VRAM memory ready
[   15.539112] [drm] radeon: 32M of GTT memory ready.
[   15.539127] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   15.539576] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   15.539595] [drm] radeon: cp idle (0x10000C03)
[   15.539712] [drm] Loading R300 Microcode
[   15.540142] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   15.545464] [drm] radeon: ring at 0x0000000080000000
[   15.545489] [drm] ring test succeeded in 3 usecs
[   15.545623] [drm] radeon: ib pool ready.
[   15.546197] [drm] ib test succeeded in 0 usecs
[   15.546234] [drm] Default TV standard: NTSC
[   15.546236] [drm] 14.318180000 MHz TV ref clk
[   15.546327] [drm] Panel ID String: QDS                     
[   15.546330] [drm] Panel Size 1280x800
[   15.546382] [drm] Default TV standard: NTSC
[   15.546384] [drm] 14.318180000 MHz TV ref clk
[   15.546413] [drm] Radeon Display Connectors
[   15.546415] [drm] Connector 0:
[   15.546417] [drm]   VGA
[   15.546420] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   15.546422] [drm]   Encoders:
[   15.546424] [drm]     CRT1: INTERNAL_DAC2
[   15.546426] [drm] Connector 1:
[   15.546428] [drm]   LVDS
[   15.546431] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   15.546433] [drm]   Encoders:
[   15.546434] [drm]     LCD1: INTERNAL_LVDS
[   15.546436] [drm] Connector 2:
[   15.546438] [drm]   S-video
[   15.546439] [drm]   Encoders:
[   15.546441] [drm]     TV1: INTERNAL_DAC2
[   15.706547] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.782260] [drm] fb mappable at 0xC8040000
[   15.782263] [drm] vram apper at 0xC8000000
[   15.782266] [drm] size 4096000
[   15.782268] [drm] fb depth is 24
[   15.782269] [drm]    pitch is 5120
[   15.783666] fb0: radeondrmfb frame buffer device
[   15.783669] registered panic notifier
[   15.783676] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   15.790567] vga16fb: initializing
[   15.790573] vga16fb: mapped to 0xc00a0000
[   15.790580] vga16fb: not registering due to another framebuffer present
[   15.816572] MC'97 0 converters and GPIO not ready (0x1)
[   15.817788] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.979616] Console: switching to colour frame buffer device 160x50
[   16.101360] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   16.168397] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   16.187116] type=1505 audit(1284279306.170:5):  operation="profile_load" pid=685 name="/usr/share/gdm/guest-session/Xsession"
[   16.203907] type=1505 audit(1284279306.186:6):  operation="profile_replace" pid=690 name="/sbin/dhclient3"
[   16.204340] type=1505 audit(1284279306.190:7):  operation="profile_replace" pid=690 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.204532] type=1505 audit(1284279306.190:8):  operation="profile_replace" pid=690 name="/usr/lib/connman/scripts/dhclient-script"
[   16.251486] type=1505 audit(1284279306.234:9):  operation="profile_load" pid=695 name="/usr/bin/evince"
[   16.256088] type=1505 audit(1284279306.242:10):  operation="profile_load" pid=695 name="/usr/bin/evince-previewer"
[   16.290321] type=1505 audit(1284279306.274:11):  operation="profile_load" pid=695 name="/usr/bin/evince-thumbnailer"
[   16.311369] eth0: link down
[   16.311701] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.869636] ppdev: user-space parallel port driver
[   89.592799] eth0: link down
[   89.593398] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  236.226255] usb 1-4: USB disconnect, address 2
[  236.226265] usb 1-4.3: USB disconnect, address 3
[  236.532084] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  236.666816] usb 1-4: configuration #1 chosen from 1 choice
[  236.667162] hub 1-4:1.0: USB hub found
[  236.667579] hub 1-4:1.0: 4 ports detected
[  236.940420] usb 1-4.2: new high speed USB device using ehci_hcd and address 5
[  237.033152] usb 1-4.2: configuration #1 chosen from 1 choice
[  237.104494] usb 1-4.3: new low speed USB device using ehci_hcd and address 6
[  237.166546] Initializing USB Mass Storage driver...
[  237.166773] scsi2 : SCSI emulation for USB Mass Storage devices
[  237.167114] usbcore: registered new interface driver usb-storage
[  237.167121] USB Mass Storage support registered.
[  237.178846] usb-storage: device found at 5
[  237.178852] usb-storage: waiting for device to settle before scanning
[  237.199217] usb 1-4.3: configuration #1 chosen from 1 choice
[  237.203652] input: HID 04b3:3107 as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input9
[  237.204451] generic-usb 0003:04B3:3107.0002: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:3107] on usb-0000:00:13.2-4.3/input0
[  242.176264] usb-storage: device scan complete
[  242.176865] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Micro     8.02 PQ: 0 ANSI: 0 CCS
[  242.182077] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  242.185334] sd 2:0:0:0: [sdb] 15695871 512-byte logical blocks: (8.03 GB/7.48 GiB)
[  242.185820] sd 2:0:0:0: [sdb] Write Protect is off
[  242.185828] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  242.185834] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  242.196846] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  242.196862]  sdb: sdb1
[  242.200948] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  242.200963] sd 2:0:0:0: [sdb] Attached SCSI removable disk


```
 6) sudo lshw -C network
```

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:c3:b8:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff

```
7) iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```
8) lsb_release -d
```

Description:      Ubuntu 10.04.1 LTS

```

9) uname -mr
```

2.6.32-24-generic i686

```
10) sudo /etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                                                                                                [ OK ] 

  
```

Any ideas why this is happening now?

Cheers!

---

### Post by MaindotC on 2010-09-12
Please see post #2 and work your way back down.

---

### Post by rmforum on 2010-09-12
You think it's the b43 module that is causing this? But I did a "rmmod b43" and I came up with a message that the module could not be found?

---

### Post by MaindotC on 2010-09-12
I'm sorry but I'm a little confused.  According to what you posted, your machine does detect your wireless card.  It's almost the exact same output from post #1.  Then in post #8 you said everything was working.  Is this not the same machine?

---

### Post by rmforum on 2010-09-12
Yes, it's the same machine but I do not see the Wireless device now:

 iwconfig wlan0
```

wlan0     No such device
  
```


 iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

  

 sudo lshw -C network
```

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:c3:b8:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff

  
```

Yesterday I managed to put it to work and eventually shutdowned the system. Today when I turn on the laptop and access Ubuntu, it doesn't seem to "see" the wireless device?

---

### Post by MaindotC on 2010-09-12
If you do an lsmod | grep wl I believe you'll see (or not see) that wl isn't being used.  You can activate it using the command ```
insmod wl.ko
```  I'm not sure if that will keep it inserted after a reboot, but if it doesn't just see if you can find out how.

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> If you do an lsmod | grep wl I believe you'll see (or not see) that wl isn't being used.  You can activate it using the command ```
insmod wl.ko
```  I'm not sure if that will keep it inserted after a reboot, but if it doesn't just see if you can find out how.


I don't see any "wl" reference when I issue the lsmod command as you expected.

When issuing the ```
insmod wl.ko
``` I get:

```

insmod: can't read 'wl.ko': No such file or directory

```

---

### Post by MaindotC on 2010-09-12
This is happening because you are not referring to the full path of wl.ko nor are you in the directory in which wl.ko exists.

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> This is happening because you are not referring to the full path of wl.ko nor are you in the directory in which wl.ko exists.

I did a ```
find . -name wl.ko
``` and the system found nothing?

---

### Post by rmforum on 2010-09-12
Ok, here's what I've done now:

```

1) System > Administration > Hardware Drivers

2) Removed the Broadcom B43 wireless driver

3) Reboot

4) System > Administration > Hardware Drivers

5) Activate the Broadcom B43 wireless driver

```

After I've done this I now have the wireless device and I can access the wireless router and the internet with it.

iwconfig wlan0
```

wlan0     IEEE 802.11bg  ESSID:"SKY61102"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:18:4D:F8:35:D4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c3:b8:2f  
          inet6 addr: fe80::20f:b0ff:fec3:b82f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4759732 (4.7 MB)  TX bytes:191265 (191.2 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:69:55:f9  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe69:55f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1012749 (1.0 MB)  TX bytes:210937 (210.9 KB)

```



lsmod
```

Module                  Size  Used by
arc4                    1153  2 
b43                   163523  0 
mac80211              205146  1 b43
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_usb_audio          75765  2 
vgastate                8961  1 vga16fb
snd_usb_lib            15801  1 snd_usb_audio
snd_hwdep               5412  1 snd_usb_audio
snd_seq_dummy           1338  0 
radeon                674824  3 
ttm                    49943  1 radeon
joydev                  8708  0 
drm_kms_helper         29297  1 radeon
snd_seq_oss            26726  0 
snd_atiixp             12446  2 
snd_seq_midi            4557  0 
drm                   162409  5 radeon,ttm,drm_kms_helper
snd_atiixp_modem        9103  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_ac97_codec        100646  2 snd_atiixp,snd_atiixp_modem
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ati_agp                 5094  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac97_bus                1002  1 snd_ac97_codec
i2c_algo_bit            5028  1 radeon
agpgart                31724  3 ttm,drm,ati_agp
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  5 snd_usb_audio,snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
i2c_piix4               8335  0 
snd_page_alloc          7076  3 snd_atiixp,snd_atiixp_modem,snd_pcm
snd_timer              19098  2 snd_seq,snd_pcm
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  21 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_atiixp,snd_atiixp_modem,snd_rawmidi,snd_ac97_codec,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_seq_device
shpchp                 28820  0 
k8temp                  3024  0 
psmouse                63245  0 
soundcore               6620  1 snd
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
video                  17375  0 
output                  1871  1 video
usbhid                 36110  0 
hid                    67032  1 usbhid
8139too                18545  0 
8139cp                 16186  0 
pata_atiixp             3148  2 
mii                     4381  2 8139too,8139cp
ssb                    38671  1 b43
usb_storage            39425  2 

```


Why did it lost the wlan0 configuration in the first place? Why did it work once I've removed and added again the driver?

---

### Post by MaindotC on 2010-09-12
> **rmforum said:**
> I did a ```
find . -name wl.ko
``` and the system found nothing?

According to the installation instructions that come with the source code for the driver, this file should have been created after following the directions.  You stated that your wireless adapter was working.  Did it work after installing the driver from the broadcom site or did you use the Administration -> Hardware Drivers method?

Also I apologize for not suggesting the Hardware Drivers option in the first place.  I forgot that was there.

---

### Post by MaindotC on 2010-09-12
> **rmforum said:**
> 
Why did it lost the wlan0 configuration in the first place? Why did it work once I've removed and added again the driver?

I'll be in better position to answer this when you clarify how you got it working in your previous success.

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> According to the installation instructions that come with the source code for the driver, this file should have been created after following the directions.  You stated that your wireless adapter was working.  Did it work after installing the driver from the broadcom site or did you use the Administration -> Hardware Drivers method?

Also I apologize for not suggesting the Hardware Drivers option in the first place.  I forgot that was there.


Nothing to forgive strAlan, you've been of great help! 

Let's step back a bit so that I can describe what I did yesterday in order to have my Wireless working:

```


1) As per some previous recommendations I removed the b43 module by issuing the command "rmmod b43" from a terminal session.

2) Then I went to: Applications > Ubuntu Software Centre

3) I did a search for "broadcom"

4) I got several search results but I selected the "Common files for the Broadcom STA wireless driver" (broadcom-sta-common)

5) Selected "Install"

6) This installed the driver but still I could not be able to connect to the router using my wireless device.

7) to overcome this problem I deleted the connection and created a new one.

8) once I did this everything started working (wireless connection to the router and to the internet)

```

This morning, when I started my laptop (I had it shutdown yesterday) the wireless device was no longer available on Ubuntu but was working fine on windows.

What I did in order to have it back on was:
```

1) System > Administration > Hardware drivers

2) Removed the Broadcom B43 wireless driver

3) Reboot

4) System > Administration > Hardware Drivers

5) Activate the Broadcom B43 wireless driver

```

I now have the wireless device available, enabled and working on Ubuntu. I'm just not sure why Ubuntu lost it when I shutdown the laptop.

---

### Post by MaindotC on 2010-09-12
I'm not sure either because I'd have to compare a bunch of files and require loads of more posts.  I used to have a Belkin F5D7050 that used the same chipset and I had to use that "Hardware Drivers" option.  It was a long time ago but to my knowledge it should stay there now.  Do a reboot and verify?

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> I'm not sure either because I'd have to compare a bunch of files and require loads of more posts.  I used to have a Belkin F5D7050 that used the same chipset and I had to use that "Hardware Drivers" option.  It was a long time ago but to my knowledge it should stay there now.  Do a reboot and verify?

I've just rebooted and I had exactly the same problem. The wireless device was not present so I had to remove the driver and activate it again in order to work. What a weird thing...

---

### Post by MaindotC on 2010-09-12
Look in /etc/modprobe.d/blacklist.conf and see if b43 is blacklisted.  If it is, then I would assume Ubuntu is removing that driver from being inserted into the kernel every time you boot.

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> Look in /etc/modprobe.d/blacklist.conf and see if b43 is blacklisted.  If it is, then I would assume Ubuntu is removing that driver from being inserted into the kernel every time you boot.

The only reference to b43 that I have found there was:

```

# replaced by b43 and ssb.
blacklist bcm43xx

```

I've removed the entry:
```

# replaced by b43 and ssb.
#blacklist bcm43xx

```


And afterwards I rebooted. The problem persists. Ubuntu does not see the wireless device so I had to remove the driver and activate it again.

---

### Post by MaindotC on 2010-09-12
Please leave the bcm43xx blacklisted.

After you install the b43 driver doesn't it require you to reboot in order for the driver to take effect?  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> Please leave the bcm43xx blacklisted.

After you install the b43 driver doesn't it require you to reboot in order for the driver to take effect?  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


I have left bcm43xx blacklisted as you recommended.

No. After removing and activating the driver the system picks up the wireless device, enables it and connects it using the default configuration access.

---

### Post by MaindotC on 2010-09-12
Well I'm using terms such as "ubuntu reboot removes wireless driver" and I'm not getting anything.  You may want to mark this as solved and start a new thread for this issue (i usually don't look at/reply to a thread that has more than 2 posts because I assume they're already being helped).  I suggest about noon EST because I seem to be the only one in the N&W forum right now.  Also check out #ubuntu, #ubuntu-forums, and #ubunter-beginners in IRC.

Oh chili555 is awake - maybe you can go ahead and post that new thread now.

---

### Post by rmforum on 2010-09-12
> **strAlan said:**
> Well I'm using terms such as "ubuntu reboot removes wireless driver" and I'm not getting anything.  You may want to mark this as solved and start a new thread for this issue (i usually don't look at/reply to a thread that has more than 2 posts because I assume they're already being helped).  I suggest about noon EST because I seem to be the only one in the N&W forum right now.  Also check out #ubuntu, #ubuntu-forums, and #ubunter-beginners in IRC.

Oh chili555 is awake - maybe you can go ahead and post that new thread now.


Will do, thanks strAlan!

---

