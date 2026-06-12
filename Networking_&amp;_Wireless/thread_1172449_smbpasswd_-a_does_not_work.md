---
title: "smbpasswd -a does not work"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by shade5 on 2009-05-28
Hello, 
I got problems with the Samba command smbpasswd for creating samba user accounts. 

```
sudo smbpasswd -a user
```

should create a new user entry in /etc/samba/smbpasswd. But there is no such file. I think the cmd should create the file if it doesn't exist. On my other computer I got the file. I am using samba 3 on both. But not sure if it also got the same subversion number. How do I find it out?

And how can I create the file with the entry?

Thanks.

---

### Post by capscrew on 2009-05-28
> **shade5 said:**
> Hello, 
I got problems with the Samba command smbpasswd for creating samba user accounts. 

```
sudo smbpasswd -a user
```

should create a new user entry in /etc/samba/smbpasswd. But there is no such file. I think the cmd should create the file if it doesn't exist. On my other computer I got the file. I am using samba 3 on both. But not sure if it also got the same subversion number. How do I find it out?

And how can I create the file with the entry?

Thanks.

Samba 2 and early Samba 3 (< 3.023) used /etc/samba/smbpasswd.

Samba > 3.023  uses /var/lib/samba to hold the various tdb.

See: [_**http://samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html#id2592512**_]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html#id2592512")

---

