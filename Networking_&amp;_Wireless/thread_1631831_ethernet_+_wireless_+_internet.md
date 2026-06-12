---
title: "ethernet + wireless + internet"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by il_lele_ on 2010-11-27
Hi all, sorry for my bad english.

I have a notebook with ubuntu 10.04 and I use NetworkManager to connect with a network.

I want connect wireless and ethernet together, the wireless network give me access to Internet. 

I'm able to connect ethernet and wireless togheter, but when I activate the ethernet interface, I lose Internet connection. When I deactivate eth0, the Internet connection returns.

eth0      Link encap:Ethernet  HWaddr ----------------------
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: ------------------------------- Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5708 errors:1 dropped:0 overruns:0 frame:0
          TX packets:9291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2681548 (2.6 MB)  TX bytes:3781313 (3.7 MB)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr ------------------------------
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ------------------------- Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:20856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19076796 (19.0 MB)  TX bytes:2829063 (2.8 MB)


So, if I'm connected to wireless I can navigate on Internet, just plug in ethernet, the connection remains, but I do not have access to the Internet (not just a DNS issue, because even not ping the ip of google) . 

Can you help me?

Lele

---

### Post by grahammechanical on 2010-11-27
This is my ifconfig listing

> eth1      Link encap:Ethernet  HWaddr 00:1a:92:82:d4:32  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe82:d432/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48257 (48.2 KB)  TX bytes:14760 (14.7 KB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe0e:9be0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3745413 (3.7 MB)  TX bytes:546144 (546.1 KB)

As you can see, like your system, both ethernet and wireless are UP and RUNNING.

Wlan0 connects automatically at boot up. I click on eth1 and it gets connected. I have just done this while accessing this forum and I am not disconnected from the internet. I can access sites other than this one. I keep my ethernet cable plugged in all the time.

I notice that you do not have a inet6 addr. Did you blank it out? 

Both of your connections have an inet addr and they are different. Your are connected to the router by both connections as I am. I also notice that the Bcast address is different. This is not the case on my system. Is this the problem? I do not know.

regards.

---

### Post by il_lele_ on 2010-11-27
Thanks for your reply.
Maybe you are connected to the same LAN (router).
I connect my notebook to two different router: 
- wireless: to connect in Internet (ip address 192.168.1.1)
-ethernet: to connect another LAN (ip address 192.168.0.1)

But when I'm connected togheter I loose the Internet connection (only the Internet connection).

---

### Post by il_lele_ on 2010-12-02
up

---

