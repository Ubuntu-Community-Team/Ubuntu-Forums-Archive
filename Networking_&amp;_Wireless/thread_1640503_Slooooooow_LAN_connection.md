---
title: "Slooooooow LAN connection"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by NJC on 2010-12-07
This is a recent problem, and I can't pinpoint any change/upgrade that would cause this. Rsync transfer from Client to Server:

> sent 11756196 bytes  received 1032741 bytes  138258.78 bytes/sec
total size is 144333466390  speedup is 11285.81Pinging back and forth from each machine is fine. No Ifconfig errors Client, but Server has RX packet errors.

> eth0      Link encap:Ethernet  HWaddr 00:11:25:37:ee:44  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe37:ee44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41786 errors:2157 dropped:0 overruns:0 frame:2157
          TX packets:34138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55615449 (55.6 MB)  TX bytes:4737538 (4.7 MB)
What's the next step?

---

### Post by WinstonChurchill on 2010-12-07
> **NJC said:**
> This is a recent problem, and I can't pinpoint any change/upgrade that would cause this. Rsync transfer from Client to Server:

Pinging back and forth from each machine is fine. No Ifconfig errors Client, but Server has RX packet errors.


What's the next step?
What kind of switch are you using? Or are the machines directly connected? Is this megabit or gigabit Ethernet? What class cable (CAT5/CAT5e/CAT6/etc - it will be printed somewhere on the cable) are you using? Do you have the same issue with different client machines connecting to that same server? How old are the NIC's in the machines?

---

### Post by NJC on 2010-12-07
Connected via old Linksys router (100mbit?), CAT5 cable. I'm guessing 2 and 6yr old NIC and only 2 machines on LAN. Thanks for your help. :)

---

### Post by WinstonChurchill on 2010-12-08
> **NJC said:**
> Connected via old Linksys router (100mbit?), CAT5 cable. I'm guessing 2 and 6yr old NIC and only 2 machines on LAN. Thanks for your help. :)
Do you have a laptop or something around you can test the server again with? I'm inclined to think it's a problem with the client machine's NIC. Maybe try a different Ethernet plug on the router, but that's a long shot.

---

