---
title: "[Solved]Internet connection sharing"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by xxvirusxx on 2012-11-18
Hello,

I have two computers but I don`t have router (for now). First computer has Ubuntu 12.04 and second computer has Winodws XP.
I try using firestarter and selected **eth0** in the first, then **eth1** in the second box. (eth0 is for internet connection).

-**eth0** - has internet access and is set AutoDHCP
-**eth1** - conected to the second computer with xp.
-network card from XP is set to Auto

Also I try this (but I don`t know if is complete). In my exemple I try this

```
sudo ip addr add 192.168.0.1/24 dev eth1
sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT sudo iptables -t nat -F POSTROUTING sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables-save | sudo tee /etc/iptables.sav
iptables-restore < /etc/iptables.sav
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
net.ipv4.conf.default.forwarding=1 
net.ipv4.conf.all.forwarding=1
```

Ping work in Ubuntu computer but on XP I don`t have internet.

From here I try those commands. [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing).

So what I make wrong? Tks

---

### Post by ahallubuntu on 2012-11-18
~

---

### Post by xxvirusxx on 2012-11-19
Yes I know what is a crossover cable and I have crossover cable because it was make-it by me. If switch to Windows 7, second computer with XP has internet connection.

---

### Post by xxvirusxx on 2013-05-23
Solved.

Buying a router.

---

