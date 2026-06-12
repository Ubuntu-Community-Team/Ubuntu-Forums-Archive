---
title: "Simple SAMBA share - not working as it should"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by Sternfan on 2013-06-13
Hi all,
I am trying to set up a simple samba share that requires a username & password to open the share.

On the Ubuntu box I create a folder (in the home folder) - for example named "sharedocs."  I open nautilus, goto the share tab - share it as **sharedocs **and check the "allow others to create and delete files in this folder."  The server name is **testbox**.  The username that logged onto the ubuntu box and created the share is **tester**.

On the win7 box I go to \\testbox\sharedocs - it prompts for a logon - I put in testbox\tester and the password.  Nothing happens.  

If I go back to the ubuntu box and check the "guest access (for people without a user account)" - I can then browse to the share and it immediately opens fine (but no security -no asking for a password).  So the network is fine - just no password for the share.

Any idea on what I am doing wrong?

Thanks,
Rob

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by Sternfan on 2013-06-13
If I put in just TESTER it ends up thinking its a domain accound (the win7 box is on a domain) - I end up getting domainname\tester.

Rob

---

### Post by Sternfan on 2013-06-18
I am still having this problem.  Anybody have any idea what I am doing wrong?

Rob

---

### Post by clayb226 on 2013-06-18
What version of Ubuntu, what version of Samba? What is the out put of your testparm command? What is defined in your smb.conf file?

---

### Post by Morbius1 on 2013-06-19
> On the Ubuntu box I create a folder (in the home folder) - for example  named "sharedocs."  I open nautilus, goto the share tab - share it as **sharedocs **and check the "allow others to create and delete files in this folder."  The server name is **testbox**.  The username that logged onto the ubuntu box and created the share is **tester**.

On the win7 box I go to \\testbox\sharedocs - it prompts for a logon - I  put in testbox\tester and the password.  Nothing happens.  
Windows doesn't differentiate a local login user from a network user - there is simply the user. In Linux it's the opposite. You need to tell samba that the user: tester is also a samba user by using this command:
```
sudo smbpasswd -a tester
```
It will ask you for sudo's password and then it will ask you what password you want tester to use for samba. It can be the same as tester's local login password or not.

Just in case somthing is not configured right you might want to post the output of the following commands:

This will tell us the overall samba configuration on your box:
```
testparm -s
```
This one will show us how your share is configured since it won't be in smb.conf:
```
net usershare info --long
```

---

