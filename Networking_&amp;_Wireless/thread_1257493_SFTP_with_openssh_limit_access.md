---
title: "SFTP with openssh? limit access"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2009-09-03
ok so i setup sftp on my ubuntu machine and when i connected i noticed that i had complete view of all files and directories on the entire filesystem. How do i limit acces to lets say just one directory

---

### Post by LightningCrash on 2009-09-03
use something like ProFTPD with TLS/SSL instead of SSH/SFTP.
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html)

---

### Post by ductiletoaster on 2009-09-03
honestly i would rather stick with openssh/sftp what advantages would proftpd have? does anyone know how to limit directory access in an openssh/ sftp setup

---

### Post by ductiletoaster on 2009-09-03
Ok so i think i need to clear some things up. This is what i want. i want to be able to have it setup so when ever someone SFTP's to my computer they only have access/view one folder.

Specifically a friend and i want to setup a sharing system. so we can send and recieve files from each other. It doesnt have to be SFTP though i assumed that would be the best protocol. We just need it to be secure. Limiting access is a huge thing for us both so thats a must

---

### Post by LightningCrash on 2009-09-08
Oops, looks like 4.9 adds a built-in for what you want

[http://www.minstrel.org.uk/papers/sftp/builtin/](http://www.minstrel.org.uk/papers/sftp/builtin/)

---

