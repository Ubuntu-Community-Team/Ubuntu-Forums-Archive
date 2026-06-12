---
title: "Credentials for Samba client"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by buspital on 2010-11-11
I have an Ubuntu 10.04 file server with various shares set up on it. I connect to this using a desktop which dual boots Windows 7 and Ubuntu 10.10 (all 64 bit should that be relevant). 

I have the shares set up as mapped drives in Windows and can read and write to them fine. When I'm in Ubuntu I only have read access. I assume this is because Windows is using the proper user credentials and Ubuntu is connecting as a guest. 

Where can I set the user credentials to access the share in Ubuntu? I am just connecting through Nautilus and it never asks for any details.

---

### Post by luvshines on 2010-11-15
> **buspital said:**
> I have an Ubuntu 10.04 file server with various shares set up on it. I connect to this using a desktop which dual boots Windows 7 and Ubuntu 10.10 (all 64 bit should that be relevant). 

I have the shares set up as mapped drives in Windows and can read and write to them fine. When I'm in Ubuntu I only have read access. I assume this is because Windows is using the proper user credentials and Ubuntu is connecting as a guest. 

Where can I set the user credentials to access the share in Ubuntu? I am just connecting through Nautilus and it never asks for any details.

Try connecting through Places -> Connect to Server -> Choose windows share, enter ip, shared folder(optional), username/password

---

### Post by Morbius1 on 2010-11-15
I for one am confused by this one phrase:
> Windows is using the proper user credentials and Ubuntu is connecting as a guestIs the share set up as a guest share or does it require authentication?

Why not post the output of the following commands so we can see how you are set up:
```
net usershare info --long
``````
testparm -s
```There is a difference in how Windows handles the initial contact with a remote share and how Linux handles it but if the share requires authentication then it should prompt for one for a Linux client.

---

