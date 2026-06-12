---
title: "Squid3"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by WhoopGetOut on 2009-02-05
So I have to be missing something.....  trying to set up Squid 3.0 running on Ubuntu 8.10 Intrepid in transparent mode.  The same server that is running Squid3 is also my router and firewall. 

If I set my browser to use a proxy port 8080 then all websites etc. get listed in the access.log file.  If I take the proxy out of the web browser then there is no more logging to the access.log file.  I have the following in my iptables which from everything I read should be all I need.
-A PREROUTING -p tcp -m tcp -i eth1 --dport 80 -j REDIRECT --to-ports 8080

Does traffic not get logged to the access.log file the same way if Squid is run in transparent mode, OR am I missing something???  Please help as it's driving me nuts.....  Thanks

---

### Post by WhoopGetOut on 2009-02-10
Nevermind I figured it out....

---

