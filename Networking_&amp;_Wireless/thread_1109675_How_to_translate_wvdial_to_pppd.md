---
title: "How to translate wvdial to pppd?"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by felixdzerzhinsky on 2009-03-29
Is there an old sysadmin out there who remembers how to do pppd and who can translate my ubuntu wvdial.conf file into OpenSolaris pppd.

My ISP here seems to have changed something so I had to alter my wvdial.conf file. My working Ubuntu wvdial.conf looks like this:

```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99***1#
Username = "aa"
Password = "aa"
Stupid Mode = 0
```

With OpenSolaris it used to work like this:

[http://phnompenhopensource.wordpress.com/2008/10/28/connecting-to-star-cell-and-qb-gprs-in-phnom-penh-with-opensolaris/](http://phnompenhopensource.wordpress.com/2008/10/28/connecting-to-star-cell-and-qb-gprs-in-phnom-penh-with-opensolaris/)

I hope somebody can spot my mistake. 

I have also posted this on OpenSolaris Help forums but they are still not as active as Ubuntu's at this stage. And I know a lot of Ubuntu people know and use more than one Operating system.

[http://www.opensolaris.org/jive/thread.jspa?threadID=98218&tstart=30](http://www.opensolaris.org/jive/thread.jspa?threadID=98218&tstart=30)

---

