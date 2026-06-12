---
title: "Cannot establish connection on port 80 on wlan0 or eth0"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by m3wolf on 2009-12-11
I am running ubuntu 9.10 (Karmic) on a dell vostro 1310. I can establish a connection on all other ports I've tried so far except for port 80 (I have tried 22, AIM ports, 8000). I tried connecting to a server on port 8000 using http with success so it's not a protocol issue.

Hardware:
Dell Vostro 1310
Intel Pro Wireless 4965 AGN Network Card (wlan0)
Realtek RTL8111/8168B PCI express Gigabit Ethernet Controller (eth0)

I have tried turning off the wireless switch and plugging in an ethernet cable that worked with another computer but the same problem persisted.

`dig <host>` returns valid DNS records whose A record works when that IP address is typed into another machine.

`apt-get update` returns:
Quote:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1:4001]
with similar entries for the other repos.

I don't know why it is trying to connect to localhost. Google returned many posts that indicate it is a proxy issue. I went to
System -> Preferences -> Network Proxy
and it was set to "Direct Internet Connection". Unless there is another mechanism that could have enabled a proxy I don't think this is the culprit.

This problem only started recently but also seems to happen when I boot off of the live CD. It coincided when I was forced to ctrl+c during an `apt-get install <package>` (I don't remember the specific package) but was intermittent. Now is persistent.

Ping and traceroute both show that (UDP) packets are getting through normally.

---

### Post by m3wolf on 2009-12-11
So the package anon-proxy was setting http_proxy and HTTP_PROXY environmental variables to [http://localhost:4001](http://localhost:4001)

I removed this package and these two variables went away on logout/login.

Now apt-get update returns a "113: No route to host" error instead.
Firefox still has same problem
I double checked that the problem occurs even with firefox settings set to direct connect and use system proxy.

---

### Post by adaucourt on 2009-12-11
> **m3wolf said:**
> So the package anon-proxy was setting http_proxy and HTTP_PROXY environmental variables to [http://localhost:4001](http://localhost:4001)

I removed this package and these two variables went away on logout/login.

Now apt-get update returns a "113: No route to host" error instead.
Firefox still has same problem
I double checked that the problem occurs even with firefox settings set to direct connect and use system proxy.

need to adjust your apt.conf with appropriate proxy settings

---

### Post by Iowan on 2009-12-11
Symptoms sound a bit like DNS problem. Check */etc/resolv.conf* to see if a valid nameserver is there.

---

### Post by jkohler2 on 2010-02-07
My Acer Aspire laptop 5315-2153 has the same failure under
Karmic Koala, Ubuntu 9.10,  where the ethernet icon appears
on and off with the message "eth0 connected" or "eth0 disconnected."

This failure doesn't happen with Ubuntu 9.04.  An eth0 connection
is made at startup, and stays on for the whole session

---

