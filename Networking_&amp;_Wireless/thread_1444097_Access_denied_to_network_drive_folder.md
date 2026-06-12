---
title: "Access denied to network drive folder"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by kelphis on 2010-03-31
I have a network drive setup on windows to a samba share that is on ubuntu 9.1.  The folder im connecting to has a couple symbolic links setup and all of them give me an Access denied error when I try to open them.  I have dont everything I can think off including chowning all the folders to the user that Im logged in as and doing chmod 777 on all folders and files.  I have tried deleting the link and recreating it and nothing works.  This was working fine a few days ago and now it doesn't.

any ideas?

---

### Post by kelphis on 2010-03-31
GAHH!!!  never mind. 
I thought that I figured it out.  It still doesn't work.

---

### Post by capscrew on 2010-03-31
> **kelphis said:**
> I have a network drive setup on windows to a samba share that is on ubuntu 9.1.  The folder im connecting to has a couple symbolic links setup and all of them give me an Access denied error when I try to open them.  I have dont everything I can think off including chowning all the folders to the user that Im logged in as and doing chmod 777 on all folders and files.  I have tried deleting the link and recreating it and nothing works.  This was working fine a few days ago and now it doesn't.

any ideas?

This appears to be a symbolic links problem.  See [**_[COLOR="Blue"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1440993")for details.

---

