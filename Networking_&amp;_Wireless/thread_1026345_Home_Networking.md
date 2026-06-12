---
title: "Home Networking"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by blake100 on 2008-12-31
I am having problems trying to network my Windows XP Computer to my Ubuntu Computer.  The Ubuntu can see the XP and can share files but when I try to see the Ubuntu from the XP it asks for a password.  I try my Windows and Ubuntu password (The same) but it will not let me into the Ubuntu Computer.
Has anyone and bright ideas that might help.

---

### Post by Iowan on 2008-12-31
Have you installed Samba server (Ubuntu comes with client already installed)? Have you created a Samba user (using **smbpasswd**)? The user must already be a(n) Ubuntu user.

---

### Post by AlanR8 on 2008-12-31
Hi there and I hope you've enjoyed your (insert words of your choice) break! Have to be PC these days.

I have Kubuntu machines and XP machines on my home network and they all play together nicely. It wasn't always the case when I started with Linux but each new iteration of Kubuntu has made things easier.

I always install the following on a fresh install:

> sudo apt-get install samba smbfs system-config-samba smb4k winbind kdenetwork-filesharing

If you're running 8.1 then system-config-samba provides a nice little GUI to arrange your file shares, permissions, samba users and passwords etc and also your workgroup name. Sweet.

Let us know how you get on....

---

