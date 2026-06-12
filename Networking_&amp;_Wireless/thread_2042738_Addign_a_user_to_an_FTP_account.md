---
title: "Addign a user to an FTP account"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by conradin on 2012-08-15
Hi all, 
I am using Lucid Lynx, and have an FTP server I just set up. Te server has 2 users. 1 user has read+write to a folder. I want to add a user with read-only permissions to the user1 shared folder.
How might I do that? 
I ave already made a limited User on the system "User2"

---

### Post by conradin on 2012-08-16
So I needed to get this done, heres what I did:

I added a user ```
$adduser user2
```
then changed their home directory to the shared ftp folder of the user1
```
$sudo usermod -d /src/ftp user2
```

in the vsftp config file Uncommented the line : chroot_local_user=YES


if there is a better way to get this done, perhaps some one will enlighten me.

---

