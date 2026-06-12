---
title: "SWAT doesnt start properly"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by capo1949 on 2009-07-16
Hi

When browsing to [http://localhost:901](http://localhost:901) the following are missing from the page :- globals,shares, printers,wizard  so it looks like I am not in root.

However I enable a root account using command sudo passwd root.
graham@graham-desktop:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
graham@graham-desktop:~$ 

So when I call the local host I am ask user name and password, which is accepted, and i dont get the full swat functions

So as not to forget the password requested I used the same one as used to log onto the system on boot up. I thought maybe  this is causing a conflict of some sort so I used another one. Now when the system ask for authentication before opening the local host page it will not accept my new password, only the one I login with. it keeps failing and alarming 
A user name and password are being requested by [http://localhost:901](http://localhost:901). The site says: "SWAT"
I am using the user name 'graham' and tried 'graham-desktop' and even 'graham@graham-desktop'
any help would be appreciated
Graham

---

### Post by capo1949 on 2009-07-17
Hi

I solved this problem. I realized that the username entered is not loginusername but root.
So entered username 'root' and then passward gernerated and all is well
DUH
graham

---

