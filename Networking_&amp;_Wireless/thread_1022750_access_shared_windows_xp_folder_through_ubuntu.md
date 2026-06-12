---
title: "access shared windows xp folder through ubuntu"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by stmartin on 2008-12-27
Hello!

I got one question.

I can see successfully ubuntu shared folders from windows xp.

Now I want vice versa. Why I can't see other windows xp computers with my ubuntu machine? When I go in Network, it got WORKGROUP, and there is only my ubuntu PC. Please help!

Thanks in advance.

---

### Post by Iowan on 2008-12-27
Is WORKGROUP the name of the workgroup?  To what workgroup do the Windows machines belong? (The workgroup of the Ubuntu box should be settable in /etc/samba/smb.conf).

---

### Post by XPuntu on 2008-12-27
You might have to type your IP address in Nautilus to get there:

smb://192.168.1.etc

---

### Post by jesuspresley on 2008-12-27
> **stmartin said:**
> Why I can't see other windows xp computers with my ubuntu machine? When I go in Network, it got WORKGROUP, and there is only my ubuntu PC.

You can also edit the Samba settings by a graphical tool called system-config-samba. It makes the basic settings for SAMBA fairly easy to edit.

Iowan was right: Check if the name of the workgroup is the same in both computer settings. 

Also, check if any firewall on the Windows machine blocks the connection.

---

### Post by 2hot6ft2 on 2008-12-27
This might help.
HOWTO Ridiculously easy home file sharing with FTP and Zeroconf
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by stmartin on 2008-12-28
Thanks for the posts. 
smb://192.168.1.xxx helped.

I was wondering why there wasn't any computer in the network place.

---

