---
title: "Troubleshooting OpenVPN"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by wazz3r on 2012-10-15
Hello.

I have an issue with my openvpn server. The clients can connect to it, but they can only reach the openvpn server and no other servers in the network.

Setup:
ubuntu server, 192.168.0.10
openvpn running in tun mode with ip range: 10.0.8.0/24
client with ip 10.0.8.5
mail server, 192.168.0.8

From openvpn I push a route 192.168.0.1/24 10.0.8.1
The mail server has a route 10.0.8.0/24 192.168.0.10

From the client I can ping the ubuntu server on both 192.168.0.10 and 10.0.8.1. From the mail server I can ping both 192.168.0.10 and 10.0.8.1, but from the client I can't ping the mail server.

I believe that that problem has something to do with that the traffic from the tun0 interface is not allowed over to the eth0 interface, but I have no idea where to start looking.

I've checked iptables but I can't find anything there that should block the traffic.
```
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Any ideas what could be wrong?

---

### Post by wazz3r on 2012-10-15
Found it, ip forwarding was not enabled.

Solved by:
```
sysctl -w net.ipv4.ip_forward=1 
```

---

### Post by TheFu on 2012-10-15
Glad you found the solution.
It would be very helpful to others if you marked this thread as "SOLVED." That is in the "Thread Tools" menu.  Hopefully, I won't get in trouble for this post.

---

