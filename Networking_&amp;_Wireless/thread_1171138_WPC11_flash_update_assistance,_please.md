---
title: "WPC11 flash update assistance, please"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by kokigami on 2009-05-27
Hello, and thanks for any assistance I can get. Been playing with Ubuntu for a few months now, and getting some idea of what I am doing. I just installed it on an old Compaq Presario 1200 and most functions seem sound. I am trying to go wireless with a Lynksys WPC11 v3 pcmcia card. It works, but doesn't support WPA which is what we have set up in my home - specifically because my home computer didn't like the "transitional WEP" that our Airport extreme was putting out. I found this article on flashing the WPC11 so that it supports WPA.

[http://www.jlime.com/forum/viewtopic.php?f=6&t=1507](http://www.jlime.com/forum/viewtopic.php?f=6&t=1507)

but, when I get to the test run they suggest, I don't get any love from the system. I do get this..


prompt:~$ prism2_srec -v wlan0 pk010101.hex sf010804.hex
S3 CRC-16 generation record: start=0x007E17FE len=2 prog=0
Start address 0x00000000
srec summary for pk010101.hex
Component: 0x0015 1.1.1 (primary firmware)
Supported platforms:
  0x800c 1.0.0,  0x8013 1.0.0,  0x8017 1.0.0,  0x801b 1.0.0,  0x8022 1.0.0
Interface compatibility information:
  role=Supplier variant=1 range=4-4 iface=Primary Firmware-Driver (3)
  role=Actor    variant=2 range=1-1 iface=Controller-Firmware (2)
Separate S3 data areas:
S3 area count: 3
  addr=0x007E0000..0x007E0B55 (len=2902)
  addr=0x007E0C00..0x007E151F (len=2336)
  addr=0x007E17FE..0x007E17FF (len=2)
Total data length: 5240
Start address 0x00000000

S3 CRC-16 generation record: start=0x007E1800 len=65536 prog=1
Start address 0x00000000
srec summary for sf010804.hex
Component: 0x001f 1.8.4 (station firmware)
Supported platforms:
  0x800a 1.0.0,  0x800b 1.0.0,  0x800c 1.0.0,  0x800d 1.0.0,  0x8012 1.0.0
  0x8013 1.0.0,  0x8014 1.0.0,  0x8016 1.0.0,  0x8017 1.0.0,  0x8018 1.0.0
  0x801a 1.0.0,  0x801b 1.0.0,  0x801c 1.0.0,  0x8021 1.0.0,  0x8022 1.0.0
  0x8023 1.0.0
Interface compatibility information:
  role=Supplier variant=4 range=1-15 iface=Station Firmware-Driver (4)
  role=Actor    variant=1 range=1-1 iface=Modem-Firmware (1)
  role=Actor    variant=2 range=1-1 iface=Controller-Firmware (2)
  role=Actor    variant=1 range=4-4 iface=Primary Firmware-Driver (3)
Separate S3 data areas:
S3 area count: 3
  addr=0x007E1800..0x007EEAF9 (len=54010)
  addr=0x007F0800..0x007F17FF (len=4096)
  addr=0x007FE000..0x007FECD1 (len=3282)
Total data length: 61388
Start address 0x00000000
[B]
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not permitted
Missing wlan component info
Could not read wlan RIDs[/B]

So, not sure what that error means. Am I missing a bit of software, or is my card missing a bit of - card? 



some answers to questions I suspect you will ask - because you always do, not because I understand what they are about...

ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-06-25-2B-82-D8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:929703 (929.7 KB)  TX bytes:192947 (192.9 KB)
          Interrupt:3 Base address:0x100 

wlan0     Link encap:Ethernet  HWaddr 00:06:25:2b:82:d8  
          inet addr:192.168.121.86  Bcast:192.168.121.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe2b:82d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:912567 (912.5 KB)  TX bytes:193331 (193.3 KB)
          Interrupt:3 Base address:0x100

iwconfig

lo        no wireless extensions.

pan0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"secret"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:01:84:28:43   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"secret"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:01:84:28:43   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-69 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:22   Missed beacon:0

cat /etc/network/interfaces

auto lo
iface lo inet loopback

lsmod

Module                  Size  Used by
arc4                    9856  2 
ecb                    10752  2 
ieee80211_crypt_wep    11776  0 
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
hostap_cs              62612  3 
hostap                113924  1 hostap_cs
ieee80211_crypt        13444  2 ieee80211_crypt_wep,hostap
joydev                 18368  0 
pcmcia                 44748  1 hostap_cs
ppdev                  15620  0 
snd_via82xx            32152  3 
gameport               19340  1 snd_via82xx
snd_ac97_codec        112292  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15104  1 snd_via82xx
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           32396  3 
psmouse                61972  0 
via686a                20876  0 
pcspkr                 10496  0 
snd                    62628  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13316  0 
i2c_viapro             15892  0 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic
soundcore              15200  1 snd
video                  25360  0 
via_agp                16256  1 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
output                 11008  1 video
agpgart                42696  1 via_agp
shpchp                 40212  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by BlackRockCity on 2009-10-26
I just worked around this same error:
[B]ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not permitted
Missing wlan component info
Could not read wlan RIDs

[/B]The issue was that I was accidentally trying to update the wrong interface. In my case the card was at wlan1 not wlan0.

So you might try (since this is just a test run, no harm done):
prism2_srec -v wlan1 pk010101.hex sf010804.hex

PS. You might want to use station firmware 1.8.2. I read that 1.8.4 has issues over long distance links. I have no personal experience with either one though. My information comes from here:
[http://junsun.net/linux/intersil-prism/](http://junsun.net/linux/intersil-prism/)

---

