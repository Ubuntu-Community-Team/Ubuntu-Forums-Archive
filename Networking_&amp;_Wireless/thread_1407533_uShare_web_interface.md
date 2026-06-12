---
title: "uShare web interface"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by eekfonky on 2010-02-15
I have forwarded the port and setup the .conf file but I cannot access the ushare web interface on:
[http://192.168.0.3:49200/web/ushare.html](http://192.168.0.3:49200/web/ushare.html)

Please help

*I had to restart my computer, then it worked!!*

---

### Post by staffann on 2011-07-16
I found this old thead while searching about uShare. Actually you only need to restart the uShare service after the conf file is changed:
sudo /etc/init.d/ushare restart
Hope this helps someone.

---

