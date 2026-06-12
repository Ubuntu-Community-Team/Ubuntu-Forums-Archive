---
title: "SAMBA: 15357: tree connect failed: ERRDOS - ERRnomem (Insufficient server memory to p"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by cjtjamandra on 2009-11-19
Hi Iam suddenly getting this error when trying to mount a Win XP share to my ubuntu box.

```
15357: tree connect failed: ERRDOS - ERRnomem (Insufficient server memory to perform the requested function.)
SMB connection failed
```

---

### Post by cjtjamandra on 2009-11-23
Is it only me who has experienced this?

---

### Post by Crafty Spiker on 2010-04-18
I love it.  Two years later and it's still unresolved.  And people wonder why Linux hasn't taken over the world.:confused:

---

### Post by DataPath on 2010-05-28
This turns out to be a setting that is too low on the Windows system that you are trying to connnect to.  It *seems* to be a function of how full the disk that you're trying to mount is.

Nevertheless, use regedit to create, or if already present, change the IRPStackSize parameter. For windows XP default is 15(0xf), and range is 12-50(0xc-0x32).

> HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\lanmanserver\parameters\IRPStackSize
  DWORD
  0x11
To activate the change reboot, or give the following commands at a command prompt:

>   net stop browser
  net stop lanmanserver
  net start lanmanserver
  net start browser

Many users have observed this problem when connecting to affected shares from other Windows hosts as well, but it would seem that even in Vista and Windows 7, Microsoft has not addressed this issue.

I love it. Nine years later and Microsoft still hasn't resolved it. And people wonder why Microsoft hasn't taken over the world.

---

### Post by Baneblade on 2010-12-08
Thanks for that DataPath. Fixes my share browsing issues, but I have to keep starting and stopping the services to get keep share browsing working. 
Changing the IRPStacksize (even up to 50) doesn't seem to help?
Is there a more permanent fix for this that you know of?

---

