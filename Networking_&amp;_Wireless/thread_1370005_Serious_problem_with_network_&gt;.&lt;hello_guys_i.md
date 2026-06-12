---
title: "Serious problem with network &gt;.&lt;hello guys im new here in using dis great operating s"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by zonefull on 2010-01-01
hello guys im new here in using dis great operating system i dled ubuntu  9.10 and i got it ready on ma pc but after the setup process is done i  couldnot get it attached to my LAN or internet connection i use a DHCP  router wich need no configuration as it was shown problem is even my  acctivity lamp on da router doesnot give any activity light not even a  blink wish u guys can help me out thx for reading 



oh btw i got some records as 

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:e6:3c:76:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
 
 
 
 
 
iwconfig
 
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
 
 
 
 
 
 
lspci
 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM  Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated  Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to  I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB  UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB  UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB  UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB  UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2  EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC  Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller  (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus  Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER  (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R)  integrated LAN Controller (rev 02)
 
 
 
 
 
lsusb
 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0810:0002 Personal Communication Systems, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:5611 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
 
lsmod
 
 
 
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
shpchp                 32272  0 
parport                35340  3 ppdev,parport_pc,lp
snd_intel8x0           30168  2 
psmouse                56180  0 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
serio_raw               5280  0 
joydev                 10272  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
snd                    59204  14  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_   oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti  mer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
hid_pl                  3324  0 
ff_memless              5188  1 hid_pl
usbhid                 38208  1 hid_pl
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
e100                   32452  0 
mii                     5212  1 e100
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video



wish some1 can help me out thx an cya

---

### Post by dmizer on 2010-01-01
Please do not create duplicate threads for the same problem. Thread closed.

Thank you.

---

