---
title: "Netork Shares and permissions"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by yogiman.uk on 2010-01-21
Hi

Can someone advise me on a network problem.

I share a folder from 1 ubuntu install and give permissions for guest to have read and write access.  When I browse to the network location I get 2 problems.

1. either I am refused access to the share. Even though the share is setup exactly the same as others on my system (except the share name of course).

2. If I can enter the share I am refused permission to write to the location.

I create the share by going to terminal and doing:-

gksudo nautilus and right clicking a folder then sharing and then ticking all 3 boxes.

I get a system message asking if I want to cascade the permission I say ok.

I get very random results.

Any advise welcome and thank you in advance.

Regards


Yogiman!

---

### Post by johnson.d on 2010-01-25
Please let me know the version of ubuntu you are using?

---

### Post by yogiman_uk on 2010-01-25
> **johnson.d said:**
> Please let me know the version of ubuntu you are using?

Hi I am using 9.10 (Karmic Koala)

Thanks for the reply.

Yogiman!

---

### Post by Puck7 on 2010-01-25
When you create the share, why are you using it with gksudo? Under Nautilus it's not letting you do it?

The sharing is created with samba, you need to setup a password and a username for the samba shares, which are required in order to access them. This can setup a password for your username by issuing this command in the Terminal:
```
smbpasswd
```

When  you create the shares make sure you use the permissions you wish, either grand write access to it or not.

---

### Post by Iowan on 2010-01-25
It's been awhile - so I can't say for sure...
You may need to set up the "guest" account in */etc/samba/smb.conf*.

---

### Post by Morbius1 on 2010-01-25
If you're allowing guest access you don't need to set up a samba password. 

Please post the output of the following commands:

Type **sudo net usershare info**
Type [B]testparm -s

[/B][COLOR=Blue]EDIT: also need to know the permissions on the folder you're sharing:[/COLOR][B]

ls -dl /path/to/shared/folder
[/B]

---

