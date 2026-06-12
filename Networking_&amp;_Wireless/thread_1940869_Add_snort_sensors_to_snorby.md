---
title: "Add snort sensors to snorby"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by prathmeshg90 on 2012-03-14
I have installed snorby to represent the o/p from snort in a GUI form.
Can anyone pls tell me how to add snort sensor to snorby. Right now the software is working fine but need to find a way to add the snort sensor so that all the alerts and logs are represented in GUI form

---

### Post by Lori700698 on 2012-05-24
I hope you have gotten an answer by now, but just to be sure you get this solved let me see if I can help.

Look at barnyard2.conf, mine is located (/usr/local/snort/etc/) you need to set the output to the snorby database you set up.

here is how mine is set up.
 output database: log, mysql, user=snorby password=snorbypass dbname=snorby host=192.168.0.102

The sensor will show up from the barnyard2.conf, then it sets & uses it from your database.

config hostname:	localhost
config interface:	eth0

 Hope this helps, it's a very cool program when you get it running.

Lori

---

