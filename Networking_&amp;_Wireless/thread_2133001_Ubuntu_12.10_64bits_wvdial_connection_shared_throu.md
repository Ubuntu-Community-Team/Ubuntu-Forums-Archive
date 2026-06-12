---
title: "Ubuntu 12.10 64bits: wvdial connection shared through NAT resets and reconnect"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by vladiastudillo on 2013-04-06
Hi all, I'm having this problem: I'm sharing my wvdial modem connection through NAT configuration with these commands:

  $ sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE 
$ sudo sysctl -w net.ipv4.ip_forward=1 
$ sudo wvdial   

I have set the gateway and DNS servers in the client's lan and  everything seems to work fine for a few seconds, but the wvdial  connection starts to reset and reconnect automatically every second,  with every packet request (i'm guessing).

  Do I have to adjust the pppd options? 
Am I setting the NAT's configurations wrong?

Any help I will appreciate, thanks in advance.

---

