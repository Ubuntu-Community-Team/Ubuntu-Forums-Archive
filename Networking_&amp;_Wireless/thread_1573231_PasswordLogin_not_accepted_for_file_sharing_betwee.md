---
title: "Password/Login not accepted for file sharing between two Lucid computers"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by CTenorman on 2010-09-12
Hi,

I've got Lucid running on two machines, with folders shared on each computer. I can browse to see the share on the other computer, but when I try to look inside it it says "password required for share pictures on X" I've tried using my login username and password for each computer (it's the same for both) and it doesn't work. I even created a new user account on both computers, but the user name an password for that account don't let me see the files either.

Can anyone help me figure out what I need to do to access the share on the other computer? Thanks!

---

### Post by wheredidrealitygo on 2010-09-12
Assuming you're using samba (SMB/server message block, aka the same file sharing windows uses) and not ssh, have you made sure to install samba itself and configure users for it?

```
sudo apt-get install samba
smbpasswd -a <username>
```

it'll then prompt you to add a password specifically for samba services.

hope that helps.

---

### Post by CTenorman on 2010-09-12
Ah, I hadn't configured users for Samba yet, thank you!

---

