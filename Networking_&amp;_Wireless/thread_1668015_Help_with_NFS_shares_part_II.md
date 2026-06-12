---
title: "Help with NFS shares part II"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by jpaulb on 2011-01-15
I have a desktop box, 3 laptops running Ubuntu 10.10. using the wireless connection.

The laptops are used while on the road, desktop is used by me at home, for laptop backups, sharing picture and videos.
The desktop has all the accounts set up, while the laptop has only one account that of it´s user.
How do I march the laptop user accounts to the desktop users accounts?
On the desktop, user 1 =1000, user 2=1001, user 3=1002 however on the laptop each user is 1000, this seems to cause confusion about ownership.

I hope I have explained this, ´cause I am a bit confused about this also.

---

### Post by SeijiSensei on 2011-01-16
The simplest solution is to replicate /etc/passwd, /etc/group, and /etc/shadow on all the machines.  Then they'll have the same user-to-uid mappings.

If you want to prohibit user2 from logging in on user1's machine, you can set the shell for user2 to /usr/sbin/nologin in /etc/passwd like this:

```
user2:x:1001:1001:USER2,,,:/home/user2:/usr/sbin/nologin
```

---

