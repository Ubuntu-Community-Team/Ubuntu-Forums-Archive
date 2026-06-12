---
title: "NFS trouble, permissions"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by IslayMist on 2009-01-23
Hi,

I tried to share /var/www ( maybe that is wrong ? ) to my laptop for easy access and development, but no matter what I do, I end up with just Read Only rights.

exports; /var/www     192.168.0.1/24(rw,no_root_squash,async)
(tried other rights too...)

client fstab; servername:/var/www     /home/username/webdev  nfs  rw,hard,intr 0 0

I guess I'm doing something wrong here, but where ?

---

### Post by Vesperatus on 2009-01-23
Poke in the dark here.

Does your user ( the linux one ) has Write access to /var/www ?

Go into the directory and try to edit a file.

---

### Post by IslayMist on 2009-01-23
Wow... hold on you got something there. I have the same user name on both the server and client, but they need to have the same User ID too, right ? I mean, in order to log in remote ? How do I check / adjust that ?

---

### Post by Cosimix on 2009-01-23
Please run from the nfs server:
[B]sudo ls -lh /var | grep www
sudo cat /etc/hosts.allow | grep -v "#"
sudo cat /etc/hosts.deny | grep -v "#"[/B]

...and from the nfs client the command **id**

If you have made any recent change to the /etc/exports you need to run **exportfs -a** on the server for the changes to take effect.

---

### Post by IslayMist on 2009-01-24
Yes ! Got it. Working perfectly, thank you so much, it's worth a lot to me and it will make my work so much easier.
The problem was the user rights for the folder :D

---

### Post by Vesperatus on 2009-01-24
> **IslayMist said:**
> Yes ! Got it. Working perfectly, thank you so much, it's worth a lot to me and it will make my work so much easier.
The problem was the user rights for the folder :D

Almost each time I have some issues, it's a user right issue or a firewall issue ;)

Glad it helped.

---

