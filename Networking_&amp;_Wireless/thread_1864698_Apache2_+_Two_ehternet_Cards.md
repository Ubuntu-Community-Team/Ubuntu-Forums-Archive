---
title: "Apache2 + Two ehternet Cards"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by adoniasv on 2011-10-19
Hi !.

Sorry 4 my basic English.. but i will try to explain...

I tried to find the answer in many forums and google before posting.

I have a server connects to the oracle database over php and it works fine on intranet.

The problem starts when trying to connect to the Internet with another ethernet card.

If start first Eth1 works well from the intranet, but when I start Eth2 works only internet, fail intranet and php cant connect to OraDB2 OraDB1.

This is my /etc/network/interfaces (I cant use static ip, only dhcp)
[PHP]
# The loopback network interface
iface lo inet loopback

# Conection to Intranet
auto eth0
iface eth0 inet dhcp

# Conection to Internet
auto eth1
iface eth1 inet dhcp
[/PHP]

This is my /etc/resolv.conf

[PHP]
search server.com
nameserver dns1.eth1
nameserver dns2.eth1
[/PHP]

This is my /etc/dhcp3/dhclient.conf

[PHP]
request subnet-mask, broadcast-address, time-offset, routers, domain-name, host-name, ntp-servers;
prepend domain-name-servers dns1.eth1, dns2.eth1;
[/PHP]

Please Help me!!!

---

### Post by jonobr on 2011-10-19
I may be misunderstanding, but Im guessing you need to setup your ubuntu machine as a router.

[Here is the documentation for that]("https://help.ubuntu.com/community/Router")
What you going to have to watch for is that your ubuntu machine is going to change its ip address given its on DHCP, that will mean that the route to the DB will have to be updated for the clients on the 192 network.

Im thinking (and honestly I have not put a lot of thought into this) if it was me I would set both of the those interfaces to static ip addresses

---

### Post by adoniasv on 2011-10-19
Ok...

I will try...

Thxx 4 u fast reply!

---

### Post by adoniasv on 2011-10-21
Not works... :(

Any other Ideas Plz??

---

### Post by adoniasv on 2011-10-21
I try to use IpTables...

[PHP]
iptables -t nat -A POUSTROUTING -i eth1 -j MASQUERADE
iptables -A FORWARD -p tcp --dport 80 -d 172.x.x.x -j ACCEPT
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -d 190.x.x.x -j DNAT --to 172.x.x.x
[/PHP]

Now wok in localhost, buy not work on internet

---

### Post by adoniasv on 2011-10-23
Hey [jonobr]("http://ubuntuforums.org/member.php?u=197514")

pufff SOLVED w/ ** ip route**

[http://kindlund.wordpress.com/2007/1...utes-in-linux/]("http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/")

---

