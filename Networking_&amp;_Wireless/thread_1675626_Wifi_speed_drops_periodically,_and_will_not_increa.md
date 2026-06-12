---
title: "Wifi speed drops periodically, and will not increase without reconnecting"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by seanodonnell on 2011-01-25
after maybe half an hour, the wireless download rate drops to about 110ks (and runs happily at up to 20x this until then). At that point, it will never pick back up above that rate unless i disconnect and reconnect. Once the problem occurs once, its like to reoccur about every 5 to 10 minutes until the machine has rebooted.

Anyone have any ideas?

Its a lenovo w500

Ubuntu 10.10

2.6.35-24-generic x86_64


lspci:
Intel Corporation Ultimate N WiFi Link 5300

sean@w500:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:6a:68:6f:72  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe68:6f72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7732210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5571818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10865535277 (10.8 GB)  TX bytes:700767977 (700.7 MB)

sean@w500:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"odonnell"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:57:7E:80   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sean@w500:~$ lsmod | grep wl
iwlagn                202721  0 
iwlcore               146875  1 iwlagn
mac80211              266625  2 iwlagn,iwlcore
cfg80211              170293  5 ipw2200,libipw,iwlagn,iwlcore,mac80211

dmesg

[ 3289.719740] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 3289.719743] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[ 3289.719812] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3289.719820] iwlagn 0000:03:00.0: setting latency timer to 64
[ 3289.719888] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[ 3289.744058] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3289.744819] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[ 3289.936216] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[ 3289.941646] phy0: Selected rate control algorithm 'iwl-agn-rs'
[10326.450140] iwlagn 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr 00:0f:66:57:7e:80
[106916.260143] iwlagn 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr 00:0f:66:57:7e:80
[106960.410221] iwlagn 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr 00:0f:66:57:7e:80
[107005.161442] iwlagn 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr 00:0f:66:57:7e:80
[107017.250414] iwlagn 0000:03:00.0: ACTIVATE a non DRIVER active station id 0 addr 00:0f:66:57:7e:80

---

### Post by raumkundschafter on 2011-01-28
i've the same issue. 
10.10 with Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
and 2.6.35-25-generic kernel

---

### Post by subzero27 on 2011-01-28
I have heard that many people are facing this. I think its a kernel issue.

BTW did you try using wifi while on windows. Does it run fine ?

---

