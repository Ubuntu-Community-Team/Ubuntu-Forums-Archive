---
title: "IPTables MAC Filtering for ICS"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by davidm84 on 2009-12-02
Hi everyone,
So I've consulted Google and can't find a solution to my problem. Closest one is [here. ]("http://ubuntuforums.org/showthread.php?t=395211")I'm wanting to allow my personal computers to access Internet and shared files through or on my Ubuntu router. I also want to restrict other people on the network from accessing the Internet but allow them to access shared files on my network. 

So everything works if I don't set any rules but as soon as I try MAC filtering, it stops all the Internet access. So here's what I got:

> iptables -F
iptables -P FORWARD DROP
iptables -A FORWARD -m mac --mac-source 00:02:44:92:7F:B3 -j ACCEPT #(eth0 mac)
iptables -A FORWARD -m mac --mac-source 00:14:bf:7f:01:8a -j ACCEPT #(WAP mac)
iptables -A FORWARD -m mac --mac-source 00:1c:bf:3b:ba:41 -j ACCEPT #(Allowed Client PC mac)
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
Thanks guys

---

