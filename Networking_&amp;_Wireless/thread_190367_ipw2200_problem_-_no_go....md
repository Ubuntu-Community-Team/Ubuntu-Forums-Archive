---
title: "ipw2200 problem - no go..."
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Ingwar on 2006-06-06
I have Ubuntu Dapper with latest updates and bunch of other network related programs installed. My wired connection works fine but my wireless doesn't. No matter what I do I can't get it working. My router Netgear WGR614 works fine, I am able to connect wirelessly from another laptop. The wireless connection is WAP-PSK. I have tried all possible Howtos under the sun and yet it doesn't help. Would anybody knowledgable be so kind to walk me through this and help get it back to working (it did at one point). I am just about a month into Ubuntu, so, make it as simple as possible, please. 
My NetworkManager icon shows "No network connection" although I am LAN connected right now. The ipw2200 card is working, here is the ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:15:00:33:BA:42
          inet6 addr: fe80::215:ff:fe33:ba42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15555 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0xc000 Memory:cdeff000-cdefffff

eth1      Link encap:Ethernet  HWaddr 00:0E:7B:C4:90:95
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7bff:fec4:9095/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31126693 (29.6 MiB)  TX bytes:29030581 (27.6 MiB)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9950 (9.7 KiB)  TX bytes:9950 (9.7 KiB)


Thanks.

---

### Post by Ingwar on 2006-06-06
Help, please!!!

---

### Post by monkeyhelper on 2006-06-06
apt-get remove network-manager
- add eth1 back into /etc/network/interfaces
-apt-get install wifi-radar
- add wifi-radar to your panel to manage connections

network-manager isn't ready for the primetime yet :

[http://ubuntuforums.org/showthread.php?t=187571](http://ubuntuforums.org/showthread.php?t=187571)

---

### Post by Ingwar on 2006-06-06
MAN, you ROCK!!! This is awesome! After spending hours of reading all the stuff in forums you give me this simple solution and kaboom - it works... Thank you so very much, God bless, you!
=D>  :KS  :KS  :KS  :KS  :KS  =D>

---

