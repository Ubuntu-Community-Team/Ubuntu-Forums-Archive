---
title: "Linux to Mac OS 10.4 ok, Mac to Linux zip"
date: 2006-05-23
forum: Networking &amp; Wireless
---

### Post by Uta on 2006-05-23
I'm running Ubuntu 5.10, with Samba up and running on my Dell laptop (wireless yipee!), I can see my G5 on the network and read/write to it's shared folder but when my Mac sees Ubuntu and I try to connect from the Mac side, I get the dreaded spinning ball. I have setup up a shared folder(drwxrw) on my Linux desktop, configured smb.conf, what now? Do I need to ID my G5 as a user somewhere?
Thanks!

---

### Post by jlhughes on 2006-05-24
On my network I had a similar problem. The Ubuntu box (called Ubuntu on the network) had no trouble finding the Mac using either the network name IMAC or the IP address. Going from the Mac to the Ubuntu box, didn't work until I figured out that the Mac wants the user account and the machine name.

So, smb://Ubuntu gets nothing but smb://Ubuntu/john connects.

---

### Post by Uta on 2006-05-24
Thank you for your info and yes the usename gets a prompt but after putting in the password I get:
"The operation can not be completed because one or more required items can not be found" Error code -43
?

---

### Post by joanverde on 2007-05-07
I've got the same problem with error code -43! what to do?

---

