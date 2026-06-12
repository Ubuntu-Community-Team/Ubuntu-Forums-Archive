---
title: "software to monitor ALL network traffic"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by daweefolk on 2012-02-13
does a program exist that is able to monitor all traffic going through the network I'm connected to? I'm hoping to be able to see which connected device is using the most bandwidth, and see if anyone is "stealing" my wifi.
preferably this would be a text-based program.

---

### Post by winh8r on 2012-02-13
vnstat will monitor all network traffic and give you daily totals.


to install vnstat


```
sudo apt-get install vnstat
```


to get info on options

type ```
man vnstat
``` 

after installation





EDIT:: you might want to have a look at nmap for discovering who is on your network too if you think there is a security issue.

---

### Post by daweefolk on 2012-02-13
Thanks, I'll check them out. I guess I mostly want to know because lately we've been having issues with REALLY slow connections so I want to know either 1: who/what is using a lot of bandwidth or 2: are there any people connected who shouldn't be

---

### Post by jerrrys on 2012-02-13
I have two dated links that may still prove useful.

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by daweefolk on 2012-02-13
> **jerrrys said:**
> I have two dated links that may still prove useful.

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

Thanks for the links, it looks like iptraf might be what I'm looking for.

---

### Post by SeijiSensei on 2012-02-13
If you push all your traffic through a Linux router, [ntop]("http://www.ntop.org/") is a lovely application for traffic monitoring.

---

