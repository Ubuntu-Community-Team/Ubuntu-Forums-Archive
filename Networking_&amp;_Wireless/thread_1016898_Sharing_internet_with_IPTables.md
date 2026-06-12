---
title: "Sharing internet with IPTables"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Deathray on 2008-12-20
Hello everyone. I manged to create a wireless access point with airbase-ng. I have a dhcp daemon running which gives an ip of 10.0.0.100-200. The default gateway is 10.0.0.1 which is the ip address of the at0 interface which airbase-ng creates when creating an access point.
The domain name servers in dhcpd are OpenDNS, so I don't need to forward dns or run my own dns daemon.
So that is the wireless access point configuration. On the ethernet side, my computer uses eth0 to access ethernet with a default gateway and dns of 192.168.1.1 and eth0's ip is 192.168.1.2. How would I manage to share the internet on eth0 with the people that log onto my wireless accesspoint on at0? I'm guessing NAT will have to be used because the users on 10.0.0.0/24 will share the ip on eth0 (192.168.2.2)
I don't know much about iptables but found this.
Would that work in my situation?
```
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables -t nat -A PREROUTING -p udp -j DNAT --to 192.168.1.1
iptables -P FORWARD ACCEPT
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE

```

---

### Post by mpokrywka on 2008-12-20
Those rules will work, almost. All udp connections will be directed to 192.168.1.1, which is probably not what you want.
I strongly advise you to put your real dns address (192.168.7.1) in dhcp daemon configuration and remove this DNAT iptables rule.
Also, do not forget to enable ip_forwarding in /etc/sysctl.conf

---

### Post by Deathray on 2008-12-21
Why can't I just use OpenDNS? And what does the -udp statement actually do? What are the proper commands to make it work then (: ?

---

