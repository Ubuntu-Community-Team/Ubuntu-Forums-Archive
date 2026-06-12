---
title: "Pass all packets from eth0 to eth1 ??"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by nasiriyah on 2009-03-20
Deal all

I have server with two network interfaces.
How can I pass or forward all the packets from eth0 to eth1 by iptables or any other way?


Regard

---

### Post by balloooza on 2009-03-20
If you have a server, you could benifit from a web administration platform like this one (runs on ubuntu)

[http://ebox-platform.com/](http://ebox-platform.com/)

the screenshots are outdated, to install

[http://ebox-platform.com/community/installation-guide/](http://ebox-platform.com/community/installation-guide/)

it is nice, and automagicly configures everything.

---

### Post by nasiriyah on 2009-03-20
Thank you for the fast answer, but in simply, I'm new researcher in networking and I need to capture all the packets from the source machine which pass through Ubuntu machine (the server) to the destination machine, where the destination machine contain wiresharke software.

Regards

---

### Post by nasiriyah on 2009-03-21
Thanks for the God.
I found the answer, by type
>>sudo -i
>>echo 0> /proc/sys/net/ipv4/conf/eth0/rp_filter
>>echo 0> /proc/sys/net/ipv4/conf/eth1/rp_filter


And after that I can capture all the packets in the destination machine which sent from the source machine through the server



Regars

---

