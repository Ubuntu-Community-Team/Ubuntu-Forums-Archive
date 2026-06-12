---
title: "can detect wireless, but cannot connect."
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by habzone2007 on 2009-01-11
Hello,

I am trying to connect to my home wireless network. I can see my network in the list of wireless networks available, and the panel shows that all the bars are full (98% connectivity). It asks for pass phrase and when I supply it, it keeps asking it again & again and I Cannot access any web page. The same password & Encryption key works for another (windows) computer that I have.
Not sure what I am doing wrong. I am using Ubuntu Hardy Heron 8.04 and Intel PRO/Wireless 3945ABG for wireless (DELL Inspiron E1405).  Here's the output of ifconfig:


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:76:2f:2e  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe76:2f2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4066 errors:1 dropped:1 overruns:0 frame:0
          TX packets:3580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3525871 (3.3 MB)  TX bytes:535045 (522.5 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:d2:01:da:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154297 (150.6 KB)  TX bytes:166593 (162.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104011 (101.5 KB)  TX bytes:104011 (101.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-01-DA-03-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by tbj61898 on 2009-01-11
try to check router admin panel, you may find Access List filters enabled and in such case You need to 'enable' your machine.

Also: if you just installed linux check if you have correctly selected your keymap, try to write your password in a text editor and see if there are any typo in it.

Last: try to change encryption on your router. If it's WPA2 change it to WPA, or the opposite. If it's still WEP I suggest You to use WPA ;-)

---

### Post by habzone2007 on 2009-01-11
> **tbj61898 said:**
> try to check router admin panel, you may find Access List filters enabled and in such case You need to 'enable' your machine.
----------

ok...to access router admin panel, I did 192.168.1.1 in firefox and it showed a page of Basic setup for Linksys router. In that I see that DHCP is enabled. Now Can you tell me what it means by "enabling" my machine ?

>  Also: if you just installed linux check if you have correctly selected your keymap, try to write your password in a text editor and see if there are any typo in it.
--------
I have linux for the past year or so and I reset the router settings today. And I made sure the password has no typo in it.

>  Last: try to change encryption on your router. If it's WPA2 change it to WPA, or the opposite. If it's still WEP I suggest You to use WPA ;-)
--------------

I changed it to WPA personal.

---

### Post by tbj61898 on 2009-01-11
> **habzone2007 said:**
> ----------
ok...to access router admin panel, I did 192.168.1.1 in firefox and it showed a page of Basic setup for Linksys router. In that I see that DHCP is enabled. Now Can you tell me what it means by "enabling" my machine ?

I mean: certain routers lets you filter out devices by MAC address, so if this type of filtering is enabled your box can't connect to the router. You usually find it under "access list" or something similar. 
Does your router have a sort of "logging"? My old linksys could tell, by viewing logs, if some devices had troubles connecting.


> **habzone2007 said:**
> 
I changed it to WPA personal.

No luck with that?

In my experience I had this issue only once and it was due to certain configuration on the router. It has been a while but here's what I remeber, with some luck it may be of help.

Check if all wireless settings are set to default (DTIM beacon MTU). Set router mode "b & g" (instead of only b or only g, obviously assuming it's a b&g router), and set a channel in the "middle", like 6. The last one may seem exagerate but I once set an higher channel (like 12 or 13) and later discovered my linux box would not even see wireless network on that channel, probably due to difference with US/Canada/Europe wireless frequencies availability.

Check out dmesg, /var/log/messages or even /var/log/wpa_supplicant logs, you may find something interesting there, post them if you find something that sounds interesting.

---

### Post by habzone2007 on 2009-01-11
When I type iwconfig, it gives this:

laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr : off   Fragment thr=2346 B   
          Power Management : off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And a dmesg | grep iwl 

laptop:~$ dmesg |grep -i iwl
[   19.661677] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   19.661681] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   19.661845] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   20.294041] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   20.295001] wmaster0: Selected rate control algorithm 'iwl-3945-rs'


It can see the network but is not connecting to it *even* after I provide the correct password/encryption key.

Thanks

---

### Post by tbj61898 on 2009-01-11
Hey,
looks like someone has experience with that issue. Look [here]("http://ubuntuforums.org/showthread.php?t=753200").

I don't know if it's going to work... but it's worth giving it a try!

Good luck with that!

Andrè

---

