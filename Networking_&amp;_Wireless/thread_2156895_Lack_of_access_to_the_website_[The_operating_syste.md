---
title: "Lack of access to the website [The operating system XUbontu 13.04]"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by gr3g0ry on 2013-06-23
[SIZE=3][FONT=arial]Hi,
I installed Apache2 + PHP5 + MySQL, phpmyadmin. Everything works fine, but I can not get to my site from the outside. Also can not get in to the server via ssh on lan...

Maybe I should something to open on the firewall? Please help!

_**Introduced**__** changes**__**:**_ (Is it safe and good?)
/etc/init.d/firewall

# ustawienie polityki dzialania
iptables -P INPUT [/FONT][/SIZE][SIZE=3][FONT=arial]_**[SIZE=3][FONT=arial]ACCEPT[/FONT][/SIZE]**_
iptables -P FORWARD [/FONT][/SIZE][SIZE=3][FONT=arial]_**[SIZE=3][FONT=arial]ACCEPT[/FONT][/SIZE]**_
iptables -P OUTPUT ACCEPT
_**ADD:**_
# polaczenia nawiazane
**iptables &#8211;A INPUT &#8211;p tcp --dport 80 &#8211;j ACCEPT**



_**Original file:**_
/etc/init.d/firewall
```

# wlaczenie w kernelu forwardowania
echo 1 > /proc/sys/net/ipv4/ip_forward
# czyszczenie starych regul
iptables -F
iptables -X
iptables -t nat -X
iptables -t nat -F
# ustawienie polityki dzialania
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
# zezwolenie nna laczenie sie z naszym zewnetrznym ip po ssh

iptables -A INPUT -i lo -j ACCEPT
iptables -A FORWARD -o lo -j ACCEPT

iptables -A INPUT -s 0/0 -d 84.234.12.41 -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -s 0/0 -d 84.234.12.41 -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -s 0/0 -d 84.234.12.41 -p udp --dport 22 -j ACCEPT
iptables -A OUTPUT -s 0/0 -d 84.234.12.41 -p udp --dport 22 -j ACCEPT
# polaczenia nawiazane
iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED
iptables -A FORWARD -j ACCEPT -m state --state ESTABLISHED,RELATED
iptables -A OUTPUT -j ACCEPT -m state --state ESTABLISHED,RELATED
# udostepniaie internetu w sieci lokalnej
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -j MASQUERADE
iptables -A FORWARD -s 192.168.0.0/24 -j ACCEPT

```

[/FONT][/SIZE]

---

### Post by vipulkumar7 on 2013-06-23
Are you not able to access any website?

---

