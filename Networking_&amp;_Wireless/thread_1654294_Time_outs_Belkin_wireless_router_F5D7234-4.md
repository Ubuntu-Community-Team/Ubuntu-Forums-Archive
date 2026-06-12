---
title: "Time outs Belkin wireless router F5D7234-4"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Sam3280 on 2010-12-28
Hi,
I recently purchased a TPlink 5 port switch, which for some reason didnt work with windows, only my ubuntu computer, I found a cheap wireless belkin router which also has 4 wired ports. It now works well except that it is slow searching for new servers eg, going to facebook creates a long wait and can even time out but once on the website everything works fast, The connection is 2.89 Mbps which is good for this area and ping is 45ms. What could I do to fix this problem. This affect my ubuntu computer and the windows xp pc as well

---

### Post by Sam3280 on 2010-12-30
The following works
1) Open a firefox window 
2) go to 192.168.2.1 or type router and hit Enter.
3) Leave the password blank and click submit
4) Click on DNS under Internet WAN.
5) Uncheck the option "Automatic from ISP."
6) Enter the DNS Address > 208.67.222.222
7) Secondary DNS Address > 208.67.220.220
8) Apply the changes.

restart router

---

### Post by PatchesTheCaveman on 2010-12-30
I've noticed the built-in DNS on Belkin routers doesn't work very well.  I do the same thing (with my ISP's DNS servers of course) to get much better speed.

---

