---
title: "New to Ububtu wireless will not connect"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by jowilker on 2011-12-04
Hello, I just registered but have been grazing this and other sites for about a month for my wireless issue.

First let me introduce myself, my name is John, I reside in Creedmoor North Carolina USA, just north of Raleigh.

I have built & troubleshot my own computers for a while. I picked up a Dell PC from the wife's sister, replaced the dead HD with a freshly wiped one and loaded Ububtu 10.04. Much to my surprise I really liked it, loaded Libreoffice and WOW. I tried an HTML editor and was able to work on some html files. Loving it

I sez to meself I can put this on the puter in the shop and not worry about windoz. I got it going, was having trouble with the old wireless card so I get another, and connected. 

It was just a few days before 11.10 came out and me being in a current state of mind upgraded. 

My wireless has not worked since. It is an Anatel 0949 w RTL8185L. I have visited this & other sites, sudoed, ls, get-apt, to death and can not get it to connect. The machine recognizes the card, tries to connect only to report Authentication required by wireless network.

I have a Dlink 615 router set to WEP, with 2 wired PCs, 1 wireless PC, 1 netbook, 2 phones, & 1 son in college that uses it when he is home.

I am tired of messing with it on my own, so here I am. I see many threads that give specific instructions and ask for replies. I am using the pc in question inside the house hardwired to the router. What do I need to do to copy & past from the terminal to the forum if one of you kind folk is willing to give me a hand?

Many thanks in advance

John

---

### Post by praseodym on 2011-12-04
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by jowilker on 2011-12-04
shop@shop-PJ473AA-ABA-M1160N:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)
	Subsystem: Hewlett-Packard Company Device [103c:2a04]
	Kernel driver in use: sis900
--
00:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8225]
	Kernel driver in use: rtl8180
shop@shop-PJ473AA-ABA-M1160N:~$ ^C




shop@shop-PJ473AA-ABA-M1160N:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
shop@shop-PJ473AA-ABA-M1160N:~$ 



shop@shop-PJ473AA-ABA-M1160N:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
bluetooth             148839  7 bnep
vesafb                 13489  1 
binfmt_misc            17292  1 
arc4                   12473  2 
tuner_simple           18151  1 
tuner_types            18998  1 tuner_simple
tda9887                17874  1 
tda8290                22216  0 
tuner                  26836  2 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
msp3400                31543  1 
ac97_bus               12642  1 snd_ac97_codec
saa7115                18447  1 
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
rtl8180                35880  0 
ivtv                  143882  0 
snd_seq_midi           13132  0 
cx2341x                27739  1 ivtv
i2c_algo_bit           13199  1 ivtv
mac80211              393459  1 rtl8180
snd_rawmidi            25241  1 snd_seq_midi
v4l2_common            15793  5 tuner,msp3400,saa7115,ivtv,cx2341x
videodev               85626  6 tuner,msp3400,saa7115,ivtv,cx2341x,v4l2_common
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12653  1 rtl8180
ppdev                  12849  0 
psmouse                73673  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172392  2 rtl8180,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tveeprom               17009  1 ivtv
serio_raw              12990  0 
k8temp                 12905  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
uas                    17699  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sata_sis               12703  0 
sis900                 22729  0 
shop@shop-PJ473AA-ABA-M1160N:~$ 

shop@shop-PJ473AA-ABA-M1160N:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:2f:87:55:25  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe87:5525/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8144832 (8.1 MB)  TX bytes:1239171 (1.2 MB)
          Interrupt:19 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:57:4d:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

shop@shop-PJ473AA-ABA-M1160N:~$ 

shop@shop-PJ473AA-ABA-M1160N:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:2f:87:55:25  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe87:5525/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8144832 (8.1 MB)  TX bytes:1239171 (1.2 MB)
          Interrupt:19 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:57:4d:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


shop@shop-PJ473AA-ABA-M1160N:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

shop@shop-PJ473AA-ABA-M1160N:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
shop@shop-PJ473AA-ABA-M1160N:~$ ^C


shop@shop-PJ473AA-ABA-M1160N:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

---

### Post by bluexrider on 2011-12-04
> **praseodym said:**
> Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

wouldnt it be more reasonable "sudo lshw -c network" 

physically the card is there but the drivers? just a question

---

### Post by jowilker on 2011-12-04
Maybe the warning was a reason not to, dunno.  -J


shop@shop-PJ473AA-ABA-M1160N:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:11:2f:87:55:25
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.18 latency=32 maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:b800(size=256) memory:e1102000-e1102fff memory:20000000-2001ffff
  *-network:1
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:57:4d:73
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=3.0.0-13-generic firmware=N/A latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:d400(size=256) memory:e1104000-e11043ff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by praseodym on 2011-12-04
Which encryption mode is used? I recommend using pure WPA2-AES.
Check additionally:
```
iwconfig
sudo iwlist scan
dmesg | grep rtl8
rfkill list
```

---

