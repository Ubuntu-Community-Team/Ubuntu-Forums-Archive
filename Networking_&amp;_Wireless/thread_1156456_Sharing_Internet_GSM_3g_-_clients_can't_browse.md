---
title: "Sharing Internet GSM 3g - clients can't browse"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by marciovinicius on 2009-05-11
Hi, i'm trying to make a simple Internet server with a GSM 3g minimodem (USB).
I got an old PC, I installed Xubuntu 9.04, I plugged the minimodem, it connected, I set up the network and created a simple script with the rules for iptables.

Everything seemed to work well, but the computers in network can't open any page on Internet. Skype works, updates of Avast work, but browsers can't read any simgle page. The computers in network use Windows XP Pro.

From internet server/router (xubuntu) I can ping Internet (i'm posting from it) and others computers in my network. From the computers I can ping xubuntu's ip but I can't ping anything from Internet.

Anyone can help me?

Here is the iptables script:
```
#!/bin/bash

# Limpando regras
iptables -F
iptables -t nat -F

# Roteando os pacotes
modprobe iptables
modprobe iptable_nat
iptables -t nat -A POSTROUTING -s 192.168.10.0/27 -o ppp0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

```

---

