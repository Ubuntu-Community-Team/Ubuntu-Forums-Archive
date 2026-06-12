---
title: "IP route table (dafault gateway)"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by nsblenin on 2010-11-11
Hi. I'm trying to avoid that Ubuntu changes automatically the route table every time i connect or disconnect to a network. The problem is that i have 2 NICs: eth0 and wlan0. Every time i connect to one newtork, Ubuntu gets the 10.0.0.2(eth0) gateway by default and I want 192.168.2.1(wlan0)

Moreover i modified the interfaces file and it works if i restart (/etc/init.d/networking restart) but after disconnecting and connecting wifi it does not return to original values and makes 10.0.0.1(eth0) the default gateway.

How can I execute a comand for example (sudo ip route change to default via 192.168.2.1 dev wlan0) just after every time I connect to one wifi network ??

Or how can i slove the problem. Thanks.

---

### Post by KyHx on 2010-11-11
I am having the same problem right now.
I thought I fixed it when I delete the eth0 as metric 1 and then deleted wlan0 as metric 2 and switched them. 
After a restart the problem came back, and eth0 switched back to metric 1 in my ip routing table.  

I don't want to make it permanent as in your case, but I would be ok with wlan0 always being my default unless I choose to disconnect from wifi. Maybe a script to run on startup to swap eth0 to metric 2 and wlan0 to metric 1?

---

