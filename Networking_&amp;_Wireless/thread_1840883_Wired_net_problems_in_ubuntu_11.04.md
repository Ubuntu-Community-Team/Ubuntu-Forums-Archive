---
title: "Wired net problems in ubuntu 11.04"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by Firecast on 2011-09-08
I recently installed ubuntu 11.04 and had no problems with the net for a day. However from the next day on the net seems to connect for 10 sec and then doesnt work at all. To make it work i have to refresh the eth0 and the cycle repeats itself.

I know its not the browser issue because i tried with different browsers. Plus the network icon on the upper right says that the net is working fine even though i cant browse the net and none of the net clients work too.

I really don't want to reinstall ubuntu. Can someone suggest me how to revert back to system default settings or even a solution to my problem......plz......

---

### Post by Wayne_V on 2011-09-08
I would start by monitoring the log files:

$ sudo tail -f /var/log/{dmesg,*log}

also, when check the config when the net is working and when it is not:

$ ifconfig -a
$ route
$ netstat -s
$ sudo ethtool eth0
$ sudo mii-diag -v eth0



you might also try monitoring link status:

$ sudo mii-tool -w eth0

---

