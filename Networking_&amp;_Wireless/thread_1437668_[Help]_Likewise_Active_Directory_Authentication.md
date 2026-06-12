---
title: "[Help] Likewise Active Directory Authentication"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by nqsonk9 on 2010-03-24
Hi guys,

I'm really new to the whole Unix-Windows integration thing so I will storm this thread with newbie question :D

Using **Likewise-open** to join my Ubuntu 8.04/9.10 to Active Directory 2008, everything works well including log on locally, ssh, changing password with domain users.

Now I want to apply GPO on them:
- A random example: Running a logon script
- Grant a domain user Administrator privilege of the Ubuntu machine.

I suppose we can by some way add the domain user to the sudoers group of the Linux machine but not yet know HOW. (lead to **lwidentity**)

Any idea is welcome to discuss :)
Thanks, everyone.

---

### Post by Bufke on 2010-03-26
For admin access
edit /etc/sudoers
Add something like this, in my case I wanted only people in the UnixAdmins group to have sudo access, then I can choose who has sudo access in AD.
%ADMIN\\UnixAdmins      ALL = (ALL) ALL

Not sure about running random login scripts, maybe have all users run some login script that runs a script in a share drive that you could change.  Not the most elegant solution.

---

