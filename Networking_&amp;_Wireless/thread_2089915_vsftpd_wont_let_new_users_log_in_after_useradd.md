---
title: "vsftpd wont let new users log in after useradd"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by mushy365 on 2012-11-30
Hi, i have a vsftpd server running and i can log in using my main account. However, if i do a useradd command 

i.e : useradd -m -k /etc/skel -N -s /bin/false -g websiteowners -p 123 newuser

the user adds fine and shows up in /etc/passwd
however the user cannot login to vsftpd

I have tried restarting vsftpd, but i still get the same error.

---

