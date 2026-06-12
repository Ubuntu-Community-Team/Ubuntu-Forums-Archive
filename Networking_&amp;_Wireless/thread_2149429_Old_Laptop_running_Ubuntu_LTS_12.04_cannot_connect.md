---
title: "Old Laptop running Ubuntu LTS 12.04 cannot connect to internet"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by mwg on 2013-05-28
To make a long story short, I have tried everything to make the wireless internet work, short of plugging into ethernet (dorm, so not an option).
The ifconfig is:
   Linkencap:Ethernet  HWaddr00:08:74:95:65:00  
          UP BROADCASTMULTICAST  MTU:1500  Metric:1
          RX packets:0errors:0 dropped:0 overruns:0 frame:0
          TX packets:0errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RX bytes:0(0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11Base address:0xc00
 
eth1      Linkencap:Ethernet  HWaddr00:02:2d:70:54:59  
          UP BROADCASTMULTICAST  MTU:1500  Metric:1
          RX packets:0errors:0 dropped:0 overruns:0 frame:0
          TX packets:0errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RX bytes:0(0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5Base address:0xe100
 
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:16436  Metric:1
          RXpackets:112 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:0
          RX bytes:9056(9.0 KB)  TX bytes:9056 (9.0 KB)
 
and the iwconfig is:
 lo        no wirelessextensions.

 
eth0      no wirelessextensions.
 
eth1      IEEE802.11b  ESSID:"wildfell"  
         Mode:Managed  Frequency:2.457GHz  Access Point: None   
          Bit Rate:11Mb/s   Sensitivity:1/0  
          Retrylimit:8   RTS thr=2347 B   Fragment thr:off
          PowerManagement:off
          LinkQuality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessiveretries:0  Invalid misc:0   Missed beacon:0





Any help would be greatly appreciated!

---

### Post by praseodym on 2013-05-28
Obviously, you are using the Broadcom-STA driver (interface name eth1). Please check these outputs:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by mwg on 2013-05-28
> **praseodym said:**
> Obviously, you are using the Broadcom-STA driver (interface name eth1). Please check these outputs:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
**Uname -a**
Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux
 
**lspci -nnk | grep -iA2 net **
02:00.0 Ethernet controller [0200]: 3Com Corporation3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
            Subsystem:Dell 3C920 Integrated Fast Ethernet Controller [Latitude C640] [1028:012a]
            Kerneldriver in use: 3c59x
            Kernelmodules: 3c59x
 
 
**lsusb**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
 
 
**lsmod**
Module                 Size  Used by
nls_iso8859_1         12618  0
michael_mic           12541  4
orinoco_cs            12899  1
orinoco               70176  1 orinoco_cs
cfg80211             181041  1 orinoco
joydev                17394  0
snd_intel8x0          33463  2
snd_ac97_codec       106118  1 snd_intel8x0
ac97_bus              12671  1 snd_ac97_codec
snd_pcm               81124  2snd_intel8x0,snd_ac97_codec
dell_laptop           17210  0
snd_seq_midi          13133  0
dcdbas                14099  1 dell_laptop
snd_rawmidi           25426  1 snd_seq_midi
snd_seq_midi_event    14476  1 snd_seq_midi
microcode             18396  0
snd_seq               51594  2snd_seq_midi,snd_seq_midi_event
pcmcia                39855  1 orinoco_cs
snd_timer             28932  2 snd_pcm,snd_seq
snd_seq_device        14138  3snd_seq_midi,snd_rawmidi,snd_seq
psmouse               91022  0
radeon               832167  2
snd                   62675  11snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13032 0
soundcore             14636  1 snd
yenta_socket          27465  0
snd_page_alloc        14109  2 snd_intel8x0,snd_pcm
pcmcia_rsrc           18368  1 yenta_socket
ttm                   76326  1 radeon
lpc_ich               16993  0
drm_kms_helper        47459  1 radeon
pcmcia_core           21512  4orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
drm                  240232  4radeon,ttm,drm_kms_helper
video                 19070  0
mac_hid               13078  0
i2c_algo_bit          13317  1 radeon
rfcomm                38104  0
bnep                  17791  2
bluetooth            189585  10 rfcomm,bnep
parport_pc            32115  1
ppdev                 12850  0
shpchp                32326  0
lp                     17456  0
parport               40931  3 parport_pc,ppdev,lp
usb_storage           39720  0
3c59x                 37446  0
floppy                60214  0
 
 
**iwconfig**
lo        no wirelessextensions.
 
eth0      no wirelessextensions.
 
eth1      IEEE802.11b  ESSID:"wildfell"  
         Mode:Managed  Frequency:2.457GHz  Access Point: None   
          Bit Rate:11Mb/s   Sensitivity:1/0  
          Retrylimit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          LinkQuality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessiveretries:0  Invalid misc:0   Missed beacon:0
 
**rfkill list**
0: phy0: Wireless LAN
            Softblocked: no
            Hardblocked: no

---

### Post by praseodym on 2013-05-29
Ok, obviously a PCMCIA card, check
```

pccardctl info
```

---

