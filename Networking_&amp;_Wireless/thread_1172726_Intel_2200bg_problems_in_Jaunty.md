---
title: "Intel 2200bg problems in Jaunty"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by BluesLinux on 2009-05-28
Just upgraded to 9.04. Wireless card, which was a problem at first in 8.10, stopped working. I've tried lots of different suggestions from this site and others to no avail. Have got it showing up as if it's working in iwconfig and in wicd, but can't ping or browse.

I'm using a Dell XPS M140 and my router is set to WEP. It's a Verizon FIOS router, and they don't like to let you turn off the WEP (I called their customer support; they wouldn't give me the password to get in to the router's settings).  

Any ideas?

Here are my results from iwconfig:

eth1      IEEE 802.11g  ESSID:"9FHM2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:90:EF:43:65   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-26 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:3468  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here's what ifconfig shows:
eth1      Link encap:Ethernet  HWaddr 00:16:6f:87:cf:fc  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe87:cffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:120 dropped:120 overruns:0 frame:0
          TX packets:1 errors:0 dropped:72 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:716 (716.0 B)
          Interrupt:17 Base address:0xc000 Memory:dfbfd000-dfbfdfff 

Still can't ping or browse the internet. Can't even ping my router. See below:

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
, pipe 3

---

