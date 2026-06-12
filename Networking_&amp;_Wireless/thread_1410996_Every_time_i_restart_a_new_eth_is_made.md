---
title: "Every time i restart a new eth is made?"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by gunavara on 2010-02-19
Hello, 
every time i restart my pc new eth device is made in ubuntu 9.10 and i have to configure it every time with the ip/gw/dns etc. 
I have reached eth39 before i reinstalled ubuntu (downloaded latest from the website because i thought it was some bug or something). 
Please help me with this one i am sure it's something not really hard but i just don't know what is it and it's very annoying...

The network adapter is on board lan on a desktop computer, nothing special, it was fine in previous versions of ubuntu i didn't have any problems with it. 

Please help
--------------------------------------------------
~$ ifconfig
eth5      Link encap:Ethernet  HWaddr x: x: x: x: x: x  
          inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:x.x.x.x
          inet6 addr: x:: x: x: x: x/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59750247 (59.7 MB)  TX bytes:3588745 (3.5 MB)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14144 (14.1 KB)  TX bytes:14144 (14.1 KB)
--------------------------------------------------
(where the 'x' are the numbers, i just hide them)

---

### Post by viralmeme on 2010-02-19
> **gunavara said:**
> Hello, 
every time i restart my pc new eth device is made in ubuntu 9.10..
I get eth1 or eth0, this might help .. [iframe]("http://linux.die.net/man/8/ifrename")

---

### Post by Iowan on 2010-02-19
I've seen that in a couple of other threads (doubt I can find them). You can edit */etc/udev/rules.d/70-persistent-net.rules * to get rid of the extra copies - but that won't necessarily keep it from making more...

---

### Post by gunavara on 2010-02-20
Hey, thanks but can u guide me through the process? Or share some links where i can read about it?

---

