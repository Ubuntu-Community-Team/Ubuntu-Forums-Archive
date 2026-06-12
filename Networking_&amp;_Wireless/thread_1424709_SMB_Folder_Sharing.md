---
title: "SMB Folder Sharing"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by sagigreen on 2010-03-08
Hello, i am using Ubuntu 9 desktop, after installing and configuring SAMBA SERVER i get the following error while trying to share a folder:
 
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Wrong Password.
 
any ideas what am i doing wrong ?

---

### Post by Morbius1 on 2010-03-08
You could try a couple of things:

(1) Make sure samba is started:

Open **Terminal**
Type **sudo service samba restart**

(2) Make sure you are a member of the sambashare group:

System>Administration>Users and Groups > "Click to make changes" > Manage groups > sambashare > properties > Group Members

make sure your login id is a member of the group.

---

### Post by Robocoastie on 2010-03-12
I have the same error. Sharing worked for a day and then quit. Also can't connect to Windows network shares ('unable to retrieve share list from servers').

---

### Post by Aitaix on 2010-04-10
have the same problem...any ideas?

---

### Post by Ant01 on 2010-04-12
Sorry to butt in on this thread, but i'm having the same problem. I just loaded ubuntu 9.10 on new hard drive and previously samba was working fine on 9.04

I use my Ubuntu as a local network machine and connect vi LAN with windows machines

I followed the steps above but still get error message when I right click to share on the folder on external hard drive (NTSF) connected to my Ubuntu machine;

Failed to execute child process "testparm" (No such file or directory)
:confused:

Help will be appreciated.

Thanks

---

### Post by Morbius1 on 2010-04-12
Ant01, I think yours is a different problem. If I remember correctly there's something about a package named **samba-common-bin**.

Make sure it's installed - if it is - reinstall it then restart the samba service:

**sudo service samba restart**

---

### Post by Ant01 on 2010-04-13
> **Morbius1 said:**
> Ant01, I think yours is a different problem. If I remember correctly there's something about a package named **samba-common-bin**.

Make sure it's installed - if it is - reinstall it then restart the samba service:

**sudo service samba restart**

Thank you Morbius1 it worked. I upgraded the file **samba-common-bin** and also loaded **samba-common-bin4** and the problem is solved.

I appreciate the quick response we get from this forum. :)

---

### Post by Ant01 on 2010-04-13
:(oops I spoke to soon. When checking from the network on my Windows machine, it sees the shared access on the ubuntu machine, but when I type in my username and password it says it is incorrect. Not sure if I messed something up while fiddling around

---

