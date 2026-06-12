---
title: "Madwifi lists wireless networks, but won't connect"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by space-cake on 2009-09-01
Hello,

I've installed Madwifi as described in [this post]("http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html"). I got it to list the available wireless networks, but it won't connect to any of them. Why's that?

---

### Post by space-cake on 2009-09-02
I also forgot to mention that Wicd lists the wireless networks only on boot, then they disappear when I hit refresh. Also, when I do 

iwlist scanning

I get that there are no available wireless connections found, although Wicd lists some. After I choose one from Wicd, it doesn't connect at all. 

I really have no idea what to do.

---

### Post by space-cake on 2009-09-03
So, the problem persists. I removed madwifi and installed ndiswrapper. The output is as follows:

iwconfig

[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]

ifconfig

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:1f:c6:3c:a2:7b  
          inet addr:192.168.1.3  Bcast:192.168.1.127  Mask:255.255.255.128
          inet6 addr: fe80::21f:c6ff:fe3c:a27b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23052 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:30848038 (30.8 MB)  TX bytes:2935726 (2.9 MB)
          Memory:feac0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34759 (34.7 KB)  TX bytes:34759 (34.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:8a:2a:e3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:fa9f0000-faa00000[/INDENT]

iwlist scanning

[INDENT]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results[/INDENT]

This is funny, because Wicd clearly shows, that there ARE wireless connections in range, both secured and unsecured. The problem is that I can't connect to either of them. It sticks at "Obtaining IP address..." and that's it. Then, when I try to scan once more via Wicd all wireless connections disappear from the list. 

Could this be a hardware problem?!

---

