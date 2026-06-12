---
title: "xfce share asks for password but wont allow access"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by geidorei on 2011-04-20
Hi - just setup an old PC with Xubuntu, all aok except for some networking issue.

Have setup using Samba a share on the documents folder. When I attempt to access it from another PC, when access is allowed to everyone, all works perfectly.

However, when I allow access just to a user, on attempting to access this folder, it asks for a password but on entering the correct password it does not allow access.

Any ideas? Soz fairly new to the wonderful world of Linux and still learning! lol

As a note: other PC that I am using is running Ubuntu 10.10

Thanks, Karl

---

### Post by Toz on 2011-04-20
You need to add the user account to the samba account database. Something like:

smbpasswd -a <userid>

Have a look at the "User Accounts" section of: 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)

---

### Post by Toz on 2011-04-20
Just realized the link was old (but still valid). Here is a newer link:

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

Reference is in the "File Sharing (Basics)" section.

---

### Post by geidorei on 2011-04-20
Sorted - thanks for replying so quickly!

Karl

---

