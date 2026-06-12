---
title: "knetwork manager"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by danteuk on 2010-04-06
9.10 & 10.4beta1

For some reason knetworkmanager never sees my network card.
Previously it always DHCP'd an IP and worked, problem is that's not good I need it to be fix ( it's a small web server ) so I had to manually change the ip address from the command line(due to knetworkmanager showing nothing for wired) every time I rebooted or if the adsl router got rebooted then that too caused the ip to change to a dhcp one again.

I've just done an upgrade to 10.4(beta1) and now I don't even get a dhcp ip, nothing in resolv.conf and still knetworkmanager deny's all knowledge of a network card so I have to do this after a boot to get networked:
```

ifconfig eth0 10.1.0.11 netmask 255.255.255.0 up
route add default gw 10.1.0.2 eth0
echo nameserver 10.1.0.2 >> /etc/resolv.conf

```

Anyone got any ideas how to sort this ?

It's laptop (old Dell inspiron)

# dmesg | grep Eth
[    1.308763] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:e8:11:aa

---

### Post by dineshs on 2010-04-06
Have you tried this?
Right click on knetworkmanager icon-click edit connections-new connection-wired
select manual configuration and proceed

---

