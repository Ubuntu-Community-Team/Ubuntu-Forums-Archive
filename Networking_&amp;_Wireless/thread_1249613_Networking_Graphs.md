---
title: "Networking Graphs"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by harry71194 on 2009-08-25
Okay, I have seen images of sites similar to this, where it makes a nice pretty graph of the bandwidth being sent and received. I have looked everywhere for a free program like this with no luck.

Here is an example of what I mean,
[IMG]http://freakbits.com/media/pbt-boost.jpg[/IMG]

I know that Linode VPS has something like this, but I think it is closed source (nor do I use them). A lot of other sites I have seen with them too.


So if anyone knows a good easy to use program for making these graphs automatically and posting them somewhere on my site, it would be cool!

At the moment I am using Webalizer, and it is basic, but nice. I just need something else that will include the network traffic.
[http://harryy.us/stats/](http://harryy.us/stats/)




Thanks!

---

### Post by harry71194 on 2009-08-25
I have tried cacti, and I have read this guide, with no success.
[http://www.cyberciti.biz/faq/fedora-rhel-install-cacti-monitoring-rrd-software/](http://www.cyberciti.biz/faq/fedora-rhel-install-cacti-monitoring-rrd-software/)

Of course, it says it is for redhat, and that is probably my problem. Anyways, cacti works fine for everything, except for monitoring the network use. I just can not seem to get an SNMP OID or whatever for it working. The OID they gave does not work.

> snmpget -v 1 -c public localhost .1.3.6.1.4.1.4413.4.1
Error in packet
Reason: (noSuchName) There is no such variable name in this MIB.
Failed object: SNMPv2-SMI::enterprises.4413.4.1


---

