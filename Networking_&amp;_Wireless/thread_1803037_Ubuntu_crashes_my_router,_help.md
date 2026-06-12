---
title: "Ubuntu crashes my router, help?"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by esc0bar on 2011-07-12
Hello there,

I decided to come back to Ubuntu on my new laptop and the latest version's installation worked like a charm... until I get this huge problem.

My desktop is wired to the router and works all fine, then whenever i run ubuntu on my laptop and try to download something, surf the internet or anything related, the router crashes and i lose connection on both my desktop and my laptop.

I have to reset the router for it to restart.

My router is a dlink wbr-1310, any help would be appreciated. :(

tHanks

---

### Post by jmoorse on 2011-07-12
Have you upgraded the firmware on the router?  (refer to manufacturer website for instructions)

Try disabling ipv6 on ubuntu and see if that solves the problem.  I seem to remember some DLink models having problems with ipv6 implementations...

[http://www.upubuntu.com/2011/05/how-to-disable-ipv6-under-ubuntu.html](http://www.upubuntu.com/2011/05/how-to-disable-ipv6-under-ubuntu.html)

---

### Post by esc0bar on 2011-07-12
I'll try the ipv6 thing sicne my router is updated.

---

### Post by esc0bar on 2011-07-12
disable ipv6 but the router still crashed when i tried to load a website on ubuntu.

---

### Post by jmoorse on 2011-07-12
Get a new router?  ;)

But seriously, I found some references to DNS relay being Problematic in the dlink firmware:

[http://www.dslreports.com/forum/r18999778-WBR1310-DNS-failures-locking-up-dying](http://www.dslreports.com/forum/r18999778-WBR1310-DNS-failures-locking-up-dying)

Try disabling that and hardsetting you DNS to test.  I recommend Google honestdns (8.8.8.8) or OpenDNS (208.67.222.222, 208.67.220.220)

---

### Post by dweir on 2011-07-24
Hey folks,

I am seeing something similar.

When I connect my laptop to the wireless network I can surf away for maybe 10-15 minutes before my router freezes, requiring a reset.

I am also using the D-Link WBR-1310 Wireless G Router, with the most recent firmware, version 4.13. Sadly, this dates from December 7th, 2007.

The logs on my Router corresponding to the latest incident are as follows:

Jan 1 00:05:06     SYN-ACK port scan attack from WAN (ip:184.168.253.1) detected.
Jan 1 00:03:10     Xmas port scan attack from WAN (ip:72.247.244.81) detected.
Jan 1 00:03:10     Xmas port scan attack from WAN (ip:72.247.244.81) detected.
Jan 1 00:02:05     SYN-ACK port scan attack from WAN (ip:184.172.243.22) detected.
Jan 1 00:01:29     SYN-ACK port scan attack from WAN (ip:184.168.253.1) detected.
Jan 1 00:00:35     Remote management is disabled.
Jan 1 00:00:35     Block WAN PING is disabled.
Jan 1 00:00:35     DMZ disabled.
Jan 1 00:00:33     DHCP: Client receive ACK from 72.139.68.1, IP=174.116.3.4, Lease time=463346.
Jan 1 00:00:31     DHCP: Client send REQUEST to server 72.139.68.1, request IP=174.116.3.4.

Not sure how to interpret these exactly, but to me it looks like the router thinks something bad has happened.  IS it possible it is putting itself into some sort of locked state?

Cheers,
Dave

---

### Post by dweir on 2011-07-24
Sorry, but there is something I should add.

The above scenario is when I conenct from a laptop running Ubuntu 11.04 (latest system updates applied).

I also have an old Asus EEE-PC kicking around with Ubuntu 9.10 running.  That device never experiences this issue.

So, this issue is caused by either:
(a) something different between Ubuntu 9.10 and 11.04, or
(b) something different between the hardware devices themselves

- Dave

---

### Post by Prosis on 2011-09-13
I have exactly the same router and the same problem!

I don't understand what jmoorse means...

Help! :(

---

### Post by praseodym on 2011-09-13
Hi Prosis,


he means: Richt-klick on the network-manager applet, edit your connection->"IPv4 setting", there in the drop-down menu you choose "Automatic (DHCP), addresses only" and add the nameservers of your provider or the google public NS 8.8.8.8 and 8.8.4.4 in "DNS-Servers"

---

### Post by Prosis on 2011-09-13
Oh ok, thanks :)

But what will that change? Why does the router crash like that?

---

### Post by praseodym on 2011-09-14
Most routers cache the websites (not the IPs!) themselve, in Ubuntu the IP resolution is done by the service dhclient, this can lead to the fact, that websites are not showing up. The nameservers in the applet solve this problem

---

### Post by Prosis on 2011-09-14
Oh I see. But my problem is that when there's too much activity exchanging data with a server on the web (like when I installed Ubuntu or when I uploaded pictures on an FTP for example) the router crashes and all my machines (come computers on Windows, my iPod) lose their internet connection. I need to reset it each time.

Will this solution help that?

---

### Post by Prosis on 2011-09-14
Oh that seemed to do the trick! I tried sending the images on the FTP server again and no crash!

Thanks :)

---

