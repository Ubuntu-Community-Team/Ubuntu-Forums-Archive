---
title: "Internet slower on Ubuntu 10.10"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by saggz on 2011-01-18
Hello all,

     This is my first time posting here but I believe it to be the best place to ask my question and hope that someone can share their knowledge and help me find an answer. I have EastLink cable Internet and I have the fastest residential service money can buy, I get speed test results of 30mbps down and 2mbps up, that being said, my Internet was lightning fast on windows and Mac but when I installed Ubuntu, which is my favourite OS, my Internet is very slow and laggy. Sometimes it could take several minutes for a web page to load and some torrents download at 1-2 MBps and some download at under 100kb/sec, some web pages load instantly, some take longer.

     I've searched other forums and one suggestion I found was turning off IPv6, I am not really sure what that is but I followed the steps provided and shut it off but did not notice much of a difference. I am basically a beginner when it comes to Linux, I use the OS for my day to day school and entertainment. I listen to music, watch movies, do school work and such since I am a university student. I really love Ubuntu and don't want to be forced to go back to Win blows, I really don't like windows at all so I would really like to solve this issue and stick with this operating system.

Any help is greatly appreciated,

Thank you in advance,

Sincerely,

Brian

---

### Post by MooPi on 2011-01-18
If you could give us some info. Do you connect wired or wirelessly ? From terminal can you give us the results to ```
lsmod
```
```
lspci
```
and if you connect with wireless give us ```
iwconfig
```

---

### Post by saggz on 2011-01-18
Hello and thank you for replying, I don't use wireless, I am connected right into the router.

LSMOD:

Module                  Size  Used by
snd_seq_dummy           1350  0 
binfmt_misc             6599  1 
vboxnetadp              6614  0 
vboxnetflt             18657  0 
vboxdrv               214831  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218227  1 
nvidia               7088432  27 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
gspca_m5602            52354  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
gspca_main             23644  1 gspca_m5602
snd_seq                47174  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
videodev               43098  1 gspca_main
snd_seq_device          5744  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            13359  1 videodev
arc4                    1165  2 
joydev                  8767  0 
pcmcia                 35973  0 
ath5k                 130083  0 
mac80211              231541  1 ath5k
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     8153  1 ath5k
cfg80211              144470  3 ath5k,mac80211,ath
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
tifm_7xx1               3766  0 
video                  18712  0 
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
tifm_core               6089  1 tifm_7xx1
output                  1883  1 video
psmouse                59033  0 
k8temp                  3228  0 
acer_wmi               13929  0 
i2c_nforce2             5179  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
led_class               2633  2 ath5k,acer_wmi
agpgart                32011  1 nvidia
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sata_nv                19420  2 
pata_amd                8746  0 
forcedeth              49433  0 


LSPCI:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by mips on 2011-01-19
Post the output of the following commands here:
ifconfig -a
ip addr show
ip route show
netstat -nr
cat /etc/hosts
cat /etc/resolv.conf
sudo ethtool eth0 (Change eth0 to eth1 or whatever your lan port number is, you will have to install ethtool if not installed already with *sudo apt-get install ethtool* if not installed already)


