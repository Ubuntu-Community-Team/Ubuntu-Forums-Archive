---
title: "What does the ifconfig data mean?"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by ltwinner on 2009-10-19
Here's what I get when I run ifconfig

eth0  
[SIZE=2]Link encap:Ethernet  HWaddr 00:24:21:9c:6f:70  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe9c:6f70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106519625 (106.5 MB)  TX bytes:13142060 (13.1 MB)
          Interrupt:251 Base address:0x4000


Obviously inet addr stands for internet address...but 192.168.1.11 is not my internet address. So what does it mean?.[/SIZE][SIZE=2]

And what do the following fields mean?
HWaddr
Bcast
Mask
inet6 addr
[/SIZE]

---

### Post by JKyleOKC on 2009-10-19
It means that you are connected to a router, which is translating your actual internet address into a "local" address in the 192.168.* range.

As for the others, HWaddr is your network card's hardware address, otherwise known as its MAC. This is a (supposedly) unique combination of bits intended to identify that card or chip as opposed to the millions of other cards in existence. Bcast is the broadcast address; servers use this to reach all the boxes on a system at the same time. Mask tells the network software how to detect the "network" part of the IP addresses; in your case it's 192.168.1 and your eth0 interface is host number 11 in that network. Finally, Inet6 addr is the interface's address for version 6 of the internet protocol, which is intended to address the fact that the world may be close to running out of unique addresses; it hasn't been widely adopted, though.

---

### Post by chili555 on 2009-10-19
> but 192.168.1.11 is not my internet address.But it most certainly is. You may have an external IP address, given to you by your internet service provider, but you are attached to a router or other access point. The router is the device with the external IP address. It hands IP addresses to the computers that are connected to it. Many consumer routers use internal addresses in the 192.168.x.x range.

Routers do network address translation, meaning that when computer x.11 asks for a web page, [http://www.google.com](http://www.google.com), for example, the router requests it from the internet. When it comes back, it routes the page back to x.11, the computer that requested it. Likewise, when computer x.15 asks for [http://ubuntuforums.org](http://ubuntuforums.org), it is requested and comes back and is routed to x.15. It is pretty much an electronic version of the post office.> And what do the following fields mean?
HWaddrHWaddr is the MAC address of your ethernet or wireless device. Each device has a unique number by which it may be identified. It is generally printed right on the device. In theory, your device, and therefor, your computer and you can be traced by law enforcement and others. 

I will leave the other questions to others.

Edit: Oops! Jim beat me to it!

---

