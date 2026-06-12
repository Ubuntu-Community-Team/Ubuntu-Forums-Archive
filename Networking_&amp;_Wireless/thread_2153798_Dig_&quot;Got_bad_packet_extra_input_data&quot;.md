---
title: "Dig: &quot;Got bad packet: extra input data&quot;"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by ZTiger on 2013-06-12
I have two 13.04 systems. Dig works just fine on one but the other that was an upgrade instead of a clean in stall seems to have some odd issues.

The desktop that has the issue works normally by all accounts. I only ran into my issue with `dig` while doing some network validation on my companies network.

It queries the DNS server but at some point it gets an error


```
;; Got bad packet: extra input data
```

I have tried the same dig command on a separate  13.04 install and it works just fine. Both are plugged into the same switch (Switching ports doesn't matter). I even went so far as to spoof the laptops mac address to see if there was something upstream filtering that traffic. It still had the same result.

I'm wondering if something maybe corrupt on my install or if maybe a config from 12.10 was left over and is making things work incorrectly in 13.04

I have looked at /var/log/syslog but really didn't see anything to be alarmed about other than avahi-daemon receiving an invalid response from some other system but it wasn't eve at the time I ran the dig.

Any help would be appreciated


Information:
OS: Ubuntu 13.04 64 Bit (System upgraded from 12.10)

---

