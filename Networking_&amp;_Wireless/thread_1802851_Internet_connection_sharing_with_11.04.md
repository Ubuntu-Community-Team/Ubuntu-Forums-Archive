---
title: "Internet connection sharing with 11.04"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by eeshking on 2011-07-12
Hi all,

I'm trying to share an internet connection from my Ubuntu laptop to my Windows desktop. I am receiving internet through wlan0 and am connecting to the desktop through eth0. System -> Preferences -> Network Connections -> [edit] Auto eth0 -> IPv4 Settings -> Shared to Other Computers has worked like a charm in the past, but recently this has been failing. Specifically, when I plug the ethernet cable into my laptop, I get a toast notification for "Connection established" immediately followed by "Disconnected"; these notifications alternate every few seconds (established, disconnected, established, disconnected, established, disconnected...) On the Windows side, I get an unhelpful "This connection has limited or no connectivity"

Like I said, this has worked perfectly in the past. I have no idea what is going wrong now. Any advice?

---

### Post by spiky001 on 2011-07-12
Can you ping through eth0 to the other pc```
ping ipaddress
``` Also when eth0 connected can you check ip of both machines see if they are on the same network e,g 192.xxx.xxx.xxx 10.xx.xx.xx

---

### Post by eeshking on 2011-07-12
My Windows machine says its IP address is 169.254.119.195 (subnet mask: 255.255.0.0); when I try pinging this address from the Ubuntu machine, nothing happens (no response). 

When I do ifconfig on the Ubuntu machine, this is what I get:

```

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:17:20:45  
          inet6 addr: fe80::92e6:baff:fe17:2045/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2502 errors:0 dropped:0 overruns:0 carrier:19
          collisions:0 txqueuelen:1000 
          RX bytes:47554 (47.5 KB)  TX bytes:618389 (618.3 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4887 (4.8 KB)  TX bytes:4887 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:5b:2d:8d  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe5b:2d8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10296076 (10.2 MB)  TX bytes:1888657 (1.8 MB)

```

---

### Post by spiky001 on 2011-07-12
Have you tried starting pc with eth0 already connected, Instead of connecting after it as started

---

### Post by eeshking on 2011-07-12
Yes, it makes no difference.

---

### Post by spiky001 on 2011-07-12
Has this just happend or have you just changed to 11.04

---

### Post by eeshking on 2011-07-12
It has worked with 11.04 before. It stopped working last Thursday afternoon; it worked in the morning, then I disconnected my laptop because I was going out somewhere, and when I brought it back, Internet connection sharing didn't work. I left for vacation on Thursday evening and I just got back this morning; I reconnected the laptop to the desktop via ethernet cable and it's still not working. No idea what the issue could be.

---

### Post by spiky001 on 2011-07-12
If it was working and no software has changed Maybe a cable problem or eth0 card. I was hoping Chlli might of added some help as well, he is very good with this

---

### Post by eeshking on 2011-07-12
All right then. Thanks for the help.

---

### Post by eeshking on 2011-07-13
Hey, it just started working again, as abruptly as it stopped. I reversed the ethernet cable, fooled around with some settings on the Windows box (static vs. automatic IP addressing) but then switched things back to normal. Then I restarted the Ubuntu box and everything was working again. I think I'll chalk this one up to hardware shenanigans.

---

