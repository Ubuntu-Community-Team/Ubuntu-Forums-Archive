---
title: "r8168 unusable wired network, how do I remove and reinstall needed modules?"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by Frogster on 2012-03-10
Good afternoon all, 

I have a Realtek RTL8111/8168b PCI Express Gigabyte ethernet controller (rev2). It connects, however, nothing will load in any browser or feed reader! 

Managed to load the r8168 driver but I only get occasional connection and even then its very slow.

Any help wil be gratefully accepted, if you need further info please ask.



```
:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:1d:59:fb:3d  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::224:1dff:fe59:fb3d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:905 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2050 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:607735 (607.7 KB)  TX bytes:331912 (331.9 KB) 
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4012 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4012 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1451150 (1.4 MB)  TX bytes:1451150 (1.4 MB) 

$ lsmod 
Module                  Size  Used by 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  8 
binfmt_misc            17292  1 
gspca_zc3xx            51066  0 
gspca_main             27610  1 gspca_zc3xx 
videodev               85626  1 gspca_main 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
snd_cmipci             35513  2 
gameport               15060  1 snd_cmipci 
snd_opl3_lib           18863  1 snd_cmipci 
snd_mpu401_uart        13865  1 snd_cmipci 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13276  2 snd_opl3_lib,snd_hda_codec 
snd_pcm                80435  3 snd_cmipci,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
arc4                   12473  2 
nvidia              10390874  40 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi 
rt61pci                27493  0 
crc_itu_t              12627  1 rt61pci 
rt2x00pci              14202  1 rt61pci 
rt2x00lib              48146  2 rt61pci,rt2x00pci 
mac80211              393421  2 rt2x00pci,rt2x00lib 
psmouse                63474  0 
serio_raw              12990  0 
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi 
bluetooth             148839  23 bnep,rfcomm,btusb 
cfg80211              172427  2 rt2x00lib,mac80211 
eeprom_93cx6           12653  1 rt61pci 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28932  3 snd_opl3_lib,snd_pcm,snd_seq 
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    55902  20 snd_hda_codec_realtek,snd_cmipci,snd_opl3_lib,snd_mpu401_uart,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              12600  1 snd 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp 
usb_storage            44173  0 
uas                    17699  0 
floppy                 60310  0 
r8168                 202075  0 
```

---

### Post by Frogster on 2012-03-12
Realtek (RTL8111/RTL8168) ethernet card

followed this to replace the module [http://forums.linuxmint.com/viewtopic.php?f=49&t=80757](http://forums.linuxmint.com/viewtopic.php?f=49&t=80757).

However, I still have totally useless ethernet. Can anybody help???

> keith@Ernie:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8168
--
04:00.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Linksys WMP54G ver 4.1 [1737:0055]
	Kernel driver in use: rt61pci

keith@Ernie:~$ ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
Cannot get link status: Operation not permitted
keith@Ernie:~$ 


---

### Post by Frogster on 2012-03-13
Bump

---

### Post by flash63 on 2012-03-13
Hello,
installation instructions for the latest driver V 8.028.00 here (German uu-forum)

[http://forum.ubuntuusers.de/post/3005217/](http://forum.ubuntuusers.de/post/3005217/)

follow the section &#8222;*r8168 mittels dkms*&#8220; 

Translation:
[http://translate.google.de/translate?sl=auto&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F3005217%2F&act=url](http://translate.google.de/translate?sl=auto&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F3005217%2F&act=url)

---

### Post by Frogster on 2012-03-13
Thank you flash63

---

### Post by flash63 on 2012-03-13
The solution works?

By the way, support for Ubuntu 10.10 ends in April 2012!

---

