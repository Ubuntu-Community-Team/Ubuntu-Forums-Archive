---
title: "Able to connect to router, but not internet"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by Nanamika on 2009-03-25
I'm not able to connect to the router wirelessly, and internet is functioning when using ethernet.
I am granted an ip address according to iwconfig.

I have tried multiple networks, both at home and on campus. All lead to same results, able to connect but yields zero internet connectivity.
Not able to resolve any ip address or hostname when using ping, and all web browser access leads to timing out.

---

### Post by Cheesehead on 2009-03-25
After you next try to connect, please open a Terminal, and paste to this thread the output of the following command:```
tail /var/log/syslog
```

---

