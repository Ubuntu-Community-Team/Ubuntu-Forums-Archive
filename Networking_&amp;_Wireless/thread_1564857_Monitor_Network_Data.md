---
title: "Monitor Network Data"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by saurabh_negi on 2010-08-31
Is there any tool similar to NetMonitor for Ubuntu, which can be used to monitor the data usage.

thanks

---

### Post by MaindotC on 2010-08-31
[Ntop](http://www.ntop.org/news.php) is a tool that can monitor the amount of data passing through your network interface card.  I don't know if it also provides this information for the entire network, but if you need to monitor traffic through your network gateway/access point than you would either have to install [DD-WRT](http://www.dd-wrt.com/site/index) on your gateway/access point a service called [Nagios](http://www.nagios.org).  Checck out google images for both and you can see the type of displays it will present to you - namely pie charts.  Does that help?

---

