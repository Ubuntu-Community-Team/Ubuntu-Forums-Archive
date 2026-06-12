---
title: "cannot transfer files from ubuntu to windows"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by necromonger on 2010-03-20
I connect to the internet and my network with a wusb54g wireless adapter.
The problem is when i try to transfer a file from this ubuntu machine my wireless network shuts down.And i do not know why. my internet is fine it only happens during a file transfer here is some info.
greg@ubuntu-desktop:~$ lsusb
Bus 007 Device 003: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 007 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
greg@ubuntu-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8970 (8.9 KB)  TX bytes:8970 (8.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:b6:5a:9c:a5  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe5a:9ca5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:554272 (554.2 KB)  TX bytes:71242 (71.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-5A-9C-A5-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

greg@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"netgear"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:F2:7D:49:34   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

greg@ubuntu-desktop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"netgear"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:F2:7D:49:34   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

greg@ubuntu-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
arc4                    2144  2 
ecb                     3296  2 
rt2500usb              23364  0 
rt2x00usb              13600  1 rt2500usb
rt2x00lib              34624  2 rt2500usb,rt2x00usb
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210040  2 rt2x00usb,rt2x00lib
snd_ca0106             41216  2 
snd_ac97_codec        125720  1 snd_ca0106
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iptable_filter          3872  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              109144  2 rt2x00lib,mac80211
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
lp                     11908  0 
parport                40528  2 ppdev,lp
dell_wmi                3216  0 
dcdbas                  9136  0 
usblp                  15136  0 
snd                    77096  14 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_ca0106,snd_pcm
joydev                 13088  0 
psmouse                57124  0 
serio_raw               6596  0 
usbhid                 43968  0 
radeon                684576  2 
ttm                    43056  1 radeon
drm                   194400  4 radeon,ttm
i2c_algo_bit            7076  1 radeon
intel_agp              33040  0 
greg@ubuntu-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:7D:49:34
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"netgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000219ca38183
                    Extra: Last beacon: 47450ms ago
                    IE: Unknown: 00076E657467656172
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180203F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

greg@ubuntu-desktop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
greg@ubuntu-desktop:~$ lsb_release -d
Description:	Ubuntu 9.10
greg@ubuntu-desktop:~$ uname -mr
2.6.31-20-generic x86_64
greg@ubuntu-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
greg@ubuntu-desktop:~$ wmaster0  Interface doesn't support scanning.
> 
> wlan0     Scan completed :
>           Cell 01 - Address: 00:26:F2:7D:49:34
>                     Channel:6
>                     Frequency:2.437 GHz (Channel 6)
>                     Quality=50/70  Signal level=-60 dBm  
>                     Encryption key:off
>                     ESSID:"netgear"
>                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
>                               24 Mb/s; 36 Mb/s; 54 Mb/s
>                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
>                     Mode:Master
>                     Extra:tsf=000000219ca38183
>                     Extra: Last beacon: 47450ms ago
>                     IE: Unknown: 00076E657467656172
>                     IE: Unknown: 010882848B9624B0486C
>                     IE: Unknown: 030106
>                     IE: Unknown: 2A0106
>                     IE: Unknown: 2F0106
>                     IE: Unknown: 32048C129860
>                     IE: Unknown: DD090010180203F0000000
>                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
> 
> greg@ubuntu-desktop:~$ iwlist scan wlan0
> iwlist: unknown command `wlan0' (check 'iwlist --help').
bash: syntax error near unexpected token `('
greg@ubuntu-desktop:~$ greg@ubuntu-desktop:~$ lsb_release -d
greg@ubuntu-desktop:~$: command not found
greg@ubuntu-desktop:~$ Description:Ubuntu 9.10
Description:Ubuntu: command not found
greg@ubuntu-desktop:~$ greg@ubuntu-desktop:~$ uname -mr
greg@ubuntu-desktop:~$: command not found
greg@ubuntu-desktop:~$ 2.6.31-20-generic x86_64
2.6.31-20-generic: command not found
greg@ubuntu-desktop:~$ greg@ubuntu-desktop:~$ sudo /etc/init.d/networking restart
greg@ubuntu-desktop:~$: command not found
greg@ubuntu-desktop:~$  * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

---

### Post by necromonger on 2010-03-20
A little help please?

---

### Post by necromonger on 2010-03-20
I clicked on my network and this popped up.
Sorry, could not display all the contents of "Windows Network": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by necromonger on 2010-03-21
bump

---

### Post by drdos2006 on 2010-03-21
Try changing to a different channel from channel 6 on your router and your wireless card, to maybe 10 or 11 in your router and wireless card.

regards

---

### Post by necromonger on 2010-03-23
tried that still no luck.

---

