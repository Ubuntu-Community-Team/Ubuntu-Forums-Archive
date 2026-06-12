---
title: "Networking broken with 10.04"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by ledat on 2010-05-14
Hello all, brand new user here.  I apologize in advance for not knowing enough to even do basic things to help myself.

I installed Ubuntu on one of my machines a few days ago.  It was an oldish CD containing 9.10.  Eveything was puppies and rainbows.  However, today I updated that machine to 10.04, and it no longer sees my network.  Specifically, Windows doesn't see shares on it, and it doesn't see shares on Windows.  Further, when trying to make a share (or rather update the one I had previously) I get the following:

> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

I suppose this is a samba problem.  Steps I have taken to try to fix this:
> sudo /etc/init.d/samba start
This results in command not found.  I do have an /etc/samba with config files and what not in it though.

> sudo apt-get install samba
This results in samba is already the newest version.

> sudo apt-get install smbfs
Again, this is already the newest version.

And, being that I have no real idea what I'm doing, this is where my Googeling skills fail me.  I want to reiterate, though, that before I updated today, networking was fine in both directions, i.e. from windows to ubuntu and from ubuntu to windows.  How can I get networking to work again?  Thanks in advance.

---

### Post by pytheas22 on 2010-05-14
Did you try:
```

sudo /etc/init.d/smbd start
```

---

### Post by ledat on 2010-05-14
Thanks a lot, that worked perfectly.  Everything is once again puppies and rainbows.  With that resolved, I can now try to learn what I'm doing.  Thanks again!

---

