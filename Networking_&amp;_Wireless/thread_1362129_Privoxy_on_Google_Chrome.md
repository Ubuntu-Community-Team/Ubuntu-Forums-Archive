---
title: "Privoxy on Google Chrome"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by ExileAmongYou on 2009-12-22
I started using privoxy to block ads, and it seems to work fine (possibly with a bit of slowdown), but my issue is that when you open up the proxy settings through Google Chrome, it opens up the global system settings for proxies. It seems like this is probably going to slow down other internet apps that don't need ad blocking, like Vuze. Is that actually an issue, or does it not matter? If it is a problem, how do I set it up to just filter Chrome?

---

### Post by Brandon Williams on 2009-12-22
'man google-chrome' provides all the information you need. There are command line switches and environment variables that can be used to specify proxy settings for chrome when you launch it. For example:
```
--proxy-server=host:port
Specify  the HTTP/HTTPS proxy server.  Overrides any environment
variables or settings picked via the options dialog.
```

---

### Post by ExileAmongYou on 2009-12-23
Awesome, fixed now. Thanks!

---

