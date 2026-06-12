---
title: "Samba - Password protect only one share"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by nloding on 2009-11-03
Right now I have Samba running on a box and it's set for "share" permissions -- so no one has to enter a username and password.  We are sharing out four individual folders.

What we have now been approached with is password protecting only one of those shares.  The end result being that when a user browses to \\samba\share1, there's no username/password prompt; but if they browse to \\samba\share2, it prompts for a username and password.

I have no idea if this is even possible.  I've done some searching and can only find guides to setting up a username/password combo for ALL shares, not just one folder.

Is this possible?  If so, how?

---

### Post by nloding on 2009-11-04
Giving this a quick bump -- another day of searching and I haven't found anything.  I'm assuming this means it's not supported but I'm not giving up hope!

---

### Post by mpokrywka on 2009-11-04
I have something like this configured on my Debian Lenny system:
snipped from smb.conf:
```

security = share
[homes]
read only = no
valid users = %S
[shared]
path = /home/shared
guest ok = yes
writable = yes
guest only = yes

```

//my_server/shared is passwordless rw share
Each user has password-protected share.
Requires creating unix user (with home directory) and setting its password using **sudo smbpasswd -a username**
In my case, share name is equal to user name (i.e //my_server/joe ) and password-protected share has only one user.
You can try to fiddle with "guest ok = no" and "valid users = space separated list of user names" as share parameters, maybe this will work...

---

### Post by softclean on 2010-01-29
There's only one thing that I needed to change in order to work:

```
security = share
```

must be

```
security = user
```

Also, don't skip the step of using smbpasswd to create a password for your username, it's important.

---

