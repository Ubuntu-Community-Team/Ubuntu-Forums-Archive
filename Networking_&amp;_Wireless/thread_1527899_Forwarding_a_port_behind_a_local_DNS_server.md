---
title: "Forwarding a port behind a local DNS server"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by Kepesk on 2010-07-09
Here's my (admittedly complex) situation:

I set up a dynamic DNS address for my home network.  Let's call it awesome.server.com.  Then I set up one of my machines with a bind9 DNS server and pointed my router's DNS setting to it.  I did this so that I could resolve awesome.server.com from machines inside my network and have them correctly find my server.  Then I set up a second machine to serve web pages using [http://awesome.server.com:9200](http://awesome.server.com:9200).  I did this by forwarding port 9200 on my router to port 80 on that machine.  This works, but of course, it only works from outside my network.

**What is the best way to get [http://awesome.server.com:9200](http://awesome.server.com:9200) to work from inside my network?**

I've tried setting up the iptables on my server to forward that port, but it just times out.  I used these rules that I found by searching the internet:

```
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 9200 -j DNAT --to 192.168.0.300:80
iptables -A INPUT -p tcp -m state --state NEW --dport 9200 -i eth1 -j ACCEPT
```

However, those rules might be failing because they are intended to forward ports requested from outside the network.  I must admit, this iptables stuff is way, way over my head.  Is there a different method that I must use to make it work inside my network?  Or is there a better way besides iptables?

Thanks!

---

### Post by Kepesk on 2010-07-10
Got it figured out!

I ditched my efforts with the terribly complex iptables junk and instead enabled proxies on my server's apache installation (there are multiple instruction sets for this online).   Then I told apache to listen to port 9200 added this to the configuration.

```

<VirtualHost *:9200>
ProxyPreserveHost On
ProxyPass / http://192.168.0.300/
ProxyPassReverse / http://192.168.0.300/
ServerName flyingweasels.dontexist.com
</VirtualHost>

```

Now everything works perfectly from inside and outside the network.

---

