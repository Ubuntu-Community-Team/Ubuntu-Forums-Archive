---
title: "No valid active connections found! 8.10"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by rldwallace on 2009-04-01
Hey o' great gurus of Ubuntu,

I don't understand it! I seem to get very good internet connection, but the networking icon in the taskbar indicates "No valid active connections found!" How can dis be?

eth0      Link encap:Ethernet  HWaddr (mac of my nic)  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: (unfamiliar with this so removed until told it's perfectly safe to share) Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1959123 (1.9 MB)  TX bytes:415042 (415.0 KB)
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6559794 (6.5 MB)  TX bytes:6559794 (6.5 MB)

pan0      Link encap:Ethernet  HWaddr da:(mac)  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

When I ping with "Network Tools" I can't hit outside my network...but yet, Firefox etc. works fine.

What the heck is going on?

David

---

### Post by freonchill on 2009-04-01
the error is talking about "profiles" that network manager uses - if you left click and choose a connection.

see this - [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606)

---

### Post by rldwallace on 2009-04-01
> **freonchill said:**
> the error is talking about "profiles" that network manager uses - if you left click and choose a connection.

see this - [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606)

Thanks freonchill. Sorry for not doing a better job of searching this forum. I'll follow up on the other thread.

---

### Post by freonchill on 2009-04-01
no problem, i just searched google for your error

you make it easy by putting it in quotes.

---

