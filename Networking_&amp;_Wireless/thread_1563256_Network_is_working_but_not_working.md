---
title: "Network is working but not working?"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by TheCraneMan on 2010-08-28
OK so I set up a server yesterday and got ndiswrapper loaded on it with the appropriate driver, I edited the */etc/network/interfaces *file to contact my router with it's MAC address, WEP Key, etc...  So the problem is I can ping addresses like Google and Ubuntu Forums but I can't use *apt-get* to install or update packages. When I try *sudo apt-get update *I get a whole bunch of ```
 W: Failed to fetch <address>        Temporary Failure resolving <address>
```

My Wireless interface is wlan0 and also I can ping my server from my other computer running Linux and my server can ping that computer too.

Someone please help, thanks in advance!   -Canute

---

### Post by TheCraneMan on 2010-08-29
Nevermind dumb fix, I needed resolv.conf that's all.

---

