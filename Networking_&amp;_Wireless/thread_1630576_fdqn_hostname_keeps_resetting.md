---
title: "fdqn hostname keeps resetting"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by dcompiled on 2010-11-25
I have a strange problem with my hostname resetting every few minutes.  My hostname was hostx.blah.com and I wanted to change it to hostx.blah.org.  I made the changes to /etc/resolv.conf adding lines

search blah.org
domain blah.org
nameserver 10.0.0.1

But it keeps resetting itself back to this after a few minutes

search blah.com
domain blah.com
nameserver 10.0.0.1

Some software I am running on the machine includes postfix (local only) a bind server, mysql and apache.  The system has a static ip and also plugged into a cable modem.  I do not believe the DHCP from the cable modem is to blame but I cant be sure.

---

