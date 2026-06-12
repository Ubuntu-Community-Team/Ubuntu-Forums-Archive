---
title: "remote authentication against a tdbsam backend"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by jimmybarcelona on 2010-09-15
There are many articles on using kerberos or openldap for authentication, but I cannot find anything on how to setup a ubuntu 10.04 client to authenticate to a remote samba server using the tdbsam backend instead of ldap. I have less than 70 users, so I think the tdbsam database would work fine and require less overhead than kerberos or openldap.

I know how to add users to the samba database, and libpam-smbpass will sync unix and samba passwords, so I'm set there. But how in the world do I configure a client to authenticate against a samba database?

---

