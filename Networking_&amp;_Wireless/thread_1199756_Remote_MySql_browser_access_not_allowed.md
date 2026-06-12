---
title: "Remote MySql browser access not allowed"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by MalcolmCowen on 2009-06-29
I've got Ubuntu set up at client's site.  Works a dream, except that the MySql admin and browser utilities can't access the MySql database from the windows server which handles all the systems backups.

Apache works fine with the website.

PHP admin / browser utilities work fine as local host.

But PHP admin / browser utilities fail when accessing from remote Window system.

I've checked the Grant Privileges are OK for remote users.
I pinged so I know I've got the correct IP Address.

Are there any more things I need to set to make MySql accept connections from remote systems?

---

### Post by cyzak on 2009-06-29
I was facing the same problem. so someone sggested to change bind address in my.cnf to 0.0.0.0
</etc/mysql/my.cnf>
bind-address            = 0.0.0.0


I am not sure whether this will compromise security.

Thanks

---

