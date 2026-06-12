---
title: "havp error avg: could not connect to scanner"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2012-12-28
I have ubuntu linux havp proxy installed and working with clamav but I want to use avg dowlonded avg free 2012.
i get in the error log
--initializing avg socket scanner
avg: could not connect to scanner! scanner down?

in the havp.config file i have
#avg socket scanner
enableavg true
#avg daemon needs to run on the same server as havp (it does)
#default
avgserver 127.0.0.1
avgport 55555

---

