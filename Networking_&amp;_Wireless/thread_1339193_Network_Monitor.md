---
title: "Network Monitor"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by joe2012 on 2009-11-27
My internet provider recently capped the bandwidth and I don't want to have to log into their site to see all the bandwidth used. Is there a tool that can track the bandwidth, and alert me when the bandwidth hits a certain amount?

Thanks.

---

### Post by Yoann Juet on 2009-11-27
You can try "ifstat" tool for instant bandwidth reporting. Another solution (more complex) could be to activate your local snmp agent then poll it regularly - oid corresponding to your network interface - then graph bandwidth consumption with rrdtool. cacti tool does the job with a web interface (apt-get install cacti)

---

