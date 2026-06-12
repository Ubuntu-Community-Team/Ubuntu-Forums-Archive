---
title: "HUAWEI error"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by doperative on 2011-07-29
I downloaded and run sakis3g and I get this results .. ./sakis3g  .. modem responded "ERROR" while checking for pin .. any help would be really appreciated ...

---

### Post by pdc on 2011-08-02
is this of any help

[http://lmgtfy.com/?q=sakis+help+forum+.%2Fsakis3g+..+modem+responded+%22ERROR%22+while+checking+for+pin+](http://lmgtfy.com/?q=sakis+help+forum+.%2Fsakis3g+..+modem+responded+%22ERROR%22+while+checking+for+pin+).

---

### Post by doperative on 2011-08-02
> **pdc said:**
> is this of any help

I have been round the houses on this I have tried every solution .. OK this works ...

#Boot up ..

$/etc/init.d/network-manager stop

$killall modem-manager 

#insert modem

$modem-manager --debug

#And in another BASH Window

$/etc/init.d/network-manager start

# And I'm up and browsing, how do I automate this, I do know if I close the first Windows then the modem is disconnected.

---

