---
title: "/etc/init.d/snort says started but ps -ef says no"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Claudius1974 on 2009-02-22
I hope that somebody can help me with this one. 

I've just installed Snort and MySQL using apt-get on the lastest version of Ubuntu server. When i run Snort interactively using 'snort -c /etc/snort/snort.conf' I can see alerts being logged after running nmap against the server and running ps -ef | grep snort shows snort running as a process. 

However, when the daemon is started using /etc/init.d/snort the script reports that Snort has started but I do not see any alerts logged and there is no corresponding entry is ps -ef. /etc/init/d/snort status returns fail.

Has anybody come across this before? I'm assuming that Snort is failing quietly but can't find any mention if there is a log file or verbose setting that I can turn on to solve this?

---

