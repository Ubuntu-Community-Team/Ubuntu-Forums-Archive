---
title: "[Precise\12.04] Restart network-manager every time I plug in ethernet"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by grounds on 2013-08-29
I recently updated my Netbook (ACER Aspire One AO521-3530) from 10.04 netbook revision to full 12.04 Desktop ubuntu.

Since I upgraded, network-manager has been doing some funky things.
First off, when booting I get the failsafe.conf run messages, I have been able to troubleshoot these via this thread ([http://www.howtoforge.com/forums/showthread.php?t=57545](http://www.howtoforge.com/forums/showthread.php?t=57545))
I simply decreased the timers. It's a simple solution but I fear there is a more important issue at hand here. Now I am satisfied with my boot times.

However, when ever I plug in an ethernet cable, nothing happens. If I restart the network-manager service, all works fine!
After I restart the service, I can connect, reconnect, plug in or take out any network connections at will and the service seems to figure it all out without problem.

It's a minor inconvenience, and I'm not entirely fond of start-up scripts to restart the network manager on boot or something silly of the sort. I am just curious as how to further troubleshoot this issue. Maybe if I can get network-manager to load properly on initial boot, then failsafe will not run at all and my network will be fine. I'm not looking for a hackjob solution here, I'm more interested in learning at least *why*&#8203; this is happening.

So does anyone have any ideas of why this is occurring, or could anyone point me to the process in initialization that will fire off failsafe.conf so I can figure out why It's throwing "[COLOR=#000000][FONT=verdana]waiting for network configuration" etc.
[/FONT][/COLOR]

---

### Post by GwL3eNC on 2013-08-29
Hello,

possibly you can find some information in the /var/log/syslog file. It's long and i dont know
all things in there, but if you 

cat /var/log/syslog | grep net
cat /var/log/syslog | grep wlan0
cat /var/log/syslog | grep dhc

you can see something about network-manager and other network events. Hopefully an error message that helps you.

---

