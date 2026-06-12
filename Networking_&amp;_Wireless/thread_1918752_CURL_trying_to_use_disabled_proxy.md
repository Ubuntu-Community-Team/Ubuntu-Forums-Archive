---
title: "CURL trying to use disabled proxy"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by Weirdy on 2012-02-01
Hey guys;

I just tried to use curl from the terminal on my laptop and its failing. It's trying to use a proxy I sometimes use but is disabled at the moment. Let me explain....

I take my laptop between home, where I connect to the internet without a proxy, and school, where I have to enable it. I enable/disable it through the Network -> Proxy menu (Running 11.10 Oneiric here) as and when I need to. At the moment the proxy is disabled (I'm accessing the web fine) but curl has somehow found that I sometimes use this proxy and is trying to contact it. (I found that out by running it with the ```
--verbose
``` flag)

Any ideas why this is happening/how I can fix it?

---

### Post by Weirdy on 2012-02-01
Update: I tried running it with the --noproxy * flag, which according to the man page would turn off the proxy, but to no avail :(

---

