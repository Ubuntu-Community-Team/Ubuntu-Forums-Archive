---
title: "connecting to the net with Jaunty"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by brotell on 2009-07-24
I have currently Jaunty on dual boot with xp my problem is as follows I use a Maxon bp3-ext which is a mobile modem that attaches via a usb connection, with xp I just use my supplied cd and then login, with Ubuntu I have no net.
When I type lsusb I get
Bus 003 Device 002: ID l6d8:6280 CMOTECH Co., Ltd CMOTECH CDMA Technologies USB modem
What options are availible to me to get my net working with Ubuntu, remembering that I have to use another computer to follow any instructions.

Thanks In advance
Terry

---

### Post by superprash2003 on 2009-07-24
post output of ifconfig from the terminal ,are you able to access your modem via http?

---

### Post by brotell on 2009-07-24
eth0      Link encap:Ethernet  HWaddr 00:16:e6:66:b1:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:12400 (12.4 KB)  TX bytes:12400 (12.4 KB) 
unable to use net in any form from jaunty

---

