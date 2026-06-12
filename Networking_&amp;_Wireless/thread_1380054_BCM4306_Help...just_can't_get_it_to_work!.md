---
title: "BCM4306 Help...just can't get it to work!"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by mbabauer on 2010-01-13
I have an earlier post asking for help with getting this card to work with the ndiswrapper.  I thought I would try to start over from scratch.

This morning I reinstalled 9.10 from a freshly burned DVD.  The install went fine.  Upon reboot, I followed [these instructions]("http://caytin.wordpress.com/2009/07/21/how-to-broadcom-wireless-in-ubuntu-jaunty-jackalope/") to get the WiFi card working.  However, it is still being EXTREMELY problematic.

The problem I have using the b43legacy drivers is that it keeps timing out, and when it does FINALLY connect, I get about 1-2 minutes of a working connection before it drops, and that's IF I can get it to connect.

I have read several troubleshooting guides, followed them all, but so far I can't figure out what's going on.

The laptop is a Compaq Presario 2100, the card is reported as a BCM4306 (rev2).  Here are some outputs from commands:

**lcpci**
```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
```**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:0f:20:1f:73:dc  
          inet addr:10.88.0.109  Bcast:10.88.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe1f:73dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19155310 (19.1 MB)  TX bytes:606949 (606.9 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.6 KB)  TX bytes:1600 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:57:89:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-57-89-39-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"stay_out"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```**lsmod**
```
Module                  Size  Used by
b44                    28684  0 
mii                     5212  1 b44
ieee80211_crypt_tkip     9276  0 
ieee80211_crypt         5024  1 ieee80211_crypt_tkip
isofs                  31620  0 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_ali5451            18888  2 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
pcmcia                 36808  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1660  2 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ecb                     2524  2 
yenta_socket           24200  1 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         11644  1 yenta_socket
joydev                 10272  0 
shpchp                 32272  0 
soundcore               7264  1 snd
i2c_ali15x3             6336  0 
b43legacy             117752  0 
iptable_filter          3100  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          9156  1 snd_pcm
i2c_ali1535             5792  0 
mac80211              181236  1 b43legacy
ip_tables              11692  1 iptable_filter
psmouse                56180  0 
lp                      8964  0 
cfg80211               93052  2 b43legacy,mac80211
serio_raw               5280  0 
led_class               4096  1 b43legacy
ppdev                   6688  0 
parport_pc             31940  1 
x_tables               16544  1 ip_tables
parport                35340  3 lp,ppdev,parport_pc
floppy                 54916  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ssb                    35300  2 b44,b43legacy
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
natsemi                26944  0 
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp
```**iwevent** (shows repeated attempts to contact the AP)
```
07:29:56.407759   wlan0    Set Mode:Managed
07:29:57.879991   wlan0    Scan request completed
07:30:04.281432   wlan0    Scan request completed
07:30:04.281522   wlan0    Set Mode:Managed
07:30:04.310765   wlan0    Set Frequency:2.437 GHz (Channel 6)
07:30:04.910434   wlan0    New Access Point/Cell address:Not-Associated
07:30:10.741501   wlan0    Scan request completed
07:30:10.741595   wlan0    Set Mode:Managed
07:30:10.741628   wlan0    Set Frequency:2.437 GHz (Channel 6)
07:30:11.354339   wlan0    New Access Point/Cell address:Not-Associated
07:30:17.157513   wlan0    Scan request completed
07:30:17.157607   wlan0    Set Mode:Managed
07:30:17.157640   wlan0    Set Frequency:2.437 GHz (Channel 6)
07:30:17.770404   wlan0    New Access Point/Cell address:Not-Associated
07:30:23.413543   wlan0    Scan request completed
07:30:23.413638   wlan0    Set Mode:Managed
```**dmesg** (shows timeouts and some warnings)
```
[ 1309.264578] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1309.464154] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1309.664131] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1309.864132] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 1315.696588] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1315.896110] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1316.096091] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1316.296119] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 1318.768178] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1318.770573] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1322.122541] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1322.320126] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1322.520126] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1322.720121] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 1328.532463] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1328.732094] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1328.932100] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1329.132102] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 1334.968641] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1335.168159] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1335.368126] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1335.568121] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 1341.384669] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1341.584112] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1341.788232] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1341.988106] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 1347.797138] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1347.996116] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1348.196103] wlan0: authenticate with AP 00:18:39:6a:08:16
[ 1348.396144] wlan0: authentication with AP 00:18:39:6a:08:16 timed out
[ 2278.295819] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)

```

A few things to note: The guide I used this morning had me try to load the 'wl' module.  I don't have a wl module, so that failed.  It also had me try to unload the ssb module, but that also failed because it said it was in use.  Also, I have seen mention in several places that this BCM4306 should used the b43 driver, not the b43legacy driver.  I tried with the b43, but when I do, the card doesn't show up in iwconfig any more.

Thanks in advance for any help you can offer...

---

### Post by bkratz on 2010-01-13
Searching for an answer for you ( not much yet) but I have confirmed that the rev 2 version of the card uses the b43legacy while the rev 3 version uses b43.

---

### Post by bkratz on 2010-01-13
> **bkratz said:**
> Searching for an answer for you ( not much yet) but I have confirmed that the rev 2 version of the card uses the b43legacy while the rev 3 version uses b43.

The link I was referring too is back up (it was down) here it is

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

look under supported chip types

---

### Post by homeuser1 on 2010-01-13
What's the output of "rfkill list"  I have the exact same card as you and my card installed fine with the driver that ubuntu selected.  My problem was something with the 9.10 update that switched my wireless off.  You don't want any "yes" blocks.  

dell@dell-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Here's my wireless card

*-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff

---

### Post by mbabauer on 2010-01-14
Bah, I gave up on this.  To many wasted hours.  So, I bought a USB dongle last night from one of the big-box stores, and that is working fine.  I blacklisted the b43legacy drivers so there wasn't a conflict.

---

### Post by homeuser1 on 2010-01-14
I just installed 9.04 and all my wireless problems are gone for now.  :D

---

### Post by mbabauer on 2010-01-15
I started with 9.04, then moved to 9.10 hoping it was driver-related (and fixed in the newer version).  I wish I could share some magical fix with the forums, but alas my patience wore thin.  Plus my kids were nagging me to get the laptop done and handed over to them.

It's very possible that the wifi card is just bad.  The laptop was given to me from a friend who's son decided to stick a large magnet right over the drive.  I told him it could be fixed, most likely, but he wanted a new laptop and this was a perfect excuse to get one.  Ironically, it's running right now with memory and HDD from an Apple G4 PowerBook.

---

