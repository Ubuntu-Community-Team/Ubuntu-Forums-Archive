---
title: "How to connect two pc with lan for internet access"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by shadhin on 2013-07-20
I have two computers, the first computer (PC1) have two network cards,  the first network card (ethernet 0) is connected to a broadband(DSL). The  second network card (ethernet 1) is connected to the second computer  (PC2). My problem is, how to configure the two computers (PC1 & PC2)  that PC2 can access the internet? Please help. Thanks.

---

### Post by praseodym on 2013-07-20
Create a new profile in the network-manager of the first PC naming it somehow. For the _regular_ eth0 interface choose "Automatic DHCP" for the second profile for eth1 "together with other ...". For the second profile you need the MAC address of the interface:
```

ifconfig eth1
```
Add it, too.

On PC2 choose "Automatic DHCP"

---

### Post by anspectrum on 2013-07-20
> **shadhin said:**
> I have two computers, the first computer (PC1) have two network cards,  the first network card (ethernet 0) is connected to a broadband(DSL). The  second network card (ethernet 1) is connected to the second computer  (PC2). My problem is, how to configure the two computers (PC1 & PC2)  that PC2 can access the internet? Please help. Thanks.

You have not mentioned which operating system you are using. It could be MS / Linux/ Mac etc etc. 
Anyhow, For

Windows:

You need to enable routing services through Control Panel---->>Administrative Tools---->>> Services
Then you need to share the connection that is connected to the DSL modem.

Linux:

You need to use IP Tables to redirect traffic from one Ethernet (Connected to DSL modem) to the other ethernet (connected to the PC2) and the other way round. Also you will be required to use NAT translations to get the traffic from Ethernet 2( connected to PC2) to Eth-1 (connected to DSL) and to get it back.

This is the basic idea of doing it. Please search for actual commands to accomplish this depending on your OS.

---

### Post by shadhin on 2013-07-20
thanks. I'm using Ubuntu 13.04 64 Bit.

---

### Post by david83 on 2013-07-30
Isn't it better to place a router in between?
In this situation pc1 should always be powered on to get internet towards pc2

---

### Post by david83 on 2013-07-30
Isn't it better to place a router in between?
In this situation pc1 should always be powered on to get internet towards pc2

---

### Post by gordintoronto on 2013-07-30
+1 for the router. Last week I bought a router at Goodwill, for $0.80. It's not state of the art, but it's a better and simpler solution than PC2 going through PC1 to the Internet.

---

### Post by kurt18947 on 2013-07-30
+2 for a router, there are several advantages.  Gordon, stressing the budget are we? :D

---

### Post by sammiev on 2013-07-30
+3 for a router, saves a little work and a little on power as only one computer needs to be on.

---

