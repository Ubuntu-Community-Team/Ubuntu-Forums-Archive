---
title: "Strange issue when sharing via samba"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by lordofduct on 2008-12-15
Ok I have two PC's running Ubuntu 8.10

One of these machines has a very large storage drive on it hosting storage to my entire house. Stuff like movies, music, and some public storage for anyone that wants to use it (there's about 1.5 terrabytes of space just to freeload on).

I set a directory on this storage device... let's call it ~/share/ and in smb.conf I set some basic props to it to allow anyone access to it. I want to keep it just open so that way any one in the house doesn't need to do anything special to access it. They just jack into the wall and can watch movies I'm hosting in my bedroom.

```

[anyuser]
comment = public share
path = ~/share/
browseable = yes
public = yes
writable = yes

```

Now the issue:

ISSUE - everything shares fine, we can read and write to it and all the great stuff, but the problem is if I'm on another computer and I copy a folder that contains folders with in it over to this network share. It only copies what is directly in the folder over. Any recursive folder contents don't get copied.

What is happening?

---

### Post by Coreigh on 2008-12-15
Are the client computers all Windows? Is the computer you do the copy to a Windows computer? Is there a permissions inconsistency from the parent to the child folders that is causing them to be dropped? It is often best to have open shares in Samba get connected a generic or nobody account from all clients so that you can side step ownership and permissions problems.

Here is a sample share:
> 
[storage]
comment = Storage (public files)
writable = yes
path = /usr/files/storage
public = yes
only guest = yes
guest account = nobody
browsable = yes
You need the permissions to be wide open for this to work.
```
sudo chmod 777 /usr/files/storage
```


Do some googling for
> 
samba public share

---

