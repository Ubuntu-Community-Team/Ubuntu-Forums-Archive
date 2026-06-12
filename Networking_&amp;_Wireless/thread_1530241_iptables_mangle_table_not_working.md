---
title: "iptables mangle table not working"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by alex_max on 2010-07-13
Hello, 

I have noticed that DHCP Discovery packets are sent with DSCP 4 which, as I understand it, cannot be modified from dhcpd. So I am trying to configure iptables to modify the DSCP 4 to DSCP 0. For that, I used the following commands: 

iptables -t mangle -A POSTROUTING -p udp --sport 68 -o eth2 -j DSCP --set-dscp=0
iptables -t mangle -A OUTPUT -p udp --sport 68 -o eth2 -j DSCP --set-dscp=0

However, it doesn't seem to be working. DHCP broadcast packets are still sent with DSCP 4 (DHCP Requests which are unicast are sent correctly with DSCP 0).
What am I doing wrong? This has been driving me crazy so any input will be greatly appreciated. 

Thanks,
Alexandra

---

