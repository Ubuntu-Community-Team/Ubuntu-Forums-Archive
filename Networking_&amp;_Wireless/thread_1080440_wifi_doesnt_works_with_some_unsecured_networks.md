---
title: "wifi doesnt works with some unsecured networks"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by asarturas on 2009-02-25
There is strange issue with my pc these weeks. Administrators changed something and now I cannot get my internet working.

The interesting part is, that it works for someone, and don't for elses. For instance. I have vmware virtual mashine installed on my ubuntu, so, then I connect to this wifi (it is unsecured) it connects, but don't get any result (like in firefox - it says "looking up for ..."). And then I start my virtual machine while this wifi is connected - it simply works and does everything.

How can it be true? Maybe it is because of some driver issues for "Intel Corporation PRO/Wireless 2200BG" (my wireless card) for Ubuntu 8.10 (Kernel 2.6.27-11-generic, GNOME 2.24.1).

I tried google, but it is too rare (or general) question and given search results are useless.

I'm sure that someone also had this issue, so could you please be so king to say me how did you fix this?

Thank you very much.

---

### Post by superprash2003 on 2009-02-25
in the pc which has no internet.. go to the terminal and post outputs of following commands
1)ifconfig
2)iwconfig

---

### Post by asarturas on 2009-02-25
Now I have internet on my running VMWare Player virtual pc (Windows XP), and on a hosting computer (Ubuntu) it doesn't works. Outputs:

**arturas@laptop:~$ ifconfig**
[I]eth0      Link encap:Ethernet  HWaddr 00:13:ce:3d:20:59  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe3d:2059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16553 errors:0 dropped:6 overruns:0 frame:0
          TX packets:11763 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30515329 (30.5 MB)  TX bytes:5503090 (5.5 MB)
          Interrupt:17 Base address:0xe000 Memory:c8008000-c8008fff [/I]

eth1      Link encap:Ethernet  HWaddr 00:03:25:21:10:a7  
          inet6 addr: fe80::203:25ff:fe21:10a7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:504414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419968700 (419.9 MB)  TX bytes:268784078 (268.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6518777 (6.5 MB)  TX bytes:6518777 (6.5 MB)

**arturas@laptop:~$ iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.

[I]eth0      IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:E7:27:F2:C0   
          Bit Rate:24 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=76/100  Signal level=-53 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:6   Missed beacon:13[/I]

pan0      no wireless extensions.

---

### Post by superprash2003 on 2009-02-26
try to open [http://74.125.67.100](http://74.125.67.100) .. are you able to access your router?

---

### Post by asarturas on 2009-03-03
No, unortunately I also can't access direct IP addresses. I also was thinking that maybe it's just DNS issue, but unfortunately it's not.

I can't access router, because it's not mine - it's supplied by owner of a residence there I live now and it is used by many other people.

What next? Have you guys some suggestions?

For me it seems like some issues of drivers on ubuntu for my wireless card. Because Win XP from virtual mashine connects to this network perfectly (throw bridge). Can this suggestion be true?

---

### Post by superprash2003 on 2009-03-26
is the ubuntu able to ping xp?

---

