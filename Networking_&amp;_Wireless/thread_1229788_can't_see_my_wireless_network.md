---
title: "can't see my wireless network"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by necromonger on 2009-08-02
dell xps 410 with linksys wusb 54g wireless adapter for internet and network.greg@greg-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 002: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
greg@greg-desktop:~$ lspci -nn | grep 'Wireless Brand
> grep 'Wireless Brand
grep: Brand: No such file or directory greg@greg-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24734 (24.7 KB)  TX bytes:24734 (24.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:b6:5a:9c:a5  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe5a:9ca5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4494629 (4.4 MB)  TX bytes:694596 (694.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-5A-9C-A5-63-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
greg@greg-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:42:E5:ED   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

greg@greg-desktop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:42:E5:ED   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
greg@greg-desktop:~$ lsmod
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  1 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
snd_ca0106             39968  2 
snd_ac97_codec        112292  1 snd_ca0106
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi
rt2500usb              27904  0 
rt2x00usb              18688  1 rt2500usb
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
rt2x00lib              37888  2 rt2500usb,rt2x00usb
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              12036  1 rt2x00lib
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 18368  0 
mac80211              217592  2 rt2x00usb,rt2x00lib
intel_agp              34108  0 
psmouse                61972  0 
snd                    62756  14 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
ac97_bus                9856  1 snd_ac97_codec
snd_page_alloc         16904  2 snd_ca0106,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
dcdbas                 15264  0 
agpgart                42696  2 drm,intel_agp
serio_raw              13444  0 
pcspkr                 10496  0 
usblp                  20224  0 
cfg80211               38288  2 rt2x00lib,mac80211
usbhid                 42336  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

greg@greg-desktop:~$ lsmod | grep "wlan_module_name
>
greg@greg-desktop:~$ lsmod | grep "wlan_module_name
> dmesg

> sudo lshw -C network
>
> iwlist scan
>  iwlist scan wlan0
>
> lsb_release -d
>
> uname -mr
>
> sudo /etc/init.d/networking restart
>

i can connect to the internet just fine but i can't see or get on my wireless windows machines i need help.

---

### Post by necromonger on 2009-08-03
no one can help me?

---

### Post by HappyFeet on 2009-08-03
Did you install samba? The way I have done it, is to install samba and then go to Places>Network and it automatically saw any windows machines.

---

### Post by cariboo on 2009-08-03
Have you got sharing setup properly on your windows computer? 

Can you ping your windows computer by name or by ip address?

Are both computers in the same workgroup?

---

