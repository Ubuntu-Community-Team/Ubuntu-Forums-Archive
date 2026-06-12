---
title: "help with iptables"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by ulao on 2012-09-19
I'm looking to block traffic from an ip to facebook.

Was thinking this
iptables -A OUTPUT -s 192.168.0.27 -p tcp -d facebook.com -j DROP

didnt work, can anyone help?

---

### Post by Doug S on 2012-09-20
One problem is that facebook uses many servers and IP addresses and it is not clear (at least to me) which IP address will end up being used if one tries to access [www.facebook.com]("http://www.facebook.com"). For an iptables solution, you might need to drop packets destined for any facebook owned IP address.
I also think your rules would have to bo added to the FORWARD chain, not the OUTPUT chain.
Perhaps something like this (where I am trying to block 192.168.111.100 from accessing facebook):```
$IPTABLES -A FORWARD -i $INTIF -s 192.168.111.100 -p tcp -m iprange --dst-range 66.220.144.0-66.220.159.255 -j DROP
$IPTABLES -A FORWARD -i $INTIF -s 192.168.111.100 -p tcp -m iprange --dst-range 69.63.176.0-69.63.191.255 -j DROP
$IPTABLES -A FORWARD -i $INTIF -s 192.168.111.100 -p tcp -m iprange --dst-range 69.171.224.0-69.171.255.255 -j DROP
$IPTABLES -A FORWARD -i $INTIF -s 192.168.111.100 -p tcp -m iprange --dst-range 204.15.20.0-204.15.23.255 -j DROP

```which gave this when an attempt was tried:```
Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       tcp  --  eth0   *       192.168.111.100      0.0.0.0/0           destination IP range 66.220.144.0-66.220.159.255
       0        0 DROP       tcp  --  eth0   *       192.168.111.100      0.0.0.0/0           destination IP range 69.63.176.0-69.63.191.255
      [COLOR=red]10      512 DROP[/COLOR]       tcp  --  eth0   *       192.168.111.100      0.0.0.0/0           destination IP range 69.171.224.0-69.171.255.255
       0        0 DROP       tcp  --  eth0   *       192.168.111.100      0.0.0.0/0           destination IP range 204.15.20.0-204.15.23.255

```Note: I have no clue if I got all of facebook IP addresses or not.

---

### Post by GeForce 9500GT on 2012-09-20
Did you read the [how-to's]("https://help.ubuntu.com/community/IptablesHowTo")? Here's [a page]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables") with almost the same info. And [another one]("http://linux.die.net/man/8/iptables"). Hope this will help you.

---

