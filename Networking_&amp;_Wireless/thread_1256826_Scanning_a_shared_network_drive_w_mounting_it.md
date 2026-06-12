---
title: "Scanning a shared network drive w/ mounting it"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by sa125 on 2009-09-03
Hi - I need to scan some files on a network server machine from my own (w/ python). So far I have been doing it by mounting that folder on my machine and processing it. Both machines are running linux and reside on the same local network. 

I know that in Windows, one can access a network folder by simply specifying \\server\folder address, and I wanted to see if there's something similar in linux (in concept), that would not require using a mount.

---

### Post by df6269 on 2009-09-03
If samba client has been installed in your machine, you can use this way to reach network share folders
smb://ipaddress or netbios name/share folder

---

### Post by sa125 on 2009-09-03
> **df6269 said:**
> If samba client has been installed in your machine, you can use this way to reach network share folders
smb://ipaddress or netbios name/share folder

Thanks for the reply. What you suggest works great from nautilus, but what about accessing it through the command line?

---

