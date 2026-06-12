---
title: "Cannot connect from Windows"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by jfl on 2006-06-29
Once again I am tapping the vast resources of this great community.

Problem:
I have an Ubuntu box on a W2000 workgroup;
installed Samba, configured smb ...
the Ubuntu box is accessing the W2000 network with no problem
but if I try to access the Ubuntu machine from any of the Windows machines, I get a dialog box asking for username and password.
I tried everything name/pwd I could think of.  ](*,) 
I created a Windows user with the same username and password than my Ubuntu login. Still does not accept. 
In the "Computers near me" I see the Ubuntu machine; in the comment column it shows *"moique server(Samba,Ubuntu)".*

I have the windows machines setup to log me in directly (no pwd) if that makes a difference.
HEEEEELLLLP 

TIA

---

### Post by x64Jimbo on 2006-06-29
There's a FAQ/How-To on this topic:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by Footer on 2006-06-29
It sounds like the only step you are missing is:

[INDENT]```
sudo smbpasswd -L -a your_username
```[/INDENT]

on the Ubuntu box.

This is also mentioned in the FAQ/How-To link above.

Good luck!

:)

---

