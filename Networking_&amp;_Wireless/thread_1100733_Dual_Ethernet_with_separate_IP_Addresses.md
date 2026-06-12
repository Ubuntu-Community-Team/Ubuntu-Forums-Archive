---
title: "Dual Ethernet with separate IP Addresses"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by jamesab on 2009-03-19
Hello everyone,

I'm having a problem using 2 NIC's on the same server (ubuntu 8.10).  I can only get 1 OR 2 to work, but not 1 AND 2 at the same time. I have an ISP that allows 3 IP addresses per account, and 2 are to be used by the server and 1 for the wireless router.  All 3 are connected to an ethernet network hub.  The IP's are assigned by my ISP's DHCP.  The router pings OK and eth0 pings OK, but eth1 ping times out.  If I "sudo ifdown eth0", then I am able to ping eth1 OK.  If I then "sudo ifup eth0" then I am able to ping eth0 again but not eth1.

Is there any way to use both cards with separate IP's at the same time?  For example, I want Apache to see both IP addresses and use them for Virtual Host directives.

Thanks in advance.

---

