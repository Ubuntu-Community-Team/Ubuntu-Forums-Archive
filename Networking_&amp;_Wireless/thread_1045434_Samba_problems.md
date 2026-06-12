---
title: "Samba problems"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2009-01-20
I'm trying to mount my Download folder on my laptop and it says, "unable to mount Windows share". Both machines are Ubuntu and samba seems in order. Any suggestions would be helpful.

UPDATE: I'm able to mount my desktop and copy the file to it, haven't tried my server yet.

UPDATE #2: My server can't access my laptop either.

---

### Post by theozzlives on 2009-01-21
Bump

---

### Post by dmizer on 2009-01-21
To allow other computers to access shares on your Ubuntu computer, see the first link in my sig.

To access Windows shares on other computers from your Ubuntu computer, see the second link in my sig.

---

### Post by theozzlives on 2009-01-22
> **dmizer said:**
> To allow other computers to access shares on your Ubuntu computer, see the first link in my sig.

To access Windows shares on other computers from your Ubuntu computer, see the second link in my sig.

I know how to access shares, it just won't!

---

### Post by dmizer on 2009-01-22
Okay, then what is your /etc/fstab line?

Also, please install smbclient, and post the output of:
```
smbtree
```

Do you have any firewalls in place on either Ubuntu or Windows?

---

