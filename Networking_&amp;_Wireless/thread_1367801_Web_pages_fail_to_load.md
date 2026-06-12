---
title: "Web pages fail to load"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by kogger on 2009-12-29
At my girlfriend's house, for some reason my Ubuntu doesn't want to load any web pages. Windows works just fine (which is where I'm writing this from); Ubuntu connects, and running ping from the terminal succeeds; so what could be causing the browsers to fail?

I have a dell studio 15 dual-booted with windows 7 and karmic koala and a dell 1397 wlan wireless card.

---

### Post by focwiz on 2009-12-29
> **kogger said:**
> At my girlfriend's house, for some reason my Ubuntu doesn't want to load any web pages. Windows works just fine (which is where I'm writing this from); Ubuntu connects, and running ping from the terminal succeeds; so what could be causing the browsers to fail?

I have a dell studio 15 dual-booted with windows 7 and karmic koala and a dell 1397 wlan wireless card.

Does she have a different ISP than you do?  It may be a DNS Issue.  See the following post...?
[http://ubuntuforums.org/showthread.php?t=1361797]("http://ubuntuforums.org/showthread.php?t=1361797")

---

### Post by jonest1 on 2009-12-29
Are you getting name resolution?  In other words, try to resolve [www.yahoo.com](www.yahoo.com) and it should come back with IP addresses.  

If it does not come back with addresses, you may want to initially look at hardcoding the dns server settings into network manager.

You may also want to run 'route -n' to ensure the default gateway is the router.  The the route where the destination is '0.0.0.0'.

If all this checks out, the only thing I can think of quickly are if you have some proxy settings which are getting in the way.

---

### Post by FuManShu on 2009-12-30
Is your wireless working on connections other than your girlfriends?  The Dell 1397 wlan is actually the BCM4312 if I'm not mistaken and that is a card that is renowned for it's compatibility issues w/ Linux.  If this is an all encompassing issue than you might try installing the bcmwl-kernel-source package, available on the live CD if you don't have internet access, as this has helped many to resolve their Broadcom wireless issues, though your specific issue is a bit different.

On another thought, since you're able to connect and ping addresses, perhaps it's a IPv6 issue.  If you are using Firefox, type in the address bar "about:config" without the quotes.  Find the line that says "network.dns.disableIPv6" and toggle it to true.  Right-click the network icon --> Edit Connections... --> Highlight your girlfriends network and click edit --> IPv6 Settings --> Set to ignore.  If that still doesn't work, try running:

sudo ip addr del ::1/128 dev lo

I have to do this when I tether my iPhone, as it does not recognize Quad-A DNS queries, resulting in massive timeouts.

---

