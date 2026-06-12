---
title: "Unusual unsolicited download from Canonical"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by sujop on 2012-04-27
I installed Ubuntu 12.04 LTS yesterday. Since then I have noticed that my computer is constantly downloading from 91.189.89.76 and 91.189.89.114 on port 443 . Setting up firewall rules to deny connections to and from these IP address makes not difference. The only way to stop this is to disconnect the system from the internet. Is anyone experiencing the same?

---

### Post by chili555 on 2012-04-27
I suspect this is Network Time Protocol.```
$ ping -c3 [COLOR="Red"]ntp[/COLOR].ubuntu.com
PING ntp.ubuntu.com (91.189.94.4) 56(84) bytes of data.
64 bytes from europium.canonical.com (91.189.94.4): icmp_req=1 ttl=43 time=99.3 ms
64 bytes from europium.canonical.com (91.189.94.4): icmp_req=2 ttl=43 time=98.9 ms
64 bytes from europium.canonical.com ([COLOR="Red"]91.189[/COLOR].94.4): icmp_req=3 ttl=43 time=99.2 ms
```That's how your computer has the correct time within a few tenths of a second.

---

### Post by sujop on 2012-04-27
It is certainly not NTP. The traffic that I see is encrypted traffic. I used Wireshark to see what was going on.  The funny thing is that setting firewall rules to deny all the traffic in and out makes no difference.

---

