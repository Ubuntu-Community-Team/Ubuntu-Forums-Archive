---
title: "New Dlink router + Ubuntu not loading some web pages"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by jgmillr1 on 2010-10-15
I recently upgraded from my somewhat flaky dlink DIR-615 router to a new dlink DIR-628 router. Afterwards, I began noticing strange behavior with Firefox. Most web pages would load just fine, but others would either load incompletely (no images, broken drop-downs displayed as lists) or not at all. Affected web sites I noticed include amazon, facebook, monster, and netflix.

After trouble shooting of my computer (initially running 10.04, later running 10.10), I realized that other Ubuntu computers on my network were also having the same trouble. However, my wife's WinXP computer was not experiencing any such difficulty.

The issue is with the dlink 628 router, but there is something else Ubuntu/linux specific here as well. When I bypassed the router and directly connected the computer to the network, the web pages loaded fine. As soon as I reconnected it through the router, I experienced the same trouble again. When I used my old router, I had no trouble either. I get the problem regardless of wire or wireless. The MTU is set for 1500 on the computer and the router as default.

I'm ready to head back to the store and get a different router brand. Though I would like to understand the problem better in case the next one has the same issue. Anyone have any thoughts?

Thanks in advance.
-greg

In case it helps:

jgmillr1@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:7e:6a:24:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52085 (52.0 KB)  TX bytes:52085 (52.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:21:6a:44:0a:94  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe44:a94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22686459 (22.6 MB)  TX bytes:7004789 (7.0 MB)

---

### Post by pricetech on 2010-10-15
I never met a dlink that was more than a paperweight.

Netgear, Linksys, Allied Telesyn, TrendNet, are the brands I use and recommend.  TrendNet is my current pick of the lot.

You can psychoanalyze the problem if you want, but I'd just get a better router and be done with it.

---

### Post by z0diacx on 2011-08-30
I'm having the EXACT same problem with my DLink.

It's a DLINK N 150 Wirless Router  (although I'm using wired).

Some sites load fine, others (especially some big ones, like Google, Facebook, etc) load very slowly, partially, or are unresponsive until I hit F5/REFRESH a few times.

That it was something to do with IPv6 settings but I tried 'em all.

Think I'll return it.

---

### Post by praseodym on 2011-08-30
You can directly use the Network Manager applet to force a specific DNS server. For this you have to edit the network connection and under the tab "IPv4 settings" for the specific network connection set the method to "Automatic (DHCP) addresses only". Now you can in the same window set the DNS server manually, but still obtain the network addresses via DHCP. I recommend to use the google-public-nameservers 8.8.8.8 and 8.8.4.4 or the nameservers of you ISP

---

### Post by z0diacx on 2011-08-31
> **praseodym said:**
> You can directly use the Network Manager applet to force a specific DNS server. For this you have to edit the network connection and under the tab "IPv4 settings" for the specific network connection set the method to "Automatic (DHCP) addresses only". Now you can in the same window set the DNS server manually, but still obtain the network addresses via DHCP. I recommend to use the google-public-nameservers 8.8.8.8 and 8.8.4.4 or the nameservers of you ISP

For me it wasn't that the DNS wouldnt' resolve the sites to IPs; it was just slow loading times of web pages or only partial loading of web page content.  (if it was DNS prob it wouldn't even find the site)

Anyway, I've returned my DLink and am back on my old LinkSys.  No wireless N but ohwell.

---

### Post by praseodym on 2011-09-01
> **z0diacx said:**
> For me it wasn't that the DNS wouldnt' resolve the sites to IPs; it was just slow loading times of web pages or only partial loading of web page content.  (if it was DNS prob it wouldn't even find the site)

Did you try? This is a continuous problem in Ubuntu, because the service "dhclient" is responsible for DNS resolution. If you use a router the router has to tell the system via DHCP which nameserver should be used. Most routers use their own nameserver as a cache and name their own IP adress as a nameserver to the system.

---

### Post by z0diacx on 2011-09-02
> **praseodym said:**
> Did you try? This is a continuous problem in Ubuntu, because the service "dhclient" is responsible for DNS resolution. If you use a router the router has to tell the system via DHCP which nameserver should be used. Most routers use their own nameserver as a cache and name their own IP adress as a nameserver to the system.

Actually I don't even use Ubuntu (didn't even know what it was before joining here).  I was just searching to see if I was the only one that had that problem with a router before.

But like I mentioned, it can't be a DNS problem.  If the person's DNS server responds with a site's IP address, the IP address is used from that point on.  And if the DNS doesn't respond, the site can't be contacted at all.  With me, pages would often load only partially, or VERY slowly. (which wouldn't be a DNS problem since DNS is only contacted at the very beginning to get the IP, and IP is used after that.  [at least with Windows], the IP is cached so it doesn't have to ask DNS 500X for each instance on a web page)

---

