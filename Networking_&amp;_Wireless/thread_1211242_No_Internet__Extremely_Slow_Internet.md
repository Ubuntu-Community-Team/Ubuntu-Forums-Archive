---
title: "No Internet / Extremely Slow Internet"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by aghanim on 2009-07-12
First and foremost, I am a newb to ubuntu, but I've had some experience setting up a FreeBSD machine a few years ago. I've been running ubuntu for the past few months without any problems whatsoever.

A few days ago, I requested a bump-up in speed on my dsl. The next morning ubuntu wouldn't connect to the internet. It would get an ip from the router (D-Link WBR-2310) but nothing else. I wanted to do a traceroute, but apparently it isn't installed. It seems like a DNS issue, but torrents don't seem to work either. Pidgin connects sometimes.

Since I had requested the bump, I called my isp to make sure it wasn't because my line was being activated, they told me everything was fine. The tech (if you can call him that) told me to connect the modem to my comptuer directly. I did that but then realized that I would need some software to connect to the isp. I went to network connections and added a dsl connection with my username and password, but it didn't work, so I deleted it.

Here's the kicker: I am dual-booting vista and that side works perfectly.

---

### Post by scrooge_74 on 2009-07-12
Did you try putting the open dns servers directly on your configs?

I think to hook the adls directly you need to use ppp or something like that

---

### Post by superprash2003 on 2009-07-12
post output of** ifconfig **from the terminal

---

### Post by aghanim on 2009-07-13
eth0    Link encap:Ethernet  HWaddr 00:1d:60:19:10:6e  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe19:106e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:524519 (524.5 KB)  TX bytes:863402 (863.4 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4232 (4.2 KB)  TX bytes:4232 (4.2 KB)

---

### Post by superprash2003 on 2009-07-13
try using opendns servers - 208.67.222.222 and 208.67.220.220 .. if that doesnt fix it.. you could try modifying your MTU [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by aghanim on 2009-07-14
Okay, it looks like it wasn't a problem at all.. Aparently my modem was wonky and not connecting properly. After doing a few power-cycles, at the recommendation of a "Level 2 Tech" at my ISP everything ended up working fine. I wonder why the vista part was working fine though?

Thanks for all your help =)

---

