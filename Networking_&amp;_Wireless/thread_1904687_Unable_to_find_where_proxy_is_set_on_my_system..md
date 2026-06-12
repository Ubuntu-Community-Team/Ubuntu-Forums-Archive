---
title: "Unable to find where proxy is set on my system."
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by ravigup on 2012-01-05
Hi All,

When i do env |grep proxy, it shows http_proxy variable is set on my system. I searched in .bashrc and in System>Network Proxy but unable to find any proxy setting there. I also check this in apt.conf file but it is not set there also.
I want to remove this proxy setting. Please help me know, how to unset this proxy setting.

Thanks in advance
Ravi

---

### Post by Toz on 2012-01-05
Hello and welcome to the forums.

Try running this command from a terminal window to see if it might identify the location of where http_proxy is being set (assuming it was set system-wide):
```
sudo bash -c "fgrep -ri http_proxy /etc/*"
```

---

