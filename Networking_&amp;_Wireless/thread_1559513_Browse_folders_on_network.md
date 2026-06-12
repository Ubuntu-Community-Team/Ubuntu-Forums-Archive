---
title: "Browse folders on network"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by aytech on 2010-08-23
Hello, 
My problem is that I cant browse network shares in programs (like GRsync, for example)
I want to sync files on local computer with the NAS, of course over Network - Share_Name i can open and browse files on NAS,  but in the program i dont have the option to set server as left folder.
OS - Ubuntu 10.04

I wonder if there's a workaround i could use, 
Thank you, 
Oleg

---

### Post by aytech on 2010-09-10
I found a way to browse the files on the network from rsync gui, not sure if thats the best one: 
I mount the network drive with the command 
smbmount //smb/share /home/user/share -o username=smbusername, password=smbpassword
 
Share is the folder I created in home directory. 
It works fine, but I have to do it manually every time I logon. Is there a way to automate this task?
 
Thanks for any help

---

### Post by dmizer on 2010-09-10
The best way is to mount the network shares as local drives as outlined in the second link in my sig.

---

### Post by aytech on 2010-09-10
> **dmizer said:**
> The best way is to mount the network shares as local drives as outlined in the second link in my sig.
@dmizer: thanks for the tip, i will try it this way..

---

### Post by aytech on 2010-09-11
@dmizer: Worked like a charm, many thanks for the info, great help!!

---

