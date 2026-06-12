---
title: "Monitor Bandwidth"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by talguy on 2009-02-01
Is there anyway to monitor the bandwidth that each computer on my network uses.  I am using the crappy free wireless router that comcast gave me.

Evan

---

### Post by puppywhacker on 2009-02-01
you could use mrtg or rrdtool to collect network bandwith usage. They work by every 5 minutes collecting statistics via SNMP from the machines you want. So each client has to run an SNMP server and your client will make nice graphs out of them.

---

### Post by talguy on 2009-02-01
ok.. I wanted to have something run on the router and then log into it and check the files or get email notifications.  I guess i would have to install tomato but my router is not supported.  I didn't want to run software on my computer to monitor the useage cause my computer is not hardwired to the router since I am on the third floor and it is on the first.

Evan

---

