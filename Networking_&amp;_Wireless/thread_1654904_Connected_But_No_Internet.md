---
title: "Connected But No Internet"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by QsoftStudios on 2010-12-29
I'm running Ubuntu 10.04 LTS and how I get internet is I attach a network cable from my desktop, to a router, then to my laptop witch is running windows 7 and has wireless. This allows me to share the wireless connection and use the laptop as a modem. It worked for the longest time but then it suddenly didn't, It says it was connected to the network but theirs no internet connection. Iv tried several NICs and routers but nothing seems to work. Do any of you know how to fix this?

---

### Post by PatchesTheCaveman on 2010-12-29
I'll bet you $20 the problem is on the Windows laptop, not Ubuntu.  Click on the wireless icon next to your clock and click *Open Network and Sharing Center*.  Then click *Change adapter settings* on the blue bar on the left.  Right-click on *Wireless Network Connection* and hit *Properties*.  Click on the *Sharing* tab.  If *Allow other network users to connect through this computer's Internet connection* is unchecked, check it and hit OK.  That should make it work.  

If it is already checked, uncheck it and click OK.  Then go back into that Properties window, return to the Sharing tab, and recheck it and hit OK.  Then see if it works.  Sometimes Windows arbitrarily decides to stop sharing your Internet connection and that is the only way to fix.  You should really consider running Ubuntu on your laptop to share your Internet connection.  It does a much better job than Windows at doing so.

If it still doesn't work after that, then get on the Ubuntu desktop go to Applications > Accessories > Terminal and type the following in the black box and press Enter:
```
ifconfig -a
```

Copy and paste what appears into a post here.  We'll see if we can fix it.

---

### Post by QsoftStudios on 2010-12-29
Nvm I caved and got a wireless adapter but thanks anyway!

---

