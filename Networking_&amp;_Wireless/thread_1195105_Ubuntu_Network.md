---
title: "Ubuntu Network"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by marsdend on 2009-06-23
Hi all,

Im wondering if this is possible and a difficulty level.

Im wanting to use Ubuntu Server 9.04 on a dedicated home server with the following features:

 * Multiple Clients (2 Ubuntu 9.04, 1 Windows XP)
 * 3 User Accounts but with access from all 3 Clients (eg. Log in and documents and maybe settings follow)
 <edit: User account stored on server and acess that from PC>
 * If user changes password on PC1 they can log onto PC2 with the same password
 *Backup Solution for Files

Thanks in advance,
Dan

---

### Post by MaindotC on 2009-06-23
It's not difficult, but it's a ton of reading.  I believe what you want to use is something called LDAP.  Installing LDAP on your server machine will allow other clients on the network to check with the LDAP server (for authentication) upon logging in.  As for backup solution you can use rsync (along with multiple other programs) for backing up specific files or directories, or you can do backups of the entire disk image of a machine with partimage or ghost4linux.

---

