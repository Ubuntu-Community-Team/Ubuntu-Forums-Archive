---
title: "seting up a router"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by dmshade3 on 2011-01-17
I am trying to setup a router using Ubuntu server 10.10.

I want it to pass everything - including dhcp relay.

I have 2 nics and both work.  One is connected as 172.16.200.125 and is the "external" nic.  I access the internet via this connection.  One is connected as 172.17.1.1 and is connected to a switch with another pc on it.

I have dhcp3relay installed and configured to match the above, pointing to a proper/working dhcp server.

I can ping form the workstation (172.17.1.200) to the 1.1 AND to the 172.16.200.125 successfully.  But, I cannot ping beyond that.  Additionally, dhcp relay is not working.

I have Webmin installed and have enabled (sysctl.conf) packet forwarding.  I have also setup 3 rules in iptables via webmin - accept everything - in , out ,  forward.

I have checked/double checked each setting and restarted the networking and even rebooted.

If I modify the rules to reject on 172.17.1.1 it does so appropriately.  If/when I re-enable the accept it works as before - request timed out.

Any suggestions?

Thanks in advance!

Mark

---

