---
title: "Filesharing folder on Ubuntu that Mac can access"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by tharpa on 2011-04-17
I have a folder on Ubuntu that I would like to share with my Mac laptop.  (I am able to share a folder from my Windows drive to my Mac.)

How do I do this?

---

### Post by Morbius1 on 2011-04-17
Pretty much the same way you did it on Windows:

Open Nautilus ( Your Home folder )
Right click a folder you own say ... Documents
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

---

### Post by tharpa on 2011-06-18
> **Morbius1 said:**
> Pretty much the same way you did it on Windows:

Open Nautilus ( Your Home folder )
Right click a folder you own say ... Documents
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

'net usershare' returned error 255: net usershare add: failed to add share documents. Error was Operation not permitted

---

### Post by Morbius1 on 2011-06-18
2 possible reasons:

[1] You are not a member of the correct group so add yourself:
```
 sudo gpasswd -a your_user_name sambashare
```
Then logoff and login again.

[2] You already shared it as someone else - probably root:
```
ls -al /var/lib/samba/usershares
```
This will show you if "documents" is already there and who owns it.

---

