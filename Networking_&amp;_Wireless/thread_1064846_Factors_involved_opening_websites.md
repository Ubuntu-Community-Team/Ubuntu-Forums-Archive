---
title: "Factors involved opening websites"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by gilloz on 2009-02-09
I've noticed on this forum that there are people who are having the same problem that I am experiencing.  When you click on a link, it takes forever to open up that website.  You get the "Waiting for (website name)" in the status bar.  Can anyone tell me what are the factors that are taken into consideration to determine how fast or slow the websites will open?

---

### Post by punx45 on 2009-02-09
well, theres the load on the server, the speed of the server itself, the servers uplink speed, the speed of any route hops between it and your ISP, your speed to your ISP, then theres the content of the page, some can get stuck by bugs in scripts and stuff like that.   the list goes on.

---

### Post by primpil on 2009-02-09
have same problem
google loading fast, all others - without end
can ping all sites(responce pretty fast), but cant load them

ubuntu  8.10

same sites on same laptop in win xp loads fast :(

---

### Post by netztier on 2009-02-09
> **punx45 said:**
> the list goes on.

[SIZE="4"]DNS![/SIZE]

A lot of these problems are DNS related. I always wonder why there are so many suggestions to disable IPv6, enable this, configure that - and nobody cares to debug DNS properly. 

There are broadband routers out there that have just plain broken DNS proxy services on them, which get into a timing race condition between DNS proxy and resolver ("DNS client) on the OS. Some resolvers behave different than others - hence the apparent difference between windows and Linux/Unix on the same hardware/same network/using same router. There once was (still is?) such an issue between Safari on MacOSX (10.5.6, I believe) and the broadband routers made by AVM (their Fritz!Box product line, quite popular in Germany).

One of the first things to work around these problems is to manually configure other DNS servers than the DNS-Proxy on your broadband router (if your DNS has the same IP address as your default gateway, then you're very probably using your router's DNS proxy). These can be your ISP's DNS, or ones by opendns.com, thus bypassing the (possibly broken) DNS proxy of your broadband router.

Depending on the router's capabilities, you can configure it's DHCP server to tell the client systems which (external) DNS servers to use (instead of advertising it's own LAN address as DNS). Then you can simply enter your ISPs DNS addresses right there, and renew the client's DHCP lease (check that /etc/resolv.conf now has other IP addresses listed than before).

Classicaly, DNS servers are configured in /etc/resolv.conf, and you can do that while connected. But as soon as NetworkManager renews a DHCP lease or reconnects to a network, it will probably overwrite your changes. 

If you can't modifiy the DHCP server config in the router, you can uncomment a line in  /etc/dhcp3/dhclient.conf and add your preferred name servers there

Original
```
#prepend domain-name-servers 127.0.0.1;
```

change to 

```
prepend domain-name-servers <IP of preferred DNS>;
```

Like this, these servers will always be listed in /etc/resolv.conf first, regardless of what NetworkManager learns via DHCP. Be careful though, as this might have unwanted side effects, especially if you're working in a corporate or university network that has internal DNS domains. These internal domains might be unresolvable by the external DNSs, or vice-versa: your external DNSs might not be reachable from the corporate/school/university networks.

regards

Marc

---

### Post by gilloz on 2009-02-09
Thank you all for your replies.  I am presently using the Ubuntu Hardy 64 bit OS and using the OpenDNS.com DNS numbers with ipv6 still enabled.  I haven't disabled it since I have installed the 64 bit Hardy.  Not sure if it will make a difference if I disable it.  Can seen to get my siginature to appear, but I have the Asus P5N-D, Intel E8500 CPU, 4GB PC-6400 DDR2,GeForce 9600 GSO 764 GB DDR2 and 2 ea. 320 GB from W.D.  My computer is fast enough, but the opening of websites take a while. (DSL speed 768K)

---

### Post by gilloz on 2009-02-09
OK, netztier, I made the changes in my /etc/dhcp3/dhclient.conf file and I don't want to jinx this, but I made a quick run around of the website opening all kinds of websites and they open up really fast, like under 2 seconds or so.  I am not sure, but it looks really good.  I will continue to do this today and get back on to report any feedback.  Thanks so much.

Added note:  I am presently using the OpenDNS.com DNS numbers: 208.67.222.222 & 208.67.220.220

---

### Post by gilloz on 2009-02-09
OK, I'm back.  Well, the change in the dhclient.conf file has improved my situation by at least 80%.  On those occasion when the response was slow, I double clicked on the link and it opened up quickly.  Thank you netztier for the tip and primpil and punx45 for your responses.

---

