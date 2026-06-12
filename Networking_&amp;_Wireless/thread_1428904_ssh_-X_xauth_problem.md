---
title: "ssh -X xauth problem"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by evan54 on 2010-03-13
hi,

I'm relatively new to all this so this may be obvious but can't figure it out... :S

so when typing:

ssh -X user@server

I'm prompted for the password give it but it doesn't start the x-server. Instead I get this message:

-----------------------------------------------------------------------------------------------------------------------------
xauth:  error in locking authority file /afs/ir/users/path/.Xauthority
xauth:  error in locking authority file /afs/ir/users/path/.Xauthority
xauth:  error in locking authority file /afs/ir/users/path/.Xauthority
xauth:  error in locking authority file /afs/ir/users/path/.Xauthority

exec: 5: /usr/bin/X11/X: not found
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /afs/ir/users/path/.Xauthority
-----------------------------------------------------------------------------------------------------------------------------

any help would be appreciated.  I looked into the directory and the .Xauthority file doesn't exist ... :s

thanks,
eVan

---

### Post by dmizer on 2010-03-13
Well, what are you using for your SSH client? Are you by chance using putty with Windows?

Are you trying to connect from a remote location over the internet rather than on your local LAN?

Does it work if you use the -Y switch instead?
```
ssh -Y user@server
```

---

### Post by evan54 on 2010-03-13
no I am using gnome terminal on ubuntu 9.10... The weird thing is it was working fine yesterday and suddenly stopped no idea why or how... 

also I tried the -Y command and that also doesn't work...

and I think i'm trying to connect through LAN... not sure though... how do I check? Its basically a university campus so I think it's local..

any other suggestions?

---

### Post by evan54 on 2010-03-13
ok fixed the problem was not enough space on the server so it couldn't create the .Xauthority file. At least that's my theory :D

eVan

PS thanks to dude from ox

---

