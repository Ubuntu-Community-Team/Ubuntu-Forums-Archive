---
title: "subnet routing to MS SQL 2k with ubuntu DHCP server"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by lavdate on 2006-01-17
i have 2 subnets on networks (WinXP clients): RoomA 192.168.0.0/24 and RoomB 192.168.1.0/24 .
i also have an MS SQL 2000 server (192.168.0.1) in RoomA.
i have an ubuntu with eth0 (192.168.0.2) attached to 192.168.0.0/24 and eth1 (192.168.1.2) attached to 192.168.1.0/24.
i separate them to make workgroup isolation between rooms and try to make ubuntu as router between rooms.

all i want to do is.. how to make ms sql 2k clients in RoomB connected to mssql2k server in RoomA, routed via ubuntu?

i have tried:
```

#iptables -A FORWARD -s 192.168.1.0/24 -i eth1 -d 192.168.0.0/24 -p tcp --dport 1433 -j ACCEPT
#iptables -A FORWARD -s 192.168.1.0/24 -i eth1 -d 192.168.0.0/24 -p udp --dport 1433 -j ACCEPT

```

but the sql clients in RoomB still not connected to mssql2k server in RoomA.

i`m sorry for noobz question, did i missed something?

thank you in advance :)

---

### Post by Lambert on 2006-01-17
In your sitiuation, not sure if this is the answer but turn on ip_forwarding

/etc/sysctl.conf

Should look like this.

# Uncomment the next line to enable packet forwarding for IPv4
net/ipv4/ip_forward=1

---

### Post by lavdate on 2006-01-18
thank you for quick reply, i`ll try as soon as i reach my ubuntubox :)

---

### Post by lavdate on 2006-01-19
still got the problem, i can`t see any line contains "#net/ipv4/ip_forward=1" in my /etc/sysctl.conf

i heard that ip_forwarding was not enabled by default kernel configuration. is that mean i must recompile kernel?

i have just simply add "net/ipv4/ip_forward=1" in /etc/sysctl.conf but the subnet still can`t reach mssql2k server.


thank you for kind help :)

---

### Post by cwaldbieser on 2006-01-19
[QUOTE=lavdate]still got the problem, i can`t see any line contains "#net/ipv4/ip_forward=1" in my /etc/sysctl.conf

i heard that ip_forwarding was not enabled by default kernel configuration. is that mean i must recompile kernel?

i have just simply add "net/ipv4/ip_forward=1" in /etc/sysctl.conf but the subnet still can`t reach mssql2k server.


thank you for kind help :)[/QUOTE]
```

$ sysctl net 2>&1 | grep ip_forward
net.ipv4.ip_forward = 0

```
This shows that ip_forwarding is turned off.  You can turn it on by setting it to 1.

---

### Post by Lambert on 2006-01-19
After making the change try running this command to see if it helps.

```
sudo sysctl -p 
```

Also post your routing table here.

```
sudo route 
```

---

