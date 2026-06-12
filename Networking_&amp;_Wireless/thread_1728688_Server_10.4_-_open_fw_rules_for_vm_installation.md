---
title: "Server 10.4 - open fw rules for vm installation"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by Switcher79 on 2011-04-14
Hello friends, 

i have an problem with my dedicated server ( Ubuntu 10.4 ). On it i have - in vmware player 3.1.4 - running win srv 2k8 and have for my project two fixed (static) ip adresses.

1. for the Ubuntu Server  ( 208.12.xxx.xxx )
2. for the Windows 2k8 Server ( 201.10.xxx.xxx )

The vmnet interface has the IP 10.10.20.1, the win2k8 Server using as the gateway and dns 10.10.20.1 and has ip 10.10.20.100. The LAN is 10.10.20.0/24.

network - 10.10.20.0/24
vmnet1 - 10.10.20.1
win2k8 - 10.10.20.100
w2k8 gw - 10.10.20.1
w2k8 dns - 10.10.20.1

I will connect the windows server with RDP at port 3389.

I can´t get connection from the windows to www and i can´t reach the windows over the second ip adress. So i need to open few firewall rules and routes to get the traffic. I have some help from my friends, but i haven´t success with it:

```

iptables -A FORWARD -i eth0 -o vmnet1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i vmnet1 -o eth0 -j ACCEPT
iptables -A FORWARD -j LOG
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -A FORWARD -i eth0 -o vmnet1 -p tcp --dport 3389 -j ACCEPT
iptables -A PREROUTING -t nat -i eth0 -p tcp -d 201.10.xxx.xxx --dport 3389 -j DNAT --to 10.10.20.100:3389


```I know, i must be near breakthrough, but i have no idea to resume this.

Can anyone help me plz? 
:(

---

### Post by Switcher79 on 2011-04-14
Can anyone help me plz?

I set an virtual interface:
```

ifconfig eth0:1 201.10.xxx.xxx netmask 255.255.255.0 up

```

But i have an problem when i set the rules:
```

iptables -A FORWARD -i eth0:1 -o vmnet1 -p tcp --dport 3389 -j ACCEPT
Warning: weird character in interface `eth0:1' (No aliases, :, ! or *).

```

:(:(:(

---

### Post by Switcher79 on 2011-04-15
Hello, i haven´t still solved the problem. Plz help !!! :-(

---

