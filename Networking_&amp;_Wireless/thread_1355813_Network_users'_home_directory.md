---
title: "Network users' home directory"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by cckid on 2009-12-15
Hi all,
I've searched various places and didn't see a thread that exactly matched my question so I thought I'd ask here.
I have Ubuntu 9.10 configured in such a way that users from our organization's central authentication server can log in.  This is a Kerberos+LDAP setup.  I've been able to get it working and am working out the kinks.
The current kink is redirecting the users' to a local home directory instead of the one listed in their LDAP entry.  Right now, when a user logs in their home is set to be "/net/users/xx/x/userid/" but I would like to to be something like "/home/userid".  I'm not sure where to go or what to look for to make this happen.  
Can anyone help by pointing me in the right direction?

---

