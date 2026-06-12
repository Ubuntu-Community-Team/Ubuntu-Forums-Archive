---
title: "Configure system proxy in Lubuntu 13.04"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by g0yjs0 on 2013-06-14
I am pretty new to Lubuntu, having just downloaded and installed version 13.04.  Been poking around the LXDE menus and cannot find an option for configuring the system proxy settings.

A Google search and Ubuntu forums search has been fruitless as well.

Any assistance is appreciated.

Thanks.

---

### Post by dummy910 on 2013-07-03
To set up Privoxy, do the following

as a super user:
```
apt-get install privoxy
```
start privoxy:
```
/etc/init.d/privoxy start
```
Set firefox (or other web browser) to use Privoxy via browser proxy settings:
assign ports to 8118 for both HTTP and SSL

**Privoxy 3.0.21 User Manual**
**[http://www.privoxy.org/user-manual/quickstart.html](http://www.privoxy.org/user-manual/quickstart.html)**

---

