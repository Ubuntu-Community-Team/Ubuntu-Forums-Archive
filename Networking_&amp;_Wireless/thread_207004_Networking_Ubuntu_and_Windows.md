---
title: "Networking Ubuntu and Windows"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by deweese on 2006-07-01
I have networked my dual boot laptop of Ubuntu 6.06 and Win Xp to a
Windows Server.  I have configured it so I can see the files on the server with both Linux and Windows.  On the Windows XP Server, I see the Ubuntu Laptop
but it asks for a user name and password to access it. What should I put?
The username and password that I log into Ubuntu with doesn't work.
I have no other pwd except my root password.

---

### Post by bigken on 2006-07-01
open console and type *sudo smbpasswd -e* (yourname) 
enter new passowrd 
then type *sudo smbpasswd -a* (yourname)
and last of all type *sudo /etc/init.d/samba restart* 



hope you find this helpful ;)

---

### Post by deweese on 2006-07-01
It worked perfectly!  You are very helful! Thanks!

---

