---
title: "wifi n/w connected but no internet access"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by pvnvk on 2012-12-07
Hi,

The situation I am in is a bit tricky. I am able to connect to my wifi router from my laptop but am not able to access internet. I had been using internet from the same modem and have no idea what suddenly went wrong. Three of my friends are still accessing internet from the same modem and have no problems.

I even tried to access internet from windows but again the same problem , am getting connected to the wifi network but cant access internet. 

I have tried to ping my friends connected to the wifi network and also accessed the modem using wifi during which there were no problems.

Then I tried accessing internet by connecting to the modem/router using LAN cable instead, doing which I could access internet.

Please do help me out with the wifi internet problem

---

### Post by aromo on 2012-12-07
If you can ping your friends and access the modem it means that your local network is ok.
Please post the output of
```
ifconfig
```
```
nslookup ubuntuforums.org
```
and
```
sudo traceroute 8.8.8.8
```

---

### Post by pvnvk on 2012-12-08
> **aromo said:**
> If you can ping your friends and access the modem it means that your local network is ok.
Please post the output of
```
ifconfig
```
```
nslookup ubuntuforums.org
```
and
```
sudo traceroute 8.8.8.8
```
The following is the output for ifconfig with wifi connection:

eth0      Link encap:Ethernet  HWaddr 00:22:64:54:9f:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1375451 (1.3 MB)  TX bytes:257796 (257.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28490 (28.4 KB)  TX bytes:28490 (28.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:17:04:ac  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fe17:4ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10360 (10.3 KB)  TX bytes:20578 (20.5 KB)







The following is the output for nslookup ubuntuforums.org :


Server:        127.0.1.1
Address:    127.0.1.1#53

Non-authoritative answer:
Name:    ubuntuforums.org
Address: 91.189.94.12



The following is the output for the sudo traceroute6 8.8.8.8 :

traceroute: unknown host 8.8.8.8


The sudo traceroute 8.8.8.8 resulted in command not found .... traceroute6 worked out although

---

### Post by aromo on 2012-12-10
DNS seems to be working fine.

However your routing seems off as you should be able to trace route to 8.8.8.8.  Is there any particular reason you're using IPv6?  If not, I would disable it.

Does your router have a firewall or something?

Please post the output of ```
ping 8.8.8.8
``` and ```
sudo route -v
``` to check your routing.

---

