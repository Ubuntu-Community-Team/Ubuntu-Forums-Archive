---
title: "Interconnecting Interfaces (IP Forward)"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by vikkyhacks on 2012-02-04
I have two network interfaces ppp0 (dail-up and connected to internet all time) and eth0 .I try to ping interface vmnet8(192.168.35.1) using ppp0(223.235.244.193) and get this message 

[B][I]root@VikkyHacks:~# ping -c 1 -I ppp0 192.168.35.1
PING 192.168.35.1 (192.168.35.1) from 223.235.244.193 ppp0: 56(84) bytes of data.
^C
--- 192.168.35.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms[/I][/B]

I understand that i need to ip forward to interconnect network interfaces. I used these commands to do it

***root@VikkyHacks:~# echo 1 > /proc/sys/net/ipv4/ip_forward***


but still not working 

Any help ???

---

