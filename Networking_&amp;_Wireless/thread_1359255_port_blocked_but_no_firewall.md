---
title: "port blocked but no firewall"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by snacht on 2009-12-19
my server is configured as a dmz in my router. I have removed iptables, ufw. zenmap running in my subnet tells me most ports are still closed. [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) does as well. I'm not a linux/networking guru. how can these ports be blocked?
Thanks.

---

### Post by sanderj on 2009-12-19
Which port do you expect to be open? In other words: which 'server'-like software have you installed: a webserver, a samba server, a ftp server, or ... ?

---

### Post by Iowan on 2009-12-19
Not to argue semantics, but is the port blocked - or just not open?

---

### Post by snacht on 2009-12-21
> **Iowan said:**
> Not to argue semantics, but is the port blocked - or just not open?

uhh. Thanks for that.:oops:
Indeed. the port was not being blocked. There was simply no process listening on the port.

Thanks for the help.

---

### Post by Iowan on 2009-12-21
Well, glad to help with a solution - such as it was. :)
If the problem is [SOLVED], use Thread Tools to mark it as such.

---

