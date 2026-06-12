---
title: "Single login/password for all samba shares?"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by yesint on 2010-02-22
Dear All,
My question is probably very common, but I didn't find an answer.
I have several computers, each with different user. Each user has a shared folder in samba. I want all users to access all these shares with a single login/password (not with the login/passw of each particular user).
How to achieve this?

---

### Post by johnson.d on 2010-02-24
In order to access the share you can create a common user name and password in samba using the following command:

```
$ smbpasswd -a <user-name>
```

Enter the password for the username

And in the configuration file /etc/samba/smb.conf you can add the following line to the relevant shares

```
valid users = <user-name>
```

Where user-name is the username created using smbpasswd command

Now all users can access the relevant shares using the same username and password. You can repeat this for the machines which have samba shares.

---

