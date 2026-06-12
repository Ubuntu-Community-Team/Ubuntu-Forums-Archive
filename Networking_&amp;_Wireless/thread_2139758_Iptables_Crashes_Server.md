---
title: "Iptables Crashes Server"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by ViPeRaY on 2013-04-27
Hello Everyone,

I am dealing with a weird issue which I do not know how to troubleshoot. Basically I have a Ubuntu Server 12.04.2 LTS. Here is the server specs:
[LIST]
[*]Dual Core Intel 1.86Ghz
[*]2GB System Memory
[/LIST]

I have running following apps:
[LIST]
[*]Apache2 (Used for basic web sites and FTP)
[*]Privoxy
[/LIST]

The issue is, I cannot use iptables for this box for some reason. I have a basic iptables I am trying to apply and it is all good. It takes the rules, but about 15 to 20 minutes after applying the rules, the server becomes totally unresponsive. When I try to ssh in, I get connection refused error. The weird thing is, during this time, the server still pings. However, I cannot get to the server at all which is why I have to force reboot the server. When there is no iptables, server is just fine. After reboot, I check the logs and both kernel and syslog shows a gap which means server basically stops logging when it is unresponsive.

Here is the rules I am trying to apply:

```

# Set default policies for all three default chains
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT


# Enable free use of loopback interfaces
iptables -A INPUT -i lo -j ACCEPT


# All other rules
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport ssh -i eth0 -j ACCEPT
iptables -A INPUT -p tcp --dport 50001 -i eth0 -j ACCEPT
iptables -A INPUT -p udp --dport 50001 -i eth0 -j ACCEPT
iptables -A INPUT -s 1.1.1.1 -p tcp --dport 50002 -i eth0 -j ACCEPT
iptables -A INPUT -s 1.1.1.1 -p tcp --dport 443 -i eth0 -j ACCEPT

```

Can someone please help me troubleshoot this issue?

Thanks,

---

### Post by Doug S on 2013-04-27
Your iptables rule set is simple enough. It is hard to understand why it might cause server issues after 15 minutes.
Perhaps use "top" to monitor cpu usage and memory usage during the 15 minutes after the rule set is loaded.
Also you could monitor the connection tracking table, to see if it grows unreasonably fast or to an unreasonable size (And I do not know what unreasonable would be for your server.)```
sudo cat /proc/net/ip_conntrack
```

---

