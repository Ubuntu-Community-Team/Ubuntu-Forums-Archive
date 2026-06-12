---
title: "Network manager and DNS server"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by jmarc on 2009-12-30
Is there a way to *add* a DNS server to those which are found by DHCP (I can *substitute* mines to those found by DHCP in the NetworkManager but not add one).

Yours,

-- 
Jean-Marc

---

### Post by puppywhacker on 2009-12-30
You can prepend or append the information in the file /etc/dhcp3/dhclient.conf

```
prepend domain-name-servers 192.168.1.1;
```

---

### Post by jmarc on 2009-12-30
Thanks for the hint.  If I'm not mistaken, this will be done for all DHCP lookups.  In a perfect world, I'd like to get the same effect only for some connections.

---

### Post by Iowan on 2009-12-30
What do you mean by "only for some connections."?  If only certain clients are to use the specified DNS server, they are the only ones to have their dhclient.conf file modified. Do you want to use one DNS server to look up certain sites - and another for different sites?

---

### Post by jmarc on 2009-12-31
By "connection" I mean what the Network Manager Applet mean by Connections.

If I right click on the network manager applet, I have a menu "Edit connections" and there I may create several configurations.  For some of them I've a static setting, for other I want dhcp settings but also referring an additional name server, and for some other, I just want what DHCP gives me.

---

### Post by Iowan on 2010-01-01
Thanks for explanation - I think I understand what you mean... and yes, I suspect the effect would be the same for all connections.

---

