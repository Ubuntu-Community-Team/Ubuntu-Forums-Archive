---
title: "Forwarding (or static route) between 2 LAN's"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by darknight2183 on 2010-10-16
I'm running into an issue when trying to forward packets from one LAN to another for a specific IP address.

I've an server install of 10.04.1 that I'm using as a Internet Gateway/Firewall.  Here's the layout:

eth0 WAN using DHCP
eth1 LAN static
    address 192.168.100.1
    netmask 255.255.255.0
ath0 WLAN static
    address 192.168.200.1
    netmask 255.255.255.0

I've enabled forwarding of IPv4 in /etc/syscltr.conf; DHCP server is working and ALL computers are able to get to the internet.

What's not working is that I have a printer on LAN (192.168.100.2 statically set), that I want the wireless user's to be able to access.

I'm able to ping eth1 when connected to ath1 with a client PC, but I cannot ping 192.168.100.2 no matter what rules I set in IPtables.

I've:
accepted source 192.168.200.0 destination 192.168.100.2
forwarded source 192.168.200.0 destination 192.168.100.2

and messed with SNAT and DNAT but nothing seems to allow me to route to this host.

Any idea's would be appreciated. :)

---

### Post by darknight2183 on 2010-10-16
One other thing I forgot to mention:

$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.100.0   0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.200.0   0.0.0.0         255.255.255.0   U         0 0          0 ath0
24.15.x.x     0.0.0.0         255.255.240.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         24.15.x.x     0.0.0.0         UG        0 0          0 eth0

](*,)

---

### Post by cavalier911 on 2010-10-17
This has to work in **BOTH** directions (bidirectional).
I don't see a route or firewall rule for the printer **192.168.100.2** to ping reply to wireless subnet **192.168.200.0**.

```
route add -net 192.168.200.0 netmask 255.255.255.0 gw 192.168.100.1 eth1
```

```
iptables -A FORWARD -i eth1 -s 192.168.100.2 -d 192.168.200.0 -j ACCEPT
```

If you need more help post the output from:
```
iptables -L
``` 
```
route
```
```
cat /proc/sys/net/ipv4/ip-forward
```

---

