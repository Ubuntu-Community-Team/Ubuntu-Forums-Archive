---
title: "Help - NFS, how click and open remote folder without using fstab?"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by vcrpcant on 2011-02-22
Hi,

I'd like to set a NFS share in ubuntu_box_1 so that a user on ubuntu_box_2 could click a desktop icon and automatically access the share.
They are all set up on lan static ip addresses.

However:
1 - I don't want that share to mount automatically using /etc/fstab, because I don't want users restarting the boxes every now and then to make it work.

2 - I also don't want to mount it using the terminal and sudo, because they don't know even the linux basics.

3 - I also don't want to install Samba, because fortunately there are no M$ machines in there.

Is there a way to do it?

---

### Post by An Sanct on 2011-02-22
Have you tried Places > Connect to Server ?

[A quick NFS guide]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

If you tick the "Add Bookmark", it should stay permanent

---

### Post by vcrpcant on 2011-02-22
> **An Sanct said:**
> Have you tried Places > Connect to Server ?

I'm on Ubuntu 10.04 and in Places > Connect to Server only shows:
SSH
Public FTP
FTP (with login)
Windows share
WebDave HTTP
Secure WebDave HTTP
Custom location

I have tried some of those, but no luck...

---

### Post by vcrpcant on 2011-02-22
It seems to be a bug, according to here:
[https://bugs.launchpad.net/nautilus/+bug/24430](https://bugs.launchpad.net/nautilus/+bug/24430)

---

### Post by dmizer on 2011-02-22
Perhaps something like this is what you need ...

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

