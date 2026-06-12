---
title: "wireless disconnection after every 20 - 30 minutes or so."
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by erick3 on 2013-08-25
Hello all...
 I am running a custom system running 64bit 13.04 and it seems like every 20 - 30 minutes or so I am getting disconnected from the router. I still show a strong signal, but no traffic. When I try to access my network using my phone, there are no issues. Not sure where the problem can be at right now and looking for some help.

Some info from the sticky...
lsusb - 
Bus 001 Device 012: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]

ifconfig
wlan0     Link encap:Ethernet  HWaddr 1c:7e:e5:13:ff:56  
          inet addr:192.168.1.93  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e7e:e5ff:fe13:ff56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:9 overruns:0 frame:0
          TX packets:143 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22035 (22.0 KB)  TX bytes:28120 (28.1 KB)



iwconfig
IEEE 802.11bgn  ESSID:"xxxxxx"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 74:D0:2B:D0:B9:90   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=73/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -C network
description: Wireless interface
       physical id: 1
       bus info: usb@1:1.3
       logical name: wlan0
       serial: 1c:7e:e5:13:ff:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.93 multicast=yes wireless=IEEE 802.11bgn


Thanks for any help.

---

