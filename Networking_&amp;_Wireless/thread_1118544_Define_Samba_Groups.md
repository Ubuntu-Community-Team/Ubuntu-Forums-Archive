---
title: "Define Samba Groups"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by markdavidoff on 2009-04-07
How do I define groups in my smb.conf file?

I know i need to use the "@" symbol, but then where do the usernames go?

I'm guessing it's defined under [Global] like this:

@groupName = user1, user2, etc?

But I'm not sure.

[https://help.ubuntu.com/8.10/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileprint-security.html)

Doesn't help apart from saying that you need to refer to your defined group by using the @(groupName) syntax

---

### Post by dmizer on 2009-04-07
This should help: [http://oreilly.com/catalog/samba/chapter/book/ch06_01.html](http://oreilly.com/catalog/samba/chapter/book/ch06_01.html)

Specifically:
> These users will need to be added to the group entry account in the system group file ( /etc/group or equivalent) to be recognized as part of the group.

In other words, you'll need to add the users to your samba server with the adduser command, create a group with the groupadd command, then include the samba users in the group with the usermod command.

Edit:
Here are some examples (new user is "markdavidoff", group is "shared") 

Add the user and give them samba privileges.
```
sudo useradd -s /bin/true markdavidoff
sudo smbpasswd -L -a markdavidoff
sudo smbpasswd -L -e markdavidoff
```

Create the "shared" group:
```
sudo groupadd -g 5000 shared
```
(note: check your /etc/group file to make sure the group number is unused.)

Add markdavidoff to the shared group:
```
sudo usermod -G -a shared markdavidoff
```

Then @shared will work in your /etc/smb.conf file.

---

### Post by markdavidoff on 2009-04-07
I assumed that you could define custom groups within the smb.conf file.
The server guide page I posted in the first post seemed to imply that the default groups are defined in /etc/group and additional groups could be defined in smb.conf

I was hoping this wasn't the case, as I was hoping to take my smb.conf file to my next system, with the groups defined inside that. Is there a way to define an external additional groups file?

If not, i will just go ahead and edit the /etc/group file.

---

### Post by dmizer on 2009-04-07
Do not manually edit the /etc/group file. It is a Linux system critical file. Use the groupadd command as I outlined above in my edit.

---

### Post by markdavidoff on 2009-04-07
Thanks for your awesome help

---

### Post by dmizer on 2009-04-07
> **markdavidoff said:**
> Thanks for your awesome help

No problem!

A few more things to note, when using the smbpasswd command, be sure to use the same username and password as the new user uses to login to their own machine. If they do not have a password, just hit <enter> when prompted for the password.

Also, some group names are reserved (eg: samba), make sure you use a unique group name and double check /etc/group to make sure it doesn't already exist.

---

### Post by markdavidoff on 2009-04-07
Cheers

---

