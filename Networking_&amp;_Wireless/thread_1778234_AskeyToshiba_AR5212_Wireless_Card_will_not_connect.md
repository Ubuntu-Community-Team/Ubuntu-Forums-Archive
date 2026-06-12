---
title: "Askey/Toshiba AR5212 Wireless Card will not connect"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by wilburburns on 2011-06-08
Toshiba Satellite 1905-S303 

Ubuntu 11.04

2.6.38-8-generic i686 Kernel

The Network card sees the Wireless network, but will not connect to the router.  I have tried with and without security, and neither setting makes any difference.  Using the Wired Network adapter does work when set to a STATIC IP.  



Any idea what could be the problem?  

Cliff

---

### Post by wilburburns on 2011-06-08
```
cliff@ubuntu:~$ lspci -k
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
	Kernel modules: shpchp
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
	Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: ata_piix
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: uhci_hcd
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel modules: i2c-i801
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: uhci_hcd
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel modules: snd-intel8x0m
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
	Subsystem: Toshiba America Info Systems PRO/100 VE Network Connection
	Kernel driver in use: e100
	Kernel modules: e100
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
02:0b.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: Lucent Technologies Device ab01
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
cliff@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"PEWEBHOST.COM"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:30
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

cliff@ubuntu:~$ sudo lshw -C network
[sudo] password for cliff: 
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:7b:a5:dc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.7 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:e8104000-e8104fff ioport:4000(size=64)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: eth1
       serial: 00:02:2d:56:27:14
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
```

Cliff

---

### Post by josephmills on 2011-06-09
could we please see a ```
rfkill list all 
``` and a ```
lsmod
``` and a ```
lspci -k -nn 
``` thanks

---

### Post by wilburburns on 2011-06-09
Sure Can, Here you go.  
```

cliff@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
cliff@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
radeon                896428  2 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
joydev                 17322  0 
ttm                    65184  1 radeon
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 radeon
pcmcia                 39671  1 orinoco_cs
drm                   180037  4 radeon,ttm,drm_kms_helper
soundcore              12600  1 snd
irda                  185091  0 
psmouse                73312  0 
yenta_socket           27230  0 
parport_pc             32111  1 
pcmcia_rsrc            18292  1 yenta_socket
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
crc_ccitt              12595  1 irda
serio_raw              12990  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 radeon
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
floppy                 60032  0 
crc_itu_t              12627  1 firewire_core
cliff@ubuntu:~$ lspci -k -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
	Kernel modules: shpchp
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 05)
	Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 05)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: ata_piix
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: uhci_hcd
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel modules: i2c-i801
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: uhci_hcd
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
00:1f.6 Modem [0703]: Intel Corporation 82801BA/BAM AC'97 Modem Controller [8086:2446] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel modules: snd-intel8x0m
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
02:00.0 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:00.1 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
	Subsystem: Toshiba America Info Systems PRO/100 VE Network Connection [1179:ff01]
	Kernel driver in use: e100
	Kernel modules: e100
02:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
02:0b.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
	Subsystem: Lucent Technologies Device [12a3:ab01]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
cliff@ubuntu:~$ 

```

Thanks for the help,
Cliff

---

### Post by wilburburns on 2011-06-12
Surely someone has an idea why I can see the networks but just can't connect.  

Cliff

---

