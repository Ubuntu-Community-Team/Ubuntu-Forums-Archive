---
title: "Wireless not connecting to AP"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by kripz on 2009-07-12
I'm not sure why its not working, there doesn't seem to be anything incorrect but then again im no expert. The only thing i noticed is that my wireless appears as eth1, though its probably just a name.

I've got an Asus F5R Laptop running Xubuntu 9.04.

> :-$lspci
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


> :~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:e3:fd:1b  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fee3:fd1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:293 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:261015 (261.0 KB)  TX bytes:74891 (74.8 KB)
          Memory:feac0000-feb00000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:b3:a6:5f  
          inet6 addr: fe80::21a:92ff:feb3:a65f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1540 (1.5 KB)  TX bytes:1540 (1.5 KB)



> :~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

pan0      no wireless extensions.


> :~$ lsmod
Module                  Size  Used by
cbc                    11648  103 
aes_i586               15744  104 
aes_generic            35880  1 aes_i586
ecb                    10752  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
i2c_piix4              18448  0 
asus_laptop            24440  0 
video                  25360  0 
soundcore              15200  2 snd
shpchp                 40212  0 
atl2                   34328  0 
serio_raw              13316  0 
btusb                  19608  2 
pcspkr                 10496  0 
output                 11008  1 video
led_class              12036  1 asus_laptop
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
ieee80211_crypt_tkip    16896  0 
wl                   1281236  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
usb_storage            99520  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


> :~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:b3:a6:5f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1a:92:e3:fd:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.147 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:b4:32:3c:cd:21
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


> :~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


> :~$ dmesg | grep -e Broad
[   11.923309] eth0: Broadcom BCM4311 802.11 Wireless Controller 5.10.91.9

> :~$ lsb_release -d
Description:	Ubuntu 9.04

> :~$ uname -mr
2.6.28-13-generic i686

---

### Post by superprash2003 on 2009-07-12
do add a sudo to the iwlist scan command and post output again.. **sudo iwlist scanning**

---

### Post by kripz on 2009-08-31
> **superprash2003 said:**
> do add a sudo to the iwlist scan command and post output again.. **sudo iwlist scanning**

It says the same thing as iwlist scan.

> lo Interface doesn't support scanning.

eth1 Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

pan0 Interface doesn't support scanning.

---

### Post by kripz on 2009-09-01
Got rid of NM and installed WCID. Everything is working fine.

---

