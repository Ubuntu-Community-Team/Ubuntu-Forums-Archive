---
title: "Can not mount password protected Windows shares"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by old_dos_guy on 2009-07-18
I just installed ubuntu 9.04 on an old Toshiba Satellite.  I have connected to my Windows network (using the built-in wireless via a Linksys router/access point).  I can see the shared folders that are not password protected, but I can not gain access to the ones that have a password.  I read that I needed to have the username/password on both systems, so I setup a user on the ubuntu system that was the same as username on the Windows system and set the password to the one set on the shared folder - but no change.  Ubuntu returns the error - Can not mount share.

Any ideas? (I figure I am doing something stupid.)

---

### Post by doas777 on 2009-07-18
on all my win terminals I specify ntlm v2 only for authentication, so I have to add 
```
client NTLMv2 auth = yes
``` to my smb.conf for each ubuntu client PC, and restart samba with ```
sudo /etc/init.d/samba restart
```.
I think vista specifies ntlmv2 by default. what OS is your client? also, are  both PCs in the same workgroup?

---

### Post by old_dos_guy on 2009-07-18
Duh, a little more info would be nice, I have three threads open and I guess I forgot to repeat some info.  I have three Windows systems on the same workgroup that I have connected the ubuntu system to - 1-XP Pro, 1-XP Home, and 1-Win98.  I can access shared folders on all three systems.  On the Win98 system I have a shared folder that is password protected - I can't mount it.  I have tried various username/password setups, but still get the failure to mount message from ubuntu.

---

