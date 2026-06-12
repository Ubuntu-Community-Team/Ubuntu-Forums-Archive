---
title: "samba can't access windows 7 from ubuntu"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by ypok on 2010-04-26
Hi, I installed samba (in Ubuntu 9.10) and I can access shared files in Ubuntu from Windows 7 but when I try to access W7 files from ubuntu: Places>Network, it prompts me Username, Domain, Password. I tried 
Username = W7 username
Domain=my workgroup (MSHOME)
Password=W7 login password

but it prompts me same thing again...checked some other related threads but couldn't get any luck. How do I solve this? 
Thanks in advance!
YPOK

---

### Post by garvinrick4 on 2010-04-26
This worked for me not to long ago.



gksudo gedit /etc/samba/smb.conf  
 

 

 Find this section in the file:  
 ####### Authentication #######  
 # “security = user” is always a good idea. This will require a Unix account  
 # in this server for every user accessing the server. See  
 # /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html 
 # in the samba-doc package for details. 
 #security = user  
 

 

 Uncomment the security line, and add another line to make it look like this:  
 security = user  
 username map = /etc/samba/smbusers  
 __________________

---

### Post by ypok on 2010-04-27
Thanks garvin..
Seems the problem is solved.. 
would appreciate if you could let me know what those two lines actually do!!

---

### Post by garvinrick4 on 2010-04-27
> **ypok said:**
> Thanks garvin..
Seems the problem is solved.. 
would appreciate if you could let me know what those two lines actually do!!


[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)

---

### Post by ypok on 2010-04-27
> **garvinrick4 said:**
> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)


Thanks :))

---

