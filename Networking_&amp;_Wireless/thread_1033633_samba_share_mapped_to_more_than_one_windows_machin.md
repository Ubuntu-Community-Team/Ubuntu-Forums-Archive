---
title: "samba share mapped to more than one windows machine fails"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by xalaros on 2009-01-07
Ok, i am running Intrepid desktop edition with all latest updates.
I am using samba to share my multimedia over to my Vista machine and also
i am using a virtualbox 2.1 windows xp sp3 machine(on the intrepid installation).
When i access my network shares normally with \\server\share folder everything is ok(i tried with username/pass and with guest=yes).
My problem is when i map the network shares to drives on both my vista and xp machine they seem to lock up on one machine and the other can't use them.
so if i login to the xp machine first i can't use the mapped drives in vista and vise-versa. I am getting errors like incorrect password/username or too many connections to share.
Also when this happens i can't even login to the share using the \\server\share folder way.
Any way to fix the problem or is it something to do with windows locking the network access on the share point when it is mapped and i can't do much
about it??

---

### Post by dmizer on 2009-01-07
Sounds like you could have a couple of problems here.

First of all, please post your /etc/samba/smb.conf file. Also, it could cause problems if both your Vista and your XP computer are using the same login. If you want password protected shares, your Vista computer and XP computer should have separate login accounts on your Ubuntu computer.

---

### Post by xalaros on 2009-01-08
I can't seem to fix the problem  so i need your help
I have attached my smb.conf. Also i have made 2 samba users in order
to login to my shares from the xp and vista machine.
I have security = user in smb.conf but set guest = yes on my shares.
If i need to add security to my shares as well and turn off guest access can i make a share be accessed by 2 users at once???

---

