---
title: "wireless problem"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by achechen on 2009-05-16
Hello there.
My wireless network works on Windows XP but not on Ubuntu (I can connect to the wireless network but I can't open any webpages). Please help. Required information:

Network information on Windows XP:
```
IP: 192.168.1.72
mask: 255.255.255.0
gateway: 192.168.3.2
dns: 192.204.159.1, 192.204.152.34
```

Ubuntu:
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

alper@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

alper@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:18:ae:35  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe18:ae35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9851 (9.8 KB)  TX bytes:10372 (10.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-18-AE-35-65-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

alper@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Domowa"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:BF:63:0F:FA   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=97/100  Signal level:-29 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

alper@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
arc4                    9856  2 
ecb                    10752  2 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                97912  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
uvcvideo               63240  0 
mac80211              217208  1 iwl3945
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                61972  0 
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          9344  1 uvcvideo
soundcore              15200  1 snd
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
intel_agp              34108  0 
pcspkr                 10496  0 
serio_raw              13316  0 
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
led_class              12036  1 iwl3945
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
agpgart                42696  1 intel_agp
btusb                  19608  2 
cfg80211               38032  2 iwl3945,mac80211
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

[   25.726967] wlan0: direct probe to AP 00:12:bf:63:0f:fa try 1
[   25.924062] wlan0: direct probe to AP 00:12:bf:63:0f:fa try 2
[   26.124066] wlan0: direct probe to AP 00:12:bf:63:0f:fa try 3
[   26.324068] wlan0: direct probe to AP 00:12:bf:63:0f:fa timed out
[   31.976972] wlan0: authenticate with AP 00:12:bf:63:0f:fa
[   31.978784] wlan0: authenticate with AP 00:12:bf:63:0f:fa
[   31.978796] wlan0: authenticated
[   31.978801] wlan0: associate with AP 00:12:bf:63:0f:fa
[   31.989224] wlan0: RX AssocResp from 00:12:bf:63:0f:fa (capab=0x461 status=0 aid=1)
[   31.989230] wlan0: associated
[   31.993122] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.540050] wlan0: no IPv6 routers present
[   86.277249] wlan0 direct probe responded
[   86.277259] wlan0: authenticate with AP 00:12:bf:63:0f:fa
[   86.278702] wlan0: authenticated
[   86.278710] wlan0: associate with AP 00:12:bf:63:0f:fa
[   86.283226] wlan0: RX ReassocResp from 00:12:bf:63:0f:fa (capab=0x461 status=0 aid=1)
[   86.283232] wlan0: associated

alper@ubuntu:~$ sudo lshw -C network
[sudo] password for alper: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:18:ae:35
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.72 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:27:6b:6c:64:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

wlan0     Scan completed :
          Cell 01 - Address: 00:12:BF:63:0F:FA
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=97/100  Signal level:-29 dBm  Noise level=-69 dBm
                    Encryption key:off
                    IE: Unknown: 000100
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000001a408fc5122
                    Extra: Last beacon: 80ms ago
          Cell 02 - Address: 00:12:BF:63:0F:FA
                    ESSID:"Domowa"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=96/100  Signal level:-32 dBm  Noise level=-69 dBm
                    Encryption key:off
                    IE: Unknown: 0006446F6D6F7761
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 240ms ago


alper@ubuntu:~$ lsb_release -d
Description:	Ubuntu 9.04

alper@ubuntu:~$ uname -mr
2.6.28-11-generic i686
alper@ubuntu:~$ 

alper@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface wlan0=wlan0.
```

---

### Post by spd106 on 2009-05-16
Your wireless looks ok, though you have a nameless duplicate AP. If you have turned off the AP's essid broadcast, then you might want to turn it back on again. 

> ```
IP: 192.168.1.72
mask: 255.255.255.0
gateway: 192.168.3.2
dns: 192.204.159.1, 192.204.152.34
```

I think you've got some confused settings. Can you ping the router/gateway?

Could you also please post your routing table?

**ip r**

or

**route**

---

