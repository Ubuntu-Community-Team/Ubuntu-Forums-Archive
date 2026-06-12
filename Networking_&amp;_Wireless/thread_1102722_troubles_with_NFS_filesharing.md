---
title: "troubles with NFS filesharing"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by bigbencg on 2009-03-21
I am trying to set up file sharing with NFS.

When I specify the share in /etc/exports I am trying to set my netmask at 50 addresses.

*/thor 192.168.1.0/50(rw,async)*

After saving the file and running *exportfs -a*, I get an error stating invalid netmask.

```
bigben@8151-KUBU:/$ sudo exportfs -a
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' 
specified for export "192.168.1.0/50:/thor".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: invalid netmask `50' for 192.168.1.0
```

Any netmask value over 25 returns that error.  Why???

Is it really necessary, or is it possible to, enter seperate lines for every 25 addresses?

*/thor 192.168.1.0/25(rw,async)*
*/thor 192.168.1.25/25(rw,async)*

I would like to avoid making my exports files to complicated, this is starting to remind me of my NT4.0 lmhosts days :-&

---

