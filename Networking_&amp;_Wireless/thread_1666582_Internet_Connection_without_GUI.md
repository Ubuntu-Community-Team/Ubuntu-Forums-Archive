---
title: "Internet Connection without GUI"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by wanzeo on 2011-01-13
I would like to use Ubuntu Server because I do not want or need a desktop environment on a machine that will not have a monitor attached. However, I am having trouble setting up the Internet connection because I am on a college network which requires a username and password to connect. On my Kubuntu laptop, I simply enter the information into network manager, and everything works. Is there a configuration file someplace where I can enter my username/password without having to use network manager?

---

### Post by sj1410 on 2011-01-14
it might be a proxy authentication to access the internet

you can do export on command line

```
export http_proxy=http://username:password@proxyserver:port/
```

---

### Post by darkdragn on 2011-01-14
Username and password, do they have the network set up with wpa/wpa2 enterprise encryption?

---

