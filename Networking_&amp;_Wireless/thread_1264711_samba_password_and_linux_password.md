---
title: "samba password and linux password"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by david90 on 2009-09-12
Is there a way to automatically create samba user/password when I create a linux user/password?

Why is there two different passwords?  why can't samba just use the linux password?

---

### Post by swerdna on 2009-09-12
Q1: AFAIK there isn't

Q2: Why? to give greater flexibility and security

Q3: you can use the Linux password if you like, or any other password.

---

### Post by zman58 on 2009-09-12
I have not tried this, but it looks like samba and pluggable authentication module (PAM) supports using the UNIX password instead of the samba password when mounting samba shares.

I believe this samba option should do what you want...
[INDENT]unix password sync = yes[/INDENT]

I found some additional information that might help. It looks interesting and there is also a warning about the root account you might want to pay close attention to.

[http://jaka.kubje.org/2007/05/14/unix-samba-password-sync-on-debian-etch/](http://jaka.kubje.org/2007/05/14/unix-samba-password-sync-on-debian-etch/)

---

