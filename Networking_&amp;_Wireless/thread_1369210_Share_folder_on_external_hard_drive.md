---
title: "Share folder on external hard drive"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by motorcity909 on 2009-12-31
Is it possible to share (via Samba) a folder on an external hard drive?  

The ext HD will be permanantly plugged into my Ubuntu desktop and I want to be able to access the folder on our WinXP laptops.

I tried it earlier; added a folder on the ext HD to Samba, the XP machines could see the folder within My Network Places but told me I didn't have the authorisation to access the folder.  I also couldn't open that newly shared folder within Ubuntu Places>Network.

Do I have to restart Samba after adding a new share?  Is there a command for that?

Cheers
Dave

---

### Post by 1c3man on 2010-01-11
Hi Dave,
I am relatively new to the Ubuntu scene and had a similar type question.
I did find an answer to sharing folders though (sorry, can't find the post)
Like Windows workgroups sharing, a generic username is required with identical passwords.
What I have done is set up the XP desktops with the user Owner (because they are home machines) and gave them a simple easy password.
I then created the same account credentials within Ubuntu and from term ran the following commands.

iceman@BUILD:~$ sudo smbpasswd -a owner
[sudo] password for iceman: <admin password>
New SMB password: <share password>
Retype new SMB password: <share password>

Good luck and hope it helps,

Regards,
Iceman

---

