---
title: "no network in Dapper"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Daboo on 2006-06-12
Been trying for a couple weeks to get internet in Dapper. At first I thought it was my onboard nvidia ethernet, but I've tried 2 additional working nics which work fine in XP. Here's what I get when I try ifup eth1 (which I had to write down since I cant even burn the .txt to cd):

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.38.232.1
DHCPREQ on ETH1 to 255.255.255.255 port 67
DHCPACK from 10.38.232.1
subnet_number(): inet.c:56: addr/mask length mismatch
Failed to bring up eth1

My ISP is Current Broadband, and I'm plugged directly into the power line modem. Please help!

---

### Post by jvictor on 2006-06-13
Daboo, there are a lot of threads that talk of using a static IP, disabling IPv6 and using ur ISPs DNS server in /etc/resolv.conf. Mabe following one of them may help u. It can be a prob with the network scripts of Linux or even the way the router handles windows / linux

---

### Post by grw on 2006-06-13
It might be something to do with the netmask. See
[http://www.ubuntuforums.org/showthread.php?t=133599](http://www.ubuntuforums.org/showthread.php?t=133599)

---

### Post by DougC on 2006-06-13
Or maybe this one......

[http://www.ubuntuforums.org/showthread.php?t=191231](http://www.ubuntuforums.org/showthread.php?t=191231)

---

### Post by Daboo on 2006-06-13
Thanks for the links. The problem is I've never had it working even once though. I've tried deactivating/activating and nothing. Is it possible for me to set up a static address?

---

### Post by grw on 2006-06-13
Things should work with DHCP. (I don't really know whether you can set up a static address.) My problem, however, was similar to your's but with 5.10. I never got it working at all while Windows worked fine. It took me months to find out that it was a dhcp3 bug that was very simple to fix. Have you tried the suggestions above?

---

### Post by Daboo on 2006-06-13
Well, I'm not sure what to try. Those two posts referenced are not the same problem that I'm having. Pretty stumped here :confused:

---

### Post by gmc on 2006-06-14
There is a problem with dhclient/dhcient3.

try:

sudo dhclient eth#    (ovbiously # = your ethernet port number) or
sudo dhclient3 eth#

One of those should work. It did for me, but alas I'm not at the machine right now and don't recall which one worked. It should be noted that this problem extends in to Debian/Unstable. I tried Deb/Unstable on the weekend as a test for a LTSP client and found the exact same problem there too.

Gord

P.S. Please spread the word. There are a lot of users being bitten by this problem.

---

