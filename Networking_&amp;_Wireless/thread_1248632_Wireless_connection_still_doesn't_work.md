---
title: "Wireless connection still doesn't work"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by Jaget on 2009-08-24
Hey, been trying to get my wireless connection to work on and off for about 3 weeks now. I seem to get a little further each time, but it still doesn't want to connect to any websites.

I'm on ubuntu 8.10 and it automatically recognised my wireless usb stick (Netgear MA11). First off i had some problems with my WEP key, but that was pretty easy to solve. After that when i was trying to connect my wireless card couldn't obtain an IP address, so i had to enter all the details manually. It still wouldn't connect, so i checked if my mac address was correct on the firewall on my router. It wasn't.

Added the new mac address and now ubuntu finally tells me i am connected to the wireless network NETGEAR. The signal strength is shown to be about 75% full, but for whatever reason i still can't connect to the internet when i'm using it.

Here are the results from:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:12:3f:b4:0c:e3  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:feb4:ce3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2102302 (2.1 MB)  TX bytes:379911 (379.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1444 (1.4 KB)  TX bytes:1444 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:03:f8:09  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe03:f809/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22004 (22.0 KB)  TX bytes:4380 (4.3 KB)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"NETGEAR"  Nickname:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:58:35:F2   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=87/100  Signal level=-54 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

and ping [www.google.com](www.google.com)
```
ping: unknown host www.google.com

```

Can't remember if there's any other relevant information you guys need to know, so just ask.

And if you're wondering why i don't just use my ethernet connection, i need it for xbox live.

Any help would be much appreciated.

---

### Post by Bucky Ball on 2009-08-24
You're certainly connected. Are you running static IP or is the router acting as a DHCP server? If static, is 
192.168.0.13 the correct one? Figure so.

Is the wired connection fine?

---

### Post by Jaget on 2009-08-24
I'm using a static IP as when i tried to use DHCP it wouldn't obtain an IP address. I'm sure its the correct IP address as its the same onemy brother uses when he connects with his nintendo DS.

I'm using the wired connection right now without a problem.

---

### Post by Bucky Ball on 2009-08-24
Okay, not sure if 8.10 has System->Administration->Network, but if so, get in there and check you have all the correct details. You should have 'Enable Roaming' off, static IP 192.168.0.13, the mask should come up automatically, and the IP of your router should be the gateway. That IP could be wrong if you can ping a machine in your LAN but not get on to the WAN.

You need the router IP to configure the router usually. You might want to have a *look* at how the wireless section is set-up and report back, but if other wireless devices are working fine with it, I wouldn't go there.

---

### Post by Jaget on 2009-08-24
Yeh i've checked it a couple of times now with my ds, my brothers and my sister's laptop (running windows) and its definitely the right IP.

---

