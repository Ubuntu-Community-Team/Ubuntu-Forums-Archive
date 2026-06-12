---
title: "One more question regarding Samba"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by DeusExM1 on 2009-05-09
So i managed to set up samba so that i could access my own computer on the network. (And other windows computers see mine).

The only problem is that i cannot browse (although i see them !) other windows machines on the network. I am prompted for a username and password when i double click any other computer. The other computers are not password protected and file sharing is enabled.

So are there any ways to fix this?

---

### Post by rick71 on 2009-05-09
I am also having problems actually connecting to Samba shares on the network, even though the Windows machines can connect fine.

---

### Post by cariboo on 2009-05-09
Have you set your user passwd for samba:

```
sudo smbpasswd -L -a <username>
```

and enable the user

```
sudo smbpasswd -L -e <username>
```

---

### Post by DeusExM1 on 2009-05-09
wow i cant believe that worked! I can now browse through the Public folder on other machines. Damn i cant believe it only was necessary to do that.

Thanks a lot !!!

---

### Post by rick71 on 2009-05-10
> **cariboo907 said:**
> Have you set your user passwd for samba:
```
sudo smbpasswd -L -a <username>
```
and enable the user
```
sudo smbpasswd -L -e <username>
```

Yes, I have.
I can access by IP, but not hostname.

---

### Post by rick71 on 2009-05-11
I can access by smb://ipnumber/shre in Nautilus, and I can access by mounting as an smbfs by ip and hostname, but I can't access by hostname or by clickingon the icons in Nautilus.

---

### Post by rick71 on 2009-05-11
I have installed Jaunty. Nautilus/Samba/Network seems to be running "properly".

---

