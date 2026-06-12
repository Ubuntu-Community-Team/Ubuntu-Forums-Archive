---
title: "Upgraded Dell Inspiron 1420 to 10.4 and wireless connection constantly dropping"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by dano73 on 2011-02-17
I'm a novice so hope someone can help. I recently upgraded to 10.4 and cannot get wireless to stay connected for more than a few seconds before it drops or asks me to re-enter my password. Usually re-entering the password does not help. I see my wireless network and a bunch of others in my building but just cannot get a persistent connection. 

I believe this is the card:
*Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection*

ifconfig lists the following:
[I]eth0      Link encap:Ethernet  HWaddr 00:1e:c9:03:d9:c9  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe03:d9c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36105 errors:2 dropped:0 overruns:0 frame:0
          TX packets:23451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47534856 (47.5 MB)  TX bytes:3014437 (3.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34660 (34.6 KB)  TX bytes:34660 (34.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:aa:0d:b8  
          inet6 addr: fe80::21c:bfff:feaa:db8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1216503 (1.2 MB)  TX bytes:514415 (514.4 KB)[/I]

I went into bios and all the wireless settings appear to be enabled. Any help would be appreciated thanks!

---

### Post by dano73 on 2011-02-18
Also seems to be losing the wired connection at times now. I'm ready to buy a new laptop...

---

### Post by dano73 on 2011-02-23
Okay this is solved thanks to a couple of other posts I came across. In another thread on here someone suggested uninstalling network manager and installing wcid. I did this and I got my wired connection back and it stopped dropping every 30 seconds or so.

Problem, still could not connect to my wireless connection. Wcid kept telling me my wpa2 password was bad. I searched on this and found a thread on another site where the following was suggested. I guess Network Manager wasn't completely uninstalled:

                 *Got bitten by this bug (bad password) after upgrading a machine from Ubuntu 9.10 to 10.04. It reinstalls network-manager.*
 [I]Steps to fix in a terminal:
sudo aptitude remove network-manager
sudo /etc/init.d/wicd restart[/I]
 *Hit the tray icon and connect to a wpa2 network of your choice.*


View the full thread at:
[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)

---

