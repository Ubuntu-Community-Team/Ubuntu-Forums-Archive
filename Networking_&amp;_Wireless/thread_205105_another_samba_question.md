---
title: "another samba question"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by kikingm on 2006-06-27
can someone point me a tutorial or something similar that will able to solve folder sharing problem? :confused: 
okey i have two shared folders, first folder will have an authentication to be able to access it, user/password dialog box will appear in winxp/2000/98,  the other one will have no authetication, just point and click no more user/password dialog box in winxp/2000/98. can this be done?:-k

---

### Post by kikingm on 2006-06-28
oh well it seems nobody has the answer or it is not posible to configure like that. may be this is one of the limitation of samba:confused: ](*,)

---

### Post by bforbes on 2006-06-28
You need to wait more than 2 hours for a response sometimes.

Add to the entry in smb.conf:
```

guest ok = yes

```

---

### Post by kikingm on 2006-06-28
oh okey sorry if im in a hurry.
ive already try that, the user/password is still keep on poping in winxp

ive set security=user and the folder that has suppose to have no authentication will have a authetication pop-up screen

setting security=share and the other folder have an pop-up that says the user has server/guest on it but can't be modified and if i tried to supply it with a password it keeps on poping. i have added guest account in smbuser/smbpassword

---

### Post by bforbes on 2006-06-29
Every smbuser must have a linux account as well. Try adding the user "guest" to your linux box.

A possible solution to your problem is to run a batch file that mounts the passwordless share as a network drive.

---