What make & model cable router/modem are you using?
Which of these services are you using [http://www.eastlink.ca/internet/index.asp](http://www.eastlink.ca/internet/index.asp) ?
Using a wired or wireless connection?

---

### Post by saggz on 2011-01-20
Thank you very much for replying! Here is the information you requested:

  	 	 	 	p { margin-bottom: 0.21cm; }  **Ifconfig -a**
 

 eth0      Link encap:Ethernet  HWaddr 00:16:d3:51:22:ee   
           inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:3664458 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:3321999 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:3239829922 (3.2 GB)  TX bytes:1128217239 (1.1 GB) 
           Interrupt:21  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:60285 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:60285 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:12676937 (12.6 MB)  TX bytes:12676937 (12.6 MB) 
  
 vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00   
           BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:19:7d:68:23:68   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 

 **ip addr show**
 

 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN  
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 
     inet 127.0.0.1/8 scope host lo 
 2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000 
     link/ether 00:16:d3:51:22:ee brd ff:ff:ff:ff:ff:ff 
     inet 192.168.1.102/24 brd 192.168.1.255 scope global eth0 
 3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000 
     link/ether 00:19:7d:68:23:68 brd ff:ff:ff:ff:ff:ff 
 4: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000 
     link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff 
 

 

 **ip route show**
 

 192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.102  metric 1  
 169.254.0.0/16 dev eth0  scope link  metric 1000  
 default via 192.168.1.1 dev eth0  proto static  
 

 **netstat -nr**
 

 Kernel IP routing table 
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
 192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0 
 169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0 
 0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0 
 

 

 **cat /etc/hosts**
 

 192.168.1.102	UBUNTU	# Added by NetworkManager 
 127.0.0.1	localhost.localdomain	localhost 
 ::1	UBUNTU	localhost6.localdomain6	localhost6 
 127.0.1.1	UBUNTU 
  
 # The following lines are desirable for IPv6 capable hosts 
 ::1     localhost ip6-localhost ip6-loopback 
 fe00::0 ip6-localnet 
 ff00::0 ip6-mcastprefix 
 ff02::1 ip6-allnodes 
 ff02::2 ip6-allrouters 
 ff02::3 ip6-allhosts 
 

 

 **cat /etc/resolv.conf**
 

 # Generated by NetworkManager 
 domain eastlink.ca 
 search eastlink.ca 
 nameserver 192.168.1.1
 

 **sudo ethtool eth0**
 

 Settings for eth0: 
 	Supported ports: [ MII ] 
 	Supported link modes:   10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Supports auto-negotiation: Yes 
 	Advertised link modes:  10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Advertised pause frame use: No 
 	Advertised auto-negotiation: Yes 
 	Speed: 1000Mb/s 
 	Duplex: Full 
 	Port: MII 
 	PHYAD: 1 
 	Transceiver: external 
 	Auto-negotiation: on 
 	Supports Wake-on: g 
 	Wake-on: d 
 	Link detected: yes 
 



[B]Make & Model of cable modem - Arris WBM760A
[/B]
**Make & Model of router - Dlink DIR - 655 Firmware - 1.35NA Hardware version - A3**
**I am connected right into the router via a Ethernet cable, two others use the Internet via wireless I am the only wired connection, although that hasn't affected it before, with windows installed I was getting 1-2mb/sec downloads and instant web page loads, not with Ubuntu though.**


Here is my service from EastLink - Eastlink 30


[http://www.eastlink.ca/internet/docsis3-30/index.asp](http://www.eastlink.ca/internet/docsis3-30/index.asp)


Thank you in advance for your time and help, hope I can solve this!

---

### Post by mips on 2011-01-21
Quickly browsing through that info I see no obvious problems.

---

### Post by mips on 2011-01-21
What happens if you remove the dlink router and connect your pc directly to the cable modem? Is the speed the same as with the dlink or better?

What happens if you use other dns server like 208.67.222.222, 208.67.220.220 instead of the automatically assigned eastlink ones?

What happens if you disable IPv6?
[http://www.webupd8.org/2010/05/how-t...untu-1004.html](http://www.webupd8.org/2010/05/how-t...untu-1004.html)
[http://www.ubuntugeek.com/how-to-dis...in-ubuntu.html](http://www.ubuntugeek.com/how-to-dis...in-ubuntu.html)

---

### Post by saggz on 2011-01-23
Thank you again for your help and replies.

I disabled IPv6 and it seems to of helped quite a bit. I guess I am going to get the best I can since I can't plug straight into the cable modem because the other people in my building pay me for the internet. I do however, get the full 30mbps on [www.speedtest.net](www.speedtest.net) so I am not sure I suppose I will leave it like it is because I love Ubuntu Linux.

Thank you very much for your help, it is much appreciated!

---

### Post by mips on 2011-01-24
Also try using those dns servers I listed above to see if it helps. You only have to configure them on your pc, not the whole network.

---

