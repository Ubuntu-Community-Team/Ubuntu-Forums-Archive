---
title: "iptables do not work the way it should on 10.04"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by marchost on 2010-08-14
Hi all, i'm having a weird issue on 10.04. I have a bash script I wrote to drop incoming connections that are faster than a specified rate (6 per second in the example). I've been using the script successfully on 8.04LTS and CentOS for 2-3 year but it doesnt seem to work on 10.04 :(

```

INTERVAL="2"
HITCOUNT="6"

iptables -A INPUT -d 123.123.123.123 -m state --state NEW -m recent --set
iptables -A INPUT -d 123.123.123.123 -m state --state NEW -m recent --update --seconds $INTERVAL --hitcount $HITCOUNT -j DROP

```

Thanks in advance

Marc
IPInfoDB

---

### Post by marchost on 2010-08-14
My mistake... fixed

---

