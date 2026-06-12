---
title: "Samba port?"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by jahisthebalance on 2009-01-24
I was wondering if samba shares run on a specific port, and if I would need to open that up in ufw for them to work.  Does anyone know of a comprehensive FAQ or anything like that?

---

### Post by jgoguen on 2009-01-24
Samba runs on TCP ports 139 and 445 and UDP ports 137 and 138.  If you want to run a Samba server, the firewall on that box would need to be open to allow those ports in.

The most comprehensive setup I know of is the community docs: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jahisthebalance on 2009-01-25
thanks man

---

