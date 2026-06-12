---
title: "How do I view users from my LAN on my local machine ?"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by dvlchat on 2011-11-23
Hello,

this is Ubuntu 11.10.

I'm on a LAN where many users have a local account on their machine. The accounts are exported by NFS and we have an LDAP server which contains user information. I've configured LDAP and checked that it works (I can ldapsearch on the server, and see entries for the remote users).

Where I'm stuck is how to view those users automatically as if they were local. For instance, I can't currently do "finger joe" or "cd ~joe" because there is no such user on my local machine. I will automount their directories later (I know how to do that). What I don't know is how to instruct my system to look for users in LDAP if they are not local.

Thanks in advance !

---

