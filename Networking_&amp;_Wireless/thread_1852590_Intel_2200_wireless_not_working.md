---
title: "Intel 2200 wireless not working"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by alaskandsm on 2011-09-30
Hey guys. I have a problem that I am not sure how to correct. I am still fairly new to the linux system but have done some research to my issue and with my limited knowledge of Linux systems, I am at a loss for what to do. I have a Dell Latitude D610 laptop with the Intel Pro/Wireless 2200BG wireless card. I have installed Ubuntu 11.04 onto the laptop.
 
The problem I seem to be running into the the fact that I cannot enable the wireless. When typing the command:
 
rfkill list all
 
I receive the response:
 
soft blocked: no
hard blocked: yes
 
This leads me to know that there is a hardware switch of some type that is keeping the wireless from working. My problem is that the only switch I can find is Fn+F2. But this does not work. 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:12:3f:02:f7:d7  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe02:f7d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1146837 (1.1 MB)  TX bytes:218507 (218.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod:
Module                  Size  Used by
snd_intel8x0           33213  2 
radeon                900494  3 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
ipw2200               145664  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
libipw                 46641  1 ipw2200
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 radeon
cfg80211              156212  2 ipw2200,libipw
ppdev                  12849  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32111  1 
dcdbas                 14054  0 
soundcore              12600  1 snd
lib80211               14570  2 ipw2200,libipw
serio_raw              12990  0 
video                  18951  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
tg3                   131476  0 


sudo lshw -c network:

 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:02:f7:d7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5751-v3.29a ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:57:05:75
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfbff000-dfbfffff

 
I am lost and I really don't know what to do next. Any help would greatly be appreciated. Thank you.

---

