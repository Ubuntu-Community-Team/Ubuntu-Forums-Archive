---
title: "how to make a secure share in samba"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by swerdna on 2009-07-10
Hi.

This basic Samba share on Ubuntu is accessible and writeable to me as a guest coming from another Linux machine:
> [testshare]
path = /home/john/testshare
read only = no
guest ok = yes
And when I take out the guest access, and make it like this:
> [testshare]
path = /home/john/testshare
read only = no
Then I can access the share by logging in, not as a guest.

If I log in as user john, I can write to the share from another Linux machine. but if I log in as a different user I can only read from the share, not write to it.

How do I alter the permissions on the shared directory and/or the definitions in the stanza for [testshare] in smb.conf so that the share is writeable for a user who logs into the share from a Linux machine on the LAN, using a name other than the owner of the shared directory (i.e. other than john)?

Thanks
Swerdna

---

### Post by superprash2003 on 2009-07-10
you would have to edit the folder's permissions.. since its john's home folder by default only john has write access to  it.. right click on the folder and click on properties and under permissions edit it

---

### Post by swerdna on 2009-07-10
> **superprash2003 said:**
> you would have to edit the folder's permissions.. since its john's home folder by default only john has write access to  it.. right click on the folder and click on properties and under permissions edit it

Thanks. I chmoded it to 777 drwxrwxrwx. I still can't write to it as a user different from john. I log in as someone else and can only read/copy, not create/write. What should I do now?

---

### Post by superprash2003 on 2009-07-10
right click on that folder and click on properties and go to Permissions.. what does it say now? could you post a screenshot of that window

---

### Post by swerdna on 2009-07-10
I was sure you were right about the permissions and consequently that 777 would give rw access, and I now have 777 so I looked for a problem different from permissions.

The problem was with my network browser on the other Linux distro: it was openSUSE 11.1 using KDE4.1.3. The Dolphin and Nautilus file managers both fail for browsing smb:/ to Ubuntu with the share described here. When I installed Nautilus in the openSUSE 11.1, it worked flawlessly.

So then I tried a vista network browser and that worked fine too. And then I tried an openSUSE 11.0 KDE browser and that worked fine too.

So, thanks for the help and it remains only for me to make a bug report to the openSUSE Bugzilla re their flawed KDE browsers in openSUSE 11.1.

For other readers who wish to create a secure read-write share in Ubuntu using classical sharing I recommend this one, which is easy to administer (because of the "force user" parameter) and allows only authenticated users.

```
[share_name]
path = /path_to/shared_directory
force user = username _of _owner_of_shared_directory
read only = no
```
and chmod shared_directory to 777

---

