---
title: "Network issues...  *stumped*"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by VoodooSmurf on 2006-07-11
Problem: At work (hampton inn) we have a wireless connection for the internet.  I have wireless at my house and at another hotel i visit often (sleep inn).  Wireless works at 2 of the 3 places (house and sleep inn).  

ifconfig wlan0:

Link encap:Ethernet  HWaddr 00:oc:41:CD:68:E8
inet addr:172.16.3.34  Bcast:255.255.255.255 Mask:255.255.255.0
inet6 addr:fe80::20c:41ff:fecd:68e8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets: 2622 errors:0 dropped:0 overruns:0 frame:0
TX Packets: 61 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:301316 (294.2 KiB)  TX bytes: 6324 (6.1 KiB)
Interrupt:10 Base address:0x3400


I can ping URLs but no URL access...  Works fine at my home and sleep inn, just not at my work...  anyone know what the problem could be?

Oh and i just got ubuntu yesterday and pretty new to linux systems...  i'm a newb at this.

---

### Post by scxtt on 2006-07-11
hampton inn could be using key access (WPA? WEP? not sure, barely use wireless) and you don't have the right credentials ...

---

### Post by VoodooSmurf on 2006-07-11
well generally when someone comes here, they just have to put in a code when they run IE, then they have access to the internet... but i can't get to that page so i can log in.

---

### Post by VoodooSmurf on 2006-07-11
hampton inn doesn't have WEP i know that much.. :)

---

### Post by mips on 2006-07-12
Are they not using a proxy ?

---

### Post by VoodooSmurf on 2006-07-13
on the desk computers, yes, they go through a proxy...  but wireless is 6MBit DSL...

---

### Post by gratefultux on 2006-07-13
> **VoodooSmurf said:**
> well generally when someone comes here, they just have to put in a code when they run IE, then they have access to the internet... but i can't get to that page so i can log in.

Well, sounds like it's something microsoft related that they make you do.  Ask them how that page is written (i.e. Java Script)  They might also use something obscure (ActiveX comes to mind).  You should just be able to turn on support for whatever it is in firefox and then you should be able to put in the code and connect to the web.

I hope i understood that code thing correctly :???:

---

### Post by dakaling on 2006-07-14
> **mips said:**
> Are they not using a proxy ?

Hampton Inns are using Nomadix Hotspot Gateways. The page that asks for the access code is in java.

---

### Post by penguinman5237 on 2008-02-28
i actualy talked to the lady here today, im running vista on my pc and cause it will not work on vista, i have the same issue, if anyone knows anyway of connecting with vista that would be a great help

---

