---
title: "Last few issues to iron out with iptables"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by qprfact on 2009-12-23
I have a home network with set up as follows:

1. Belkin ADSL Router incl wireless
2. Ubuntu server
3. My MacBook Pro
4. Two Acers running Ubuntu
5. Laptop running dual boot Ubuntu and Vista
6. PC running dual boot Ubuntu and Win XP
7. Wii

What I want to do is push all traffic bar the Mac via the Ubuntu server so I can control access using iptables. I have been following the guide here - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo).

All devices now have static IPs which look to the server (in my case 192.168.2.5) apart from Mac which looks at router (192.168.2.1)

This is the problem. I apply these rules in iptables from server (which I access using Chicken of the VNC on Mac):

# iptables -A INPUT -p tcp --dport ssh -j ACCEPT
# iptables -A INPUT -p tcp --dport 80 -j ACCEPT
# iptables -I INPUT 1 -i lo -j ACCEPT
# iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
# iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

All good so far. Then I do this:

# iptables -A INPUT -j DROP

At this point I lose the connection between Mac and Server and can no longer see it or SSH to it. Clearly the firewall is working!

The question is - how do I add a rule that allows me to block all else, but still allow Mac to see Server?

Thanks in advance!

---

### Post by qprfact on 2009-12-29
It appears it was DNS related - adding these two lines fixed it:

```
iptables -I INPUT -m tcp -p tcp --sport 53 -j ACCEPT

iptables -I INPUT -m udp -p udp --sport 53 -j ACCEPT
```

---