### Post by bluexrider on 2011-12-04
found a bug report in the current driver rtl8180 recommends update to current driver rtl8185 which is your chipset

download from here
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352)

follow this how to for installation
_[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)_

---

### Post by jowilker on 2011-12-04
shop@shop-PJ473AA-ABA-M1160N:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




shop@shop-PJ473AA-ABA-M1160N:~$ sudo iwlist scan
[sudo] password for shop: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:41:4D:B7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/100  Signal level=49/100  
                    Encryption key:on
                    ESSID:"wilkerhome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003e3b2732a
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 000A77696C6B6572686F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101



shop@shop-PJ473AA-ABA-M1160N:~$ dmesg | grep rtl8
[   15.980816] rtl8180 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.131976] ieee80211 phy0: hwaddr 0014d1574d73, RTL8185vD + rtl8225z2
[  745.008046] Modules linked in: bnep bluetooth vesafb binfmt_misc arc4 tuner_simple tuner_types tda9887 tda8290 tuner snd_intel8x0 snd_ac97_codec msp3400 ac97_bus saa7115 snd_pcm rtl8180 ivtv snd_seq_midi cx2341x i2c_algo_bit mac80211 snd_rawmidi v4l2_common videodev snd_seq_midi_event eeprom_93cx6 ppdev psmouse snd_seq cfg80211 snd_timer snd_seq_device tveeprom serio_raw k8temp snd soundcore snd_page_alloc parport_pc shpchp lp parport usb_storage uas firewire_ohci firewire_core crc_itu_t sata_sis sis900
shop@shop-PJ473AA-ABA-M1160N:~$ 



shop@shop-PJ473AA-ABA-M1160N:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by jowilker on 2011-12-04
> **bluexrider said:**
> found a bug report in the current driver rtl8180 recommends update to current driver rtl8185 which is your chipset

download from here
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352)

follow this how to for installation
_[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)_

I see the bottom line refers to windows dual boot, this machine is a clean 11.10 only install. What does that do to your suggestion?

I am new to Ubuntu so go easy on me. :)




John

---

### Post by jowilker on 2011-12-04
praseodym You asked for a lot of hacking by me, what do you see??




John

---

### Post by fdrake on 2011-12-04
are you able to connect with no wep security? ma ke the router open and see if you can connect

---

### Post by jowilker on 2011-12-04
> **fdrake said:**
> are you able to connect with no wep security? ma ke the router open and see if you can connect

I didn't want to because it would effect several other working machines & phones.


John

---

### Post by fdrake on 2011-12-04
ok then, can you try this :
```

sudo apt-get install wireless-tools
sudo aptitude update
sudo reboot now

```
and the try to connect with:
```

sudo iwconfig wlan0 essid "wilkerhome" key s:"your_password"

```

---

### Post by jowilker on 2011-12-04
> **fdrake said:**
> ok then, can you try this :
```

sudo apt-get install wireless-tools
sudo aptitude update
sudo reboot now

```
and the try to connect with:
```

sudo iwconfig wlan0 essid "wilkerhome" key s:"your_password"

```

sudo: aptitude: command not found

John

---

### Post by fdrake on 2011-12-04
> **jowilker said:**
> sudo: aptitude: command not found

John

use "sudo apt-get update" instead of "sudo aptitude update"

---

### Post by jowilker on 2011-12-04
shop@shop-PJ473AA-ABA-M1160N:~$ sudo iwconfig wlan0 essid "wilkerhome"  key s:"*******"
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.



John

---

### Post by jowilker on 2011-12-04
The darn thing worked with the version before 11.10.

My youngest son sez, I might have to go back to the older version.


John

---

### Post by fdrake on 2011-12-04
> **jowilker said:**
> The darn thing worked with the version before 11.10.

My youngest son sez, I might have to go back to the older version.


John

it might be a module/ kernel issue due to the upgrade . the best thing you can do is to use the old version. If this is a store-pc use a stable version, like 10.04. and if you need to update make sure you install backports.

---

### Post by jowilker on 2011-12-04
I might try a different card, anyone have any thought on this one?
[http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2688](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=3246388&CatId=2688)

There is a CompUSA store close by, and I might throw $15.00 at it.

There are some $8.00 USB Adapters any thoughts on those?

The machine is a throw away, with a clean wiped HD and a fresh install of 11.10

 

John

---

### Post by praseodym on 2011-12-05
I also recommend going back to 10.04 or even 11.04. The Realtek drivers dont compile atm with kernel 3.

---

### Post by jowilker on 2011-12-05
Thanks, I noticed the driver update was 2 years old, for an older Ubuntu too. We have the computer acting very badly now also. I am now using the house machine hard wired.

The wireless machine will be one of my least used, and I wanted internet in my shop. It is a HP that I reclaimed to try to learn Linux with.

What version do you recommend that I download that will not have issues with the wireless? I don't mind spending $15.00 on a new card, but would like to think it will work out of the box.

best

John

---

