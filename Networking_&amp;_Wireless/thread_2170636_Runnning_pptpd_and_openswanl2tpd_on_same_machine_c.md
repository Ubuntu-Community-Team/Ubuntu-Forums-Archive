---
title: "Runnning pptpd and openswan/l2tpd on same machine creates routing issues"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by fazz2 on 2013-08-27
Hey all, 
I successfully set up both methods on Ubuntu precise. pptpd assigns 192.168.0.xx and openswan assigns 192.168.2.xx addresses to hosts. Pptpd worked for months now and I decided to add openswan. 

My problem now is that openswan connections work without problems, but the pptpd traffic is not routed anymore. If I open a pptpd and an openswan connection, this is the routing info:
```
[FONT=lucida console]Kernel IP routing table
Destination     Gateway         Genmask          Flags Metric Ref  Use Iface
default         static.xx-xx    0.0.0.0          UG    100    0    0   eth0
<ext IP>        static.xx-xx    255.255.255.248  UG    0      0    0   eth0
<ext IP>        *               255.255.255.248  U     0      0    0   eth0
192.168.0.100   *               255.255.255.255  UH    0      0    0   ppp1
192.168.2.2     *               255.255.255.255  UH    0      0    0   ppp0[/FONT]
```

When I drop the connections, and execute
```
[FONT=arial][COLOR=#333333]iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE[/COLOR]
iptables -A FORWARD -p tcp --syn -s 192.168.0.0/24 -j TCPMSS --set-mss 1356[/FONT]
``` pptpd works again. Unitl I dial in with openswan. 

Basically, I want that both ppp0, ppp1 ... pppx to be forwarded to eth0 at the same time. How should I adapt the routing info to reflect this? Can I do it with iptables? 

Thanks!

---

