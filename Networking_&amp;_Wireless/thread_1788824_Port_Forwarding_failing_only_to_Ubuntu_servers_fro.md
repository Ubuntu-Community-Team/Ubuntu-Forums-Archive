---
title: "Port Forwarding failing only to Ubuntu servers from Draytek router"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by Simon L on 2011-06-23
We have a Draytek 2820n router connected to the internet, and a number of servers inside the network which are exposed to different degrees to the internet.

The windows servers are working fine with port forwarding, allowing access to the exchange server perfectly.

We have an asterisk pbx based on centos (on vmware esxi) which is on a dmz, but locked down well. These are great.

We also have a number of minimal Ubuntu servers, 10.04.2 LTS, also on vmware esxi. When I set these Ubuntu servers up with either port forwarding or on the DMZ, they work for a while, then after a random period of time, anywhere from 4 hours to 20 hours, I am unable to access the servers from the internet.

All of the servers (windows, centos and ubuntu) have been set up with static IP addresses, and all of the servers can be accessed at all times from within the network.

Connecting to the router to monitor its interfaces appears to show it sending out data as normal, and wireshark on the ubuntu servers shows a big pile of nothing.

If anybody has any suggestions as to what I'm missing, I'd really appreciate it.

Simon

---

### Post by TheRufinus on 2011-06-29
you are not alone, same problem here. nmap shows the ports are closed after a while, no matter if DMZ or port redirection. I'm in contact with draytek support your hint it only happens with ubuntu might help to resolve this. thanks.

rufinus

---

### Post by TheRufinus on 2011-06-29
i just set up a naked debian on vmware esxi and configured a DMZ on the vigor for it. 

surprise!!! its working.

so the question is, what does ubuntu makes diffrent from debian. Via its internal ip all works as expected, but with the port redirect it stops working after a short period of time, but it seems only on ubuntu.

Rufinus

---

