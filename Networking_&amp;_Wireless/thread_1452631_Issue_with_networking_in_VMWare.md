---
title: "Issue with networking in VMWare"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by Graham84 on 2010-04-12
Have just installed Ubuntu 9.10 in Vmware workstation 6.5.1 and unable to connect to external sites, or servers (using NAT). I can ping on host name and IP but can't resolve either host or IP in browser (Receive message the connection has timed out). I can't ping the host (Windows 7 Professional) IP from the guest and vice versa.

I use a mobile wireless network card, and my Windows operating systems work successfully in vmware.

Currently in my VMNet8 properties I just have Obtain IP address and DNS Automatically (same as host).

Any ideas? Host firewall also isn't blocking connections

---

### Post by 98cwitr on 2010-04-12
VMWare will use it's own internal DNS, not the one that your host is using. You will need to edit your resolv.conf or /etc/hosts file(s) in order to point to the proper DNS to resolve names correctly. You might need to set up port forwarding to communicate between the two networks, but try just editing the files first and see what happens :)

[http://www.vmware.com/support/ws5/doc/ws_net_nat_dns.html](http://www.vmware.com/support/ws5/doc/ws_net_nat_dns.html)

---

### Post by Graham84 on 2010-04-13
To connect to HTTP though? Names of external sites are resolving correctly with PING.

Tried editing host file, still nothing

Tried editing resolv.conf but wasn't entirely sure what to enter. Tried manually putting in DNS servers which the wireless card uses. Also tried setting static IP on VMNet8 to see if it makes a difference, and nothing..

---

### Post by Graham84 on 2010-04-13
Managed to get it working in VirtualBox instead, so guess I'll just keep using that! Thanks :)

---

