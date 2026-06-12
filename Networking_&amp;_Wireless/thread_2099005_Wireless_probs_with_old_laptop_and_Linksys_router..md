---
title: "Wireless probs with old laptop and Linksys router..."
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by sabermilena on 2012-12-28
Hi all,

I've acquired an old(ish) Toshiba Portege laptop and installed Xubuntu 12.04 (that's about all it'll handle).

A wired connection to my Linksys E2000 Wireless Router (yeah, I know ](*,)) works just fine, but no matter what I try it won't connect wirelessly.

I'm technically an "enthusiastic noob", pleeease take that into account?

Either that or it's off to replace the Linksys with something that's X/Ubuntu friendly?

Anyone any ideas?

Saber x  (UK based , ISP = Virgin Media (cable))

---

### Post by Pjotr123 on 2012-12-28
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by praseodym on 2012-12-28
Please show your hardware and other infos via terminal outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by sabermilena on 2013-01-05
> **praseodym said:**
> Please show your hardware and other infos via terminal outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```


Thank you praseodym - sorry about the delay... never known a new year hangover to last THAT long!   :(

Info follows...


saber@wintermute:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 0d)
    Subsystem: Toshiba America Info Systems 8255x-based Ethernet Adapter (10/100) [1179:0001]
    Kernel driver in use: e100
    Kernel modules: e100


saber@wintermute:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 15d9:0a4f Trust International B.V. 
Bus 001 Device 003: ID 0930:0502 Toshiba Corp. Integrated Bluetooth


saber@wintermute:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  1 
michael_mic            12540  4 
snd_atiixp_modem       18604  0 
snd_via82xx_modem      18377  0 
snd_intel8x0m          18498  0 
orinoco_cs             12898  1 
orinoco                70112  1 orinoco_cs
cfg80211              178877  1 orinoco
btusb                  17948  1 
snd_ali5451            23459  3 
snd_ac97_codec        110213  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  1 orinoco_cs
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96718  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62218  16 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali15x3            12878  0 
i2c_ali1535            12777  0 
soundcore              14635  1 snd
smsc_ircc2             28358  0 
irda                  185517  1 smsc_ircc2
snd_page_alloc         14115  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
crc_ccitt              12627  1 irda
shpchp                 32325  0 
bnep                   17830  2 
parport_pc             32114  1 
rfcomm                 38139  4 
bluetooth             158479  13 btusb,rfcomm,bnep
ppdev                  12849  0 
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
toshiba_bluetooth      12711  0 
wmi                    18744  1 toshiba_acpi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
firewire_ohci          40180  0 
usbhid                 41937  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_ali               13562  2 
e100                   36289  0 
ali_agp                12957  1 
hid                    77428  1 usbhid
video                  19068  0 


saber@wintermute:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Cisco39879"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:53
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

eth0      no wireless extensions.


saber@wintermute:~$ rfkill list
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


saber@wintermute:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: C0:C1:C0:20:FA:D7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"Cisco39879"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000042afd6ce0
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 000A436973636F3339383739
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001011041000100103B000103104700104B3D6652EFC3C44A1572F70CC7C7BAA71021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 02 - Address: 32:D1:5E:C0:9A:92
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f0f6693c2
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 32:D1:5E:C0:9A:93
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f0f66a258
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 06:21:04:C6:D2:D2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001313af3aa56
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0107
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101B0000000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: C8:D1:5E:C0:9A:91
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-ZMR7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f0f668aae
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 000B4254487562332D5A4D5237
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

saber@wintermute:~$

---

### Post by praseodym on 2013-01-06
It looks like a pcmcia card (module orinoco is loaded): Please show also:
```

pccardctl info
dmesg | egrep 'ori|eth1'
```

---

### Post by Us3r Unfriendly on 2013-01-06
What wireless card do you have?

Looks like there isn't a driver loaded for any card with your lsmod output.

Though I know this is a driver issue, but in some cases if your router has something like Mac filtering on, then you'll have to enable that WiFi card's Mac IP into your router's configuration.  But then again, I don't believe that your router is the culprit :D

---

### Post by sabermilena on 2013-01-14
> **praseodym said:**
> It looks like a pcmcia card (module orinoco is loaded): Please show also:
```

