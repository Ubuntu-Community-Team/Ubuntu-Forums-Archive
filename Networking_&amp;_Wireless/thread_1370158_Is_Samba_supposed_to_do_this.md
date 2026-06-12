---
title: "Is Samba supposed to do this?"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-01-01
True or False:

If you have a user on your Linux/Samba machine with a password, example:

User = Bob
Password = Password0

And Bob is on an XP computer, where his username is also Bob and his password is also Password0, is it normal for Bob to go to:

\\SambaServer, double click on Bob's share (valid users = Bob only) and Bob get RIGHT in without being prompted?

On my prior setup, the user HAD to log in. If they wanted auto login next time with their credentials, they had to check "remember password." But now it's as if Samba knows who they are. It's very strange.

What's the normal behavior? Must EVERYBODY authenticate with passwords, or if the Windows credentials are the same as Samba does it just somehow auto-detect it and allow them through?

---

### Post by Iowan on 2010-01-02
My experience has been: False.

Although my username and password are the same on my Samba server as on this (Ubuntu) client, I still need to provide username/password when I try to access my share.

---

### Post by LinuxRules1 on 2010-01-02
i have experienced that before. it's not samba it's windows. windows tries the username and password of the current user logged in and if it can't login it prompts you for the username and password(at least i think it works that way).

---

### Post by Roasted on 2010-01-03
Actually I think it may be 3rd party software on Windows that is contributing to this. It's set for "synchronize everything in my documents to samba share" and I have credentials put in so this program can auto log-in and auto-sync all of the data accordingly. I remember there being a feature "disconnect to server after operation completes". I think I may have checked it - but I'll have to double check. Almost certain that's what it is though...

---

