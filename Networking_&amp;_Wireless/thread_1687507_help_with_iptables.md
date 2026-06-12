---
title: "help with iptables"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by judderwocky on 2011-02-14
i'm running privoxy and wanted to write a script for my rc.local file or for my crontab that would load some custom iptables in.

I am running privoxy and tor, and I would like to have Tor run as a separate user. I want to allow different users to connect to the internet, but only through Privoxy, and I want to put a fairly restrictive set of protocols in place to ensure security

I was thinking about using something like this to make sure that the only connections going into and out of privoxy were on its 8118 port.....

```

iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP

iptables -A OUTPUT -p tcp --dport 80 -m owner --uid-owner privoxy -j ACCEPT
iptables -A OUTPUT -p tcp --dport ! 80 -m owner --uid-owner privoxy -j DROP

iptables -A OUTPUT -s 127.0.0.1 -d 127.0.0.1 --dport 8118 -j ACCEPT  
iptables -A INPUT  -s 127.0.0.1 -d 127.0.0.1 --dport 8118 --uid-owner privoxy -j ACCEPT    
iptables -A INPUT  -s 127.0.0.1 -d 127.0.0.1 ! --dport  8118 -m owner --uid-owner privoxy -j DROP
iptables -A OUTPUT -s 127.0.0.1 -d 127.0.0.1 ! --dport  8118 -m owner --uid-owner privoxy -j DROP


```

---

