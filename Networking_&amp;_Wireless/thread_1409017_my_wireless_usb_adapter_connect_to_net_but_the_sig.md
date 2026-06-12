---
title: "my wireless usb adapter connect to net but the signal is very week"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by rsd220 on 2010-02-17
[FONT=Arial][SIZE=3]i have wireless usb adapter rtl8187 from micromax company 
my proplem is the signal is very weak and i cannot open website 

can i increase the signal ?
[/SIZE][/FONT]
iwconfig 
```
  lo        no wireless extensions.
 

 eth0      no wireless extensions.
 

 wmaster0  no wireless extensions.
 

 wlan0     IEEE 802.11bg  ESSID:"Dentistry"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:D0:F7:10:72    
           Bit Rate=24 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off
           Power Management:off
           Link Quality=39/70  Signal level=-71 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 eth1      unassociated  Mode:Managed  Frequency=2.412 GHz   
           Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=20 dBm    
           Sensitivity=8/0   
           Retry limit:7   RTS thr:off   Fragment thr:off
           Power Management:off
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[FONT=Arial][SIZE=3]information about my adapter[/SIZE][/FONT]
 ```
           [COLOR=#0000bb]lsusb [/COLOR] 
 [COLOR=#0000bb]Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse [/COLOR] 
 [COLOR=#0000bb]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/COLOR] 
 [COLOR=#0000bb]Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter [/COLOR] 
 [COLOR=#0000bb]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/COLOR] 
 [COLOR=#0000bb]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/COLOR] 
 [COLOR=#0000bb]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/COLOR] 
 
``````
           [COLOR=#0000bb]ifconfig -a [/COLOR] 
 [COLOR=#0000bb]ifconfig -a: command not found [/COLOR] 
 
``````
           [COLOR=#0000bb]lsmod [/COLOR] 
 [COLOR=#0000bb]Module                  Size  Used by [/COLOR] 
 [COLOR=#0000bb]binfmt_misc             8356  1 [/COLOR] 
 [COLOR=#0000bb]ppdev                   6688  0 [/COLOR] 
 [COLOR=#0000bb]snd_intel8x0           30168  2 [/COLOR] 
 [COLOR=#0000bb]snd_ac97_codec        101216  1 snd_intel8x0 [/COLOR] 
 [COLOR=#0000bb]ac97_bus                1532  1 snd_ac97_codec [/COLOR] 
 [COLOR=#0000bb]snd_pcm_oss            37920  0 [/COLOR] 
 [COLOR=#0000bb]snd_mixer_oss          16028  1 snd_pcm_oss [/COLOR] 
 [COLOR=#0000bb]snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss [/COLOR] 
 [COLOR=#0000bb]snd_seq_dummy           2656  0 [/COLOR] 
 [COLOR=#0000bb]snd_seq_oss            28576  0 [/COLOR] 
 [COLOR=#0000bb]snd_seq_midi            6432  0 [/COLOR] 
 [COLOR=#0000bb]joydev                 10272  0 [/COLOR] 
 [COLOR=#0000bb]snd_rawmidi            22208  1 snd_seq_midi [/COLOR] 
 [COLOR=#0000bb]pcmcia                 36808  0 [/COLOR] 
 [COLOR=#0000bb]snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi [/COLOR] 
 [COLOR=#0000bb]iptable_filter          3100  0 [/COLOR] 
 [COLOR=#0000bb]arc4                    1660  2 [/COLOR] 
 [COLOR=#0000bb]snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event [/COLOR] 
 [COLOR=#0000bb]yenta_socket           24200  1 [/COLOR] 
 [COLOR=#0000bb]ecb                     2524  2 [/COLOR] 
 [COLOR=#0000bb]snd_timer              22276  2 snd_pcm,snd_seq [/COLOR] 
 [COLOR=#0000bb]ip_tables              11692  1 iptable_filter [/COLOR] 
 [COLOR=#0000bb]rsrc_nonstatic         11644  1 yenta_socket [/COLOR] 
 [COLOR=#0000bb]snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq [/COLOR] 
 [COLOR=#0000bb]psmouse                56180  0 [/COLOR] 
 [COLOR=#0000bb]ipw2200               140292  0 [/COLOR] 
 [COLOR=#0000bb]pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic [/COLOR] 
 [COLOR=#0000bb]snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/COLOR] 
 [COLOR=#0000bb]libipw                 43148  1 ipw2200 [/COLOR] 
 [COLOR=#0000bb]soundcore               7264  1 snd [/COLOR] 
 [COLOR=#0000bb]lib80211                6432  2 ipw2200,libipw [/COLOR] 
 [COLOR=#0000bb]serio_raw               5280  0 [/COLOR] 
 [COLOR=#0000bb]rtl8187                50624  0 [/COLOR] 
 [COLOR=#0000bb]snd_page_alloc          9156  2 snd_intel8x0,snd_pcm [/COLOR] 
 [COLOR=#0000bb]x_tables               16544  1 ip_tables [/COLOR] 
 [COLOR=#0000bb]shpchp                 32272  0 [/COLOR] 
 [COLOR=#0000bb]mac80211              181236  1 rtl8187 [/COLOR] 
 [COLOR=#0000bb]toshiba_acpi           10744  0 [/COLOR] 
 [COLOR=#0000bb]led_class               4096  1 rtl8187 [/COLOR] 
 [COLOR=#0000bb]eeprom_93cx6            1916  1 rtl8187 [/COLOR] 
 [COLOR=#0000bb]cfg80211               93052  2 rtl8187,mac80211 [/COLOR] 
 [COLOR=#0000bb]lp                      8964  0 [/COLOR] 
 [COLOR=#0000bb]parport                35340  2 ppdev,lp [/COLOR] 
 [COLOR=#0000bb]usbhid                 38208  0 [/COLOR] 
 [COLOR=#0000bb]fbcon                  36640  72 [/COLOR] 
 [COLOR=#0000bb]tileblit                2460  1 fbcon [/COLOR] 
 [COLOR=#0000bb]font                    8124  1 fbcon [/COLOR] 
 [COLOR=#0000bb]bitblit                 5372  1 fbcon [/COLOR] 
 [COLOR=#0000bb]softcursor              1756  1 bitblit [/COLOR] 
 [COLOR=#0000bb]i915                  221064  3 [/COLOR] 
 [COLOR=#0000bb]drm                   159584  3 i915 [/COLOR] 
 [COLOR=#0000bb]i2c_algo_bit            5760  1 i915 [/COLOR] 
 [COLOR=#0000bb]e100                   32452  0 [/COLOR] 
 [COLOR=#0000bb]mii                     5212  1 e100 [/COLOR] 
 [COLOR=#0000bb]ohci1394               29900  0 [/COLOR] 
 [COLOR=#0000bb]ieee1394               86596  1 ohci1394 [/COLOR] 
 [COLOR=#0000bb]intel_agp              27484  2 i915 [/COLOR] 
 [COLOR=#0000bb]agpgart                34988  2 drm,intel_agp [/COLOR] 
 [COLOR=#0000bb]video                  19380  1 i915 [/COLOR] 
 [COLOR=#0000bb]output                  2780  1 video [/COLOR] 
 
```

---

### Post by aeiah on 2010-02-17
do you get ping replies? your signal quality doesnt seem tooooo bad. says quality is 39/70. it might be a different problem rather than signal strength.

through iwconfig and/or iwlist you should be able to find your signal to noise ratio (or at least your signal reading and noise reading). the difference between them is your SNR and a even with an SNR of 6 ive had a somewhat reliable connection. you should aim for 25+ though

---

### Post by rsd220 on 2010-02-17
[FONT=Arial Black][SIZE=4][COLOR=Red][COLOR=Blue]how can i get ping replies?[/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by superprash2003 on 2010-02-17
post output of** ping google.com** and** ping 208.67.222.222** from ubuntu terminal

---

### Post by rsd220 on 2010-02-17
[COLOR=#0000bb]ping google.com [/COLOR] 
 [COLOR=#0000bb]ping: unknown host google.com 
[/COLOR]


 	 	 [COLOR=#0000bb]ping 208.67.222.222[/COLOR]
```
 	 	 [COLOR=#0000bb]ING 208.67.222.222 (208.67.222.222) 56(84) bytes of data. [/COLOR] 
 [COLOR=#0000bb]64 bytes from 208.67.222.222: icmp_seq=2 ttl=54 time=1007 ms [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=57 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=58 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=59 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=60 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=61 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=62 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=63 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=64 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=65 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=66 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=67 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=68 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=117 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=118 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=119 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=120 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=121 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=122 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=123 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=124 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=125 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=126 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=127 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=128 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=129 Destination Host Unreachable [/COLOR] 
 [COLOR=#0000bb]From 192.168.1.64 icmp_seq=130 Destination Host Unreachable [/COLOR] 
 
```

---

### Post by dummy910 on 2010-02-17
Try installing the backports for your distro... works wonders for all the karmic machines i've set up with wifi ;)
```
sudo apt-get install linux-backports-modules-karmic-generic
```
then reboot and see what happens with that signal....

---

### Post by rsd220 on 2010-02-17
> **dummy910 said:**
> Try installing the backports for your distro... works wonders for all the karmic machines i've set up with wifi ;)
```
sudo apt-get install linux-backports-modules-karmic-generic
```then reboot and see what happens with that signal....

no change

---

