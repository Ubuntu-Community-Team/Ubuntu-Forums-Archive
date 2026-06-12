---
title: "rt73usb problems in Ubuntu 10.04"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by nicpac22 on 2010-06-25
I recently upgraded from Ubuntu 9.10 to 10.04 (both 64-bit) and my USB WiFi adapter which previously worked fine stopped working.  The adapter is a Hama USB stick based on the Ralink rt73 chipset.  I've tried using the Ralink drivers that come with 10.04 (both rt2800usb and rt73usb) but neither work.  When I use rt2800usb, the adapter is recognized as interface wlan0, however I can't see any wireless networks.  When I use rt73usb (and blacklist rt2800usb to avoid conflicts) I no longer have a wlan0 interface and there is no wireless adapter shown in the network manager.  I've pasted in the results of lsmod, lsusb, and ifconfig -a (with MAC addresses removed) below.  Any help would be greatly appreciated.

Thanks,

Nick

```
bender:~> lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:01a4 Elan Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
bender:~> lsmod
Module                  Size  Used by
rt73usb                24256  0 
crc_itu_t               1715  1 rt73usb
rt2x00usb              11260  1 rt73usb
rt2x00lib              32133  2 rt73usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211
binfmt_misc             7960  1 
mxl5005s               38780  1 
s5h1409                 9670  1 
tuner_simple           15041  1 
tuner_types            18305  1 tuner_simple
cs5345                  3306  1 
tuner                  23224  1 
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cx18                  118978  0 
dvb_core              102929  1 cx18
i2c_algo_bit            6024  1 cx18
cx2341x                13761  1 cx18
v4l2_common            18357  4 cs5345,tuner,cx18,cx2341x
joydev                 11072  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ppdev                   6375  0 
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64608  0 
serio_raw               4918  0 
videodev               40486  4 cs5345,tuner,cx18,v4l2_common
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    12020  1 videodev
ir_common              43415  1 cx18
intel_agp              29225  0 
tveeprom               13882  1 cx18
nvidia              10832442  28 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
parport_pc             29958  1 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
ohci1394               30260  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
ieee1394               94675  1 ohci1394
r8169                  39650  0 
mii                     5237  1 r8169
pata_jmicron            2747  0 
ahci                   37646  5 
``````
bender:~> ifconfig -a
eth0      Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14780669 (14.7 MB)  TX bytes:4600013 (4.6 MB)
          Interrupt:30 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

```

---

### Post by LMB on 2010-07-06
I have an identical problem. My dmesg |tail is: 

```
[ 1240.647446] wlan2: deauthenticating from 00:17:3f:e2:4f:81 by local  choice (reason=3)
[ 1240.650525] wlan2: direct probe to AP 00:17:3f:e2:4f:81 (try 1)
[ 1240.848042] wlan2: direct probe to AP 00:17:3f:e2:4f:81 (try 2)
[ 1240.850517] wlan2: direct probe responded
[ 1240.850522] wlan2: authenticate with AP 00:17:3f:e2:4f:81 (try 1)
[ 1240.852628] wlan2: authenticated
[ 1240.852663] wlan2: associate with AP 00:17:3f:e2:4f:81 (try 1)
[ 1240.862196] wlan2: RX AssocResp from 00:17:3f:e2:4f:81 (capab=0x31  status=0 aid=1)
[ 1240.862203] wlan2: associated
[ 1240.875371] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 1251.444019] wlan2: no IPv6 routers present
[ 1288.760111] wlan2: deauthenticating from 00:17:3f:e2:4f:81 by local  choice (reason=3)
```I only wander what *deauthenticating  by local  choice (reason=3)* means.

Also, iwconfig: 
```

wlan2     IEEE 802.11bg  ESSID:"204/1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00.....   
          Bit Rate=1 Mb/s   Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by igar on 2010-12-20
Bumping this up since I have exactly the same problem.  dmesg message is the same as above and driver is the same.

---

### Post by magisterms on 2010-12-23
The same issue here: freshly updated Ubuntu 10.04. My device is a TP-LINK modem with RT73 chipset and only slightly different code:

Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

"2070" versus "3070" quoted by you guys earlier...

Any help would be greatly appreciated.

PS: I have tried the common solutions, which have worked all Ubuntu releases through 9.04, which were quoted in earlier posts:
[here]("http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2") and
[here]("http://ubuntuforums.org/showthread.php?t=680310")

These methods are both failing at the point where I have newest (end of 2009) version of the legacy RT73 downloaded, but when I give "make" command it fails to perform.

---

