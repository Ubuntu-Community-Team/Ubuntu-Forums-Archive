---
title: "Can't create PID file /var/run/dhcpd.pid: No such file or directory."
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-06-27
There seems to be a problem with the dhcp server (isc-dhcp-server).

I can't get it to start.

```
dhcpd -f
```

gives me > Can't create PID file /var/run/dhcpd.pid: No such file or directory.

I don't think dhcpd.pid is supposed to be in /var/run but rather in /var/run/dhcp-server

I tried to google for this and found:

[INDENT][https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/985417]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/985417") [/INDENT]

which says this was supposedly fixed in the package isc-dhcp - 4.1.ESV-R4-0ubuntu5.1 and that is what I've got.

It seems to be the latest version.

This bug seems to go back several years but I can't find a fix.

Any help please?

AB

---

### Post by AlexBooton on 2012-06-28
Well I think I found a workaround but I wouldn't call this SOLVED b/c I'm not all that confident in my fix.

All I did was add the file:
```
-rw-r--r-- 1 dhcpd dhcpd 5 Jun 28 13:00 /var/run/dhcpd.pid
```

Is this the right way to fix this?

Thanks,

AB

---

### Post by piratox on 2012-07-08
Regarde de ce coté : [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/974054](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/974054)

---

### Post by AlexBooton on 2012-07-08
> **piratox said:**
> Regarde de ce coté : [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/974054](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/974054)

Thanks.  I saw the bug report which said it had already been fixed. But it wasn't fixed for me.

AB

---

