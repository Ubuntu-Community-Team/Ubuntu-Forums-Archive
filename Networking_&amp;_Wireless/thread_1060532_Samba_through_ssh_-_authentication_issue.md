---
title: "Samba through ssh - authentication issue"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by crokett on 2009-02-04
I have a need for Windows users to access a Samba share but I don't want to do it via straight Samba.  I want to tunnel through ssh. I have a working ssh session from XP to Ubuntu and can tunnel a remote desktop through it.  I can also tunnel the Samba share but when I enter the net use command in XP it fails on bad username or password.  The same username/password work when I don't tunnel through ssh.  I suspect it has something to do with the ssh encryption.  My question is what log to check to help figure it out?  syslog, auth and samba logs have bupkus.

---

### Post by dmizer on 2009-02-04
Tunneling SAMBA through SSH is no small feat. [http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php) (this linked howto has a link to a needed XP patch).

Edit:
It would probably be easier to configure full VPN access.

---

### Post by crokett on 2009-02-05
I got it.  I had to disable NetBios on the loopback adapter.

---

