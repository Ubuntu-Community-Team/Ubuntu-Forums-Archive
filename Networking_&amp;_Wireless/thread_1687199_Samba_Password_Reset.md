---
title: "Samba Password Reset?"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by theamazingbeat on 2011-02-13
Hello All,
I somehow changed a setting or 2 and now anytime I try to access my ubuntu machine via my Windows Machine (Samba Server on Ubuntu Machine). Anytime I try to access the machine it asks me for my password...I enter it but it says it is invalid....is there anyway to reset it?

I have already tried to remove and purge everything Samba related and then tried reinstalling, but that still didn't do anything


Please help

---

### Post by Morbius1 on 2011-02-13
Just add the user-name to the samba database again:
```
sudo smbpasswd -a user-name
```It will ask you for sudo's password then it will ask you for the new samba password.

---

### Post by theamazingbeat on 2011-02-13
Thank You

---

