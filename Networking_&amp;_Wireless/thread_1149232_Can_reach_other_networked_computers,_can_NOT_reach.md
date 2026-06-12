---
title: "Can reach other networked computers, can NOT reach router or internet"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by AdotB on 2009-05-05
Hi, I have a strange problem that seems to have come out of nowhere. For a long time, until today, my current setup has worked flawlessly.

I have a desktop and a file server connected to a router. When I tried to ssh into the file server today, it took over 10 seconds to get the prompt. I soon found out that the file server could not access the Internet for updates or anything else. My desktop seems to have no problems at all.

From the file server (running Ubuntu server 8.04), I can ping the desktop, but not the default gateway. After searching for answers, I found a possible solution for the ssh slow login problem by adding "UseDNS no" to the sshd_config file. Now ssh logs in quickly as it always has, but still cannot reach the router or Internet. This makes me think there is a DNS problem, but the resolv.conf, and interfaces files both seem fine.

Does anyone have any ideas?
Thanks

---

