---
title: "can't use static ip on dhcp server"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by Baruch on 2010-08-17
Hello.
I have 2 Ethernet connections, one (eth0) for the internet which gets set with dhcp, and one (eth1) for my internal network on which I have dhcp3-server running. I set eth1 to use static IP in interfaces, but every time I reset the network, it is fine for a couple of minutes, and switches over do being served by my own dhcp server on the same machine. Why dos this happen? (the interfaces file clearly says "iface eth1 inet static")

---

### Post by Rhemat on 2010-08-17
Heya,
I hate to ask this, but did you specify a static IP address, or did you just state [iface eth1 inet static]?  If you did specify an IP address, is it one that is in your DHCP pool?  If it is, then you will have to assign a different one.  For example, if you told your DHCP server to hand out 50 addresses, and to start from 128, then any address beyond 128 is taken.
I hope this helps.

---

### Post by Baruch on 2010-08-17
> **Rhemat said:**
> Heya,
I hate to ask this, but did you specify a static IP address, or did you just state [iface eth1 inet static]?  If you did specify an IP address, is it one that is in your DHCP pool?  If it is, then you will have to assign a different one.  For example, if you told your DHCP server to hand out 50 addresses, and to start from 128, then any address beyond 128 is taken.
I hope this helps.

Nope.
I specified everything except for a gateway (this computer is itself the gateway for the internal network), and the static address is on the network, but not in the dhcp pool.
Thanks anyway.

---

### Post by Iowan on 2010-08-17
Was eth1 *ever* set for DHCP (in Network Manager, maybe)? Almost sounds like an old lease renewing itself. I'll need to search for where the client's DHCP leases are kept

---

### Post by Baruch on 2010-08-18
> **Iowan said:**
> Was eth1 *ever* set for DHCP (in Network Manager, maybe)? Almost sounds like an old lease renewing itself. I'll need to search for where the client's DHCP leases are kept
I don't think so, but I'm not sure. This is in Virtualbox and I was messing around with different types of network configurations and "attaching" different types of networks. It is a server installation. Is Network Manager installed by default in servers?

---

### Post by Baruch on 2010-08-18
Thanks, Iowan. suggesting that it was an old lease renewing itself helped. I just reset the machine and it solved the problem. My only question is why doing "sudo /etc/init.d/networking restart" didn't help?

---

### Post by dmizer on 2010-08-18
You said that it works for a short time, and then stops working as expected. Please post the output of ifconfig during both situations.

Edit ...
You mentioned the interfaces file. Have you uninstalled network-manager? Network-manager and /etc/network/interfaces conflict with eachother.

---

### Post by Baruch on 2010-08-18
> **dmizer said:**
> You said that it works for a short time, and then stops working as expected. Please post the output of ifconfig during both situations.
Sorry, can't do that since the problem was solved (see above), but what I was getting was an IP of 10.1.1.1 for the first 3 minutes, and "router" only showed one default gateway (for eth0). Then, after 3 minutes ifconfig would show an IP of 10.1.1.60 (my first IP in the dhcp pool), and "router" would show _*two*_ default gateways, one for each interface. This of course wolud whack up my internet, and I would have to run "router del default gw 10.1.1.1" (somthing like that, I don't remember it exactly) to get it to work for another 3 minutes.

---

