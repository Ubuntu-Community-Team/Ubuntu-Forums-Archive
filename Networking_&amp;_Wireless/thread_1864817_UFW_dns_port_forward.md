---
title: "UFW dns port forward"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by morvol on 2011-10-19
Hello.
I have a machine running ubuntu server and i have some virtual machines running on it. I installed ufw for my firewall and i want to be able to forward any request of port 53 to one of my virtual machine ( ip = 192.168.1.30 )

What i have done so far is:
Edit /etc/ufw/sysctl.conf to have:
```
net.ipv4.ip_forward=1
```

Added to the end of /etc/ufw/before.rules, after the *filter section:
```

*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
COMMIT
```

after that for the port forwarding i added to the /etc/ufw/before.rules:
```

*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
-A ufw-before-forward -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m state --state NEW -i eth0 -d 192.168.1.30 -p tcp --dport 53 -j ACCEPT
COMMIT
```

And to the end of the /etc/ufw/before.rules i added :
```
*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -i eth0 --dport 53 -j DNAT --to-destination 192.168.1.30:53
COMMIT
```

After all that i nmap my server and i get that 
```
PORT   STATE  SERVICE
53/tcp closed domain

```

Also i need to mention that my dns works perfectly from my local machines.

Any ideas of what else i must fix or configure?

---

