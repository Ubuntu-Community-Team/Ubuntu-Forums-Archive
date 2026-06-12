---
title: "iptables setup"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by firstAsuran on 2011-12-02
I'm having a big problem setting up my iptables for my server which also serves as my router. The problem I have is I can't seem to open any of the ports I would like to open (mainly port 80 and 443).

These are my current rules: 

-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -i eth0 -j ACCEPT
-A INPUT -i eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth1 -p tcp -m tcp --dport 80 -j ACCEPT

eth0 = LAN
eth1 = WAN

What am I missing here? (packets still get dropped and listing netstat -ant | grep LISTEN shows apache listening on port 80).

Thanks in advance

---

### Post by poolet on 2011-12-02
check out the follow link::: 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Hope that helps u!!!

---

