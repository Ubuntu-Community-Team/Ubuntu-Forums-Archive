---
title: "Networking (wired) stops after about 5 minutes"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by bwolthuis on 2009-02-19
Hi there,

Moved my NAS server over from fedora 7 to Ubuntu Server 8.10. So far I'm not able to use it, as networking stops after about 5 minutes, when copying from an XP machine over SMB to the server. After stopping, pings to the server fail, ssh to the server stops, etc. Pinging form 2 other machines also fails, so I rule the XP machine out for being faulty.

Replacing the server's NIC gave the same result.

When logged on to the server console everything seems ok. No entries in /var/log/messages, regarding the networking. After issueing a ping from the server to the outside everything is back OK.

How can I detect and solve this problem?

Regards,
Bert

---

