---
title: "Ubuntu 10.10 - Wireless loses connection avery minute"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by scorpio2002 on 2011-02-23
Hi there,
I've just installed ubuntu 10.10 and I'm experiencing a weird issue.

Basically, after connecting to a wireless network, I get disconnected in less than a minute. I never had this issue before and I have used on this same laptop many other distros and wireless has always worked fine.

Hope u can give me some directions, because I'm getting crazy.

```
$ dmesg | grep -i wireless
[    0.761048] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[    0.761080] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   24.583830] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
```

And then...

```
[ 3033.884079] wlan0: associated
[ 3033.904834] wlan0: deauthenticating from 06:24:07:89:a8:a6 by local choice (reason=1)
```

Thank you!!

---

