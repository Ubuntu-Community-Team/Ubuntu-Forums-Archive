---
title: "wireless is incredibly slow - maverick fresh install"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by nado121 on 2010-10-13
Hi,
 
yesterday I did a fresh install with 10.10 on my notebook.
Everything seemed to work fine, my ath9k wireless connected right away to my network. However, the network speed I get, according to the system monitor, is 0 most of the time and has bumps of around 1kb/s every 20 or so seconds.
It's impossible to even think about using the internet.
My smartphone uses the same network and runs perfectly well with the 6Mbit/s it's supposed to have, so I'm sure it's neither my router nor my ISP.
Downloading the wireless backports package via phone and installing them did no good, either. Nobody on #ubuntu seemed to care/know, so you guys are my last hope. What can I do? Could it help to try a different wireless client, say wicd? Where could I get a complete package with all dependencies?
 
Thanks in advance!

---

### Post by nado121 on 2010-10-13
seriously, nobody??

---

### Post by tiz29 on 2010-10-13
It also happens to me and the same result with WICD

---

### Post by nado121 on 2010-10-13
> **tiz29 said:**
> It also happens to me and the same result with WICD
 
well, at least I'm not alone with this problem

---

### Post by nado121 on 2010-10-14
bump

---

### Post by dimoftheyard on 2010-10-17
I don't have the same problem with 10.10, but could this be due to IPv6? I had that problem a couple of times. You could try that in firefox: Type about:config, agree to be carefull and change network.dns.disableIPv6 to true. If firefox is responsive again after that, you should disable IPv6 system wide. If not, I fear I don't know what to do.

---

