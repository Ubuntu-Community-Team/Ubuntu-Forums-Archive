---
title: "Configuring wifi from command line"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by viniciuscarvalho on 2010-01-24
Hello there! I followed the steps provided here: [http://ubuntuforums.org/showthread.php?t=553844](http://ubuntuforums.org/showthread.php?t=553844) but I can't get my wireless adapter to work.

I'm using XBMC Live 9.11, which I believe is based on ubuntu micro.

The output of lspci:

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

the output of ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:6a:b4:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-06-4F-6A-B4-20-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

my /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
wireless-essid   ROUTERM
wireless-key     09FCDEA805
wireless-channel 8
wireless-mode    managed


And yet, when I run dhclient, I can not get a lease for an IP from my router. Neither networking from wlan is working.

Is there anything else I should do?

---

### Post by viniciuscarvalho on 2010-02-09
Just bumping up, still struggling against this. Anyone please?

---

