---
title: "Trying to disable internet connection"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by frankelr on 2009-02-12
trying to disable internet connection, turning off network does NOT
disconnect internet connectivity.  tried ifconfig eth0 down ...does nothing.  tried firestarter via lock command stops internet, but firestarter  program fails and system reboot is required to restart.  VERY Confused!  my original goal was to disable internet for specific users.  Any idea or help????


Bob

---

### Post by odium1 on 2009-02-12
when you try ifconfig eth0 down what is it telling you?

---

### Post by frankelr on 2009-02-12
Thank you for the response,

ipconfig eth0 tell me normal standard information about a working connection.

---

### Post by frankelr on 2009-02-12
sorry i meant to type ifconfig

---

### Post by superprash2003 on 2009-02-12
its ifdown eth0 not ifconfig eth0

---

### Post by frankelr on 2009-02-12
Thank you, i will give it a try

Bob

---

