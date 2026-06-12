---
title: "Can not connect BSNL connection in Ubuntu 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by sahilnanda on 2009-11-01
I have a BSNL (Home unlimited 750) internet connection. The make and model of my internet modem is : SmartAX MT841.

I made a DSL connection like i used to do in Ubuntu 9.04 but it is not working in 9.10.

Help if anyone knows what the problem is.

---

### Post by Dexter_Greycells on 2009-11-01
Even my MTNL connection (2 MBPS, ADSL router) is facing issues.
Problem seems to be with the use of IPv6. I am still trying to resolve it as of now.

A quick fix for Firefox is to enter about:config in the address bar, find a key with IPv6 in it and set it value to true from false. In other words, you are telling Firefox to use IPv4 instead of IPv6. This only fixes the problem for Firefox. All other apps (Ubuntu software center, synaptic, Empathy, apt-get, update-manager) can't connect to the internet though.

---

### Post by alanrr_sr on 2009-11-01
There is a problem with Network Manager and DSL connections. Could this be the problem?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)

Other threads
[http://ubuntuforums.org/showthread.php?t=1308794&highlight=dsl](http://ubuntuforums.org/showthread.php?t=1308794&highlight=dsl)


Add on: If you use pppoe-conf, u can have problem with empathy also...

---

### Post by madhav165 on 2009-11-01
Refer to the solution by bogdan in [http://ubuntuforums.org/showthread.php?p=8213343](http://ubuntuforums.org/showthread.php?p=8213343). Should work till the bug ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)) is fixed. Some reported that connecting to empathy would be a problem with this workaround. I was able to connect though. ;). Change eth0 connection from manual to dhcp in /etc/network/interfaces.

---

### Post by Arup on 2009-11-01
I have BSNL with Netgear DG632 and I am yet to face any issues related to IPV6, the only glitch is that Google Talk and Google services like Orkut sometimes time out.

---

### Post by Dexter_Greycells on 2009-11-02
As I said earlier, I use an MTNL 2MBPS connection making use of an ADSL+ router to connect to the Internet and a Netgear router for home networking.
My problem has been temporarily resolved through the use of OPENDNS.
Here is the link -
[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

This was suggested in Launchpad and Ubuntuforums. Hope this helps.
Thanks,
Dexter_Greycells

---

