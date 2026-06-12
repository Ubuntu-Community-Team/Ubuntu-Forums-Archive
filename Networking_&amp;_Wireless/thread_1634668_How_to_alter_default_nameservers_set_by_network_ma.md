---
title: "How to alter default nameservers set by network manager?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by rlp1938 on 2010-11-30
The default name server set by network manager works just fine much of the time but there are times when it slows down badly. What I want to do is to have network manager add extra nameservers to the list when it starts the network.

Thanks Bob

---

### Post by SeijiSensei on 2010-11-30
If you have control of the DHCP server (presumably in your router), you may be able to add them there.  If not, you can edit (as root using sudo) /etc/dhcp3/dhclient.conf and use the "prepend domain-name-servers" directive. Note that this will put the ones you enter ahead of the one you get from DHCP.  If you want them placed after the DHCP-supplied entries, use "append" instead.  See "man dhclient.conf" for details.

---

### Post by rlp1938 on 2010-12-01
> **SeijiSensei said:**
> If you have control of the DHCP server (presumably in your router), you may be able to add them there.  If not, you can edit (as root using sudo) /etc/dhcp3/dhclient.conf and use the "prepend domain-name-servers" directive. Note that this will put the ones you enter ahead of the one you get from DHCP.  If you want them placed after the DHCP-supplied entries, use "append" instead.  See "man dhclient.conf" for details.

Thanks for this help.
1. I have no control of the DHCP server so I have done the job by editing /etc/dhcp3/dhclient.conf

2. I appended the following line to that file:
append domain-name-servers 8.8.8.8, 8.8.4.4;
and it has just worked.

---