pccardctl info
dmesg | egrep 'ori|eth1'
```



Sorry about the delay (again) praseodym, PSU blew up.  The laptop was essentially free - and I'm beginning to suspect why.

Requested info follows...

saber@wintermute:~$ pccardctl info
PRODID_1="TOSHIBA
"
PRODID_2="Wireless LAN Card
"
PRODID_3="Version 01.01
"
PRODID_4=""
MANFID=0156,0002
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


saber@wintermute:~$ dmesg | egrep 'ori|eth1'
[76501.137953] eth1: Lucent/Agere firmware doesn't support manual roaming
[76506.395520] eth1: Lucent/Agere firmware doesn't support manual roaming
[76511.597614] eth1: Lucent/Agere firmware doesn't support manual roaming
[76516.792451] eth1: Lucent/Agere firmware doesn't support manual roaming
[76522.300365] eth1: Lucent/Agere firmware doesn't support manual roaming
[76527.526351] eth1: Lucent/Agere firmware doesn't support manual roaming
[76532.750183] eth1: Lucent/Agere firmware doesn't support manual roaming
[76537.974975] eth1: Lucent/Agere firmware doesn't support manual roaming
[76543.248959] eth1: Lucent/Agere firmware doesn't support manual roaming
[76548.491266] eth1: Lucent/Agere firmware doesn't support manual roaming
[76553.696575] eth1: Lucent/Agere firmware doesn't support manual roaming
[76558.881187] eth1: Lucent/Agere firmware doesn't support manual roaming
[76564.168356] eth1: Lucent/Agere firmware doesn't support manual roaming
[76569.359183] eth1: Lucent/Agere firmware doesn't support manual roaming
[76574.604513] eth1: Lucent/Agere firmware doesn't support manual roaming

.
.
.
(1500 lines of this, I don't imagine you need to see it all?)
.
.
.

[95742.472331] eth1: Lucent/Agere firmware doesn't support manual roaming
[95747.684410] eth1: Lucent/Agere firmware doesn't support manual roaming
[95752.865107] eth1: Lucent/Agere firmware doesn't support manual roaming
[95758.106144] eth1: Lucent/Agere firmware doesn't support manual roaming
[95763.317009] eth1: Lucent/Agere firmware doesn't support manual roaming
[95768.592381] eth1: Lucent/Agere firmware doesn't support manual roaming
[95773.784614] eth1: Lucent/Agere firmware doesn't support manual roaming
[95778.992599] eth1: Lucent/Agere firmware doesn't support manual roaming
[95784.211263] eth1: Lucent/Agere firmware doesn't support manual roaming
[95789.430710] eth1: Lucent/Agere firmware doesn't support manual roaming
[95794.616740] eth1: Lucent/Agere firmware doesn't support manual roaming
[95979.876694] ADDRCONF(NETDEV_UP): eth1: link is not ready
[95986.708457] ADDRCONF(NETDEV_UP): eth1: link is not ready
[95991.894799] ADDRCONF(NETDEV_UP): eth1: link is not ready
[96002.908750] ADDRCONF(NETDEV_UP): eth1: link is not ready
[96010.880415] ADDRCONF(NETDEV_UP): eth1: link is not ready
[96014.864701] ADDRCONF(NETDEV_UP): eth1: link is not ready
saber@wintermute:~$ 


Thanks again praseodym

Saber  :)

---

### Post by praseodym on 2013-01-14
Try "the other" module for this kind of cards:
```

sudo modprobe -rfv orinoco_cs
sudo modprobe -v hostap_cs
dmesg | grep hostap
iwconfig
```

---

### Post by sabermilena on 2013-01-15
> **praseodym said:**
> Try "the other" module for this kind of cards:
```

sudo modprobe -rfv orinoco_cs
sudo modprobe -v hostap_cs
dmesg | grep hostap
iwconfig
```

Had a few problems with this praseodym.

sudo modprobe -rfv orinoco_cs

returned: 'FATAL: Module orinoco_cs is in use'

I tried blacklisting orinoco by adding 'blacklist orinoco_cs' to 
/etc/modprobe.d/blacklist.conf

Rebooted

saber@wintermute:/sbin$ sudo modprobe -rfv orinoco_cs

saber@wintermute:/sbin$ sudo modprobe -v hostap_cs
insmod /lib/modules/3.2.0-35-generic/kernel/net/wireless/lib80211.ko 
insmod /lib/modules/3.2.0-35-generic/kernel/drivers/pcmcia/pcmcia.ko 
insmod /lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/hostap/hostap.ko 
insmod /lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko 

saber@wintermute:/sbin$ dmesg | grep hostap

saber@wintermute:/sbin$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

saber@wintermute:/sbin$


wireless networking is not for the faint-hearted is it?   :)

Saber

---

### Post by praseodym on 2013-01-15
Try both drivers with WEP encryption only. Maybe these drivers only work with that.

---

### Post by sabermilena on 2013-01-21
Bad news praseodym, the Toshiba has now given up completely.

I decided to reinstall Xubuntu, but the laptop won't even read from the CD drive any more - and it's never been able to boot from the USB port.

I've got another slightly less ancient Toshiba on the way - another freebie - which I'm going to try the stuff you've shown me so far to see if it'll connect, but for now delving into Xubuntu wireless networking is on hold.

Thanks for your help praseodym  :)

Saber x

---

### Post by praseodym on 2013-01-21
For any further problems, see #3 ;-)

---

### Post by sabermilena on 2013-01-22
> **praseodym said:**
> Try both drivers with WEP encryption only. Maybe these drivers only work with that.

Bad news praseodym, the Toshiba has now given up completely.

I decided to reinstall Xubuntu, but the laptop won't even read from the  CD drive any more - and it's never been able to boot from the USB port.

I've got another slightly less ancient Toshiba on the way - another  freebie - which I'm going to try the stuff you've shown me so far to see  if it'll connect, but for now delving into Xubuntu wireless networking  is on hold.

Thanks for your help praseodym  :smile:

Saber x
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12466947") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12466947") 		 		 		 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12466947") 		 		 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12466947") 		 		 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12466947")

---

