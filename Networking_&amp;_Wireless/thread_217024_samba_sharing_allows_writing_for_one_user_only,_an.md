---
title: "samba sharing allows writing for one user only, and not other users"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-07-16
So here is my Ubuntu setup. 

Install samba and smbfs. Edit /etc/samba/smb.conf to allow "writeable=yes" and browse of home directories. 

Basically have 3 users, harisund, entertainment and executables. harisund is my regular personal stuff, entertainment is the collection of songs and movies, executables is the old .exe files for my Windows machine which are not available on the internet anymore. 

I restart samba and go to my windows machine on the same network. type in \\192.168.0.83\harisund, \\192.168.0.83\entertainment and \\192.168.0.83\executables and all good. I can access each one. 

However, if I try to create anything in harisund it works, but in entertainment and executables I am not able to create anything (as in create a text file, save a text file there, copy and paste a folder into it etc).
 
As far as I can see, all permissions are identical for harisund,entertainment and executables. Even samba's writeable directive is switched on. 

If it matters, my user name in my Windows machine is hari. And they are on the same workgroup as well.

Any ideas?

---

### Post by rbalfour on 2006-07-16
check the linux permissions on the folder.

Make sure the users are in the proper group with rw access. Linux STILL controls who can write to the filesystem..

---

