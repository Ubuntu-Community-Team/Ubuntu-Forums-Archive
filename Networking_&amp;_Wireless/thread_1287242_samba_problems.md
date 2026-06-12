---
title: "samba problems"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by chris200x9 on 2009-10-09
I keep getting no such address when I input ```
sudo mount.cifs //192.168.1.103/home/chris200x9 ~/LinuxBox -o user=<user,password=<password> 
```

I'm following this guide [http://wiki.archlinux.org/index.php/Samba#Introduction](http://wiki.archlinux.org/index.php/Samba#Introduction)

I don't know why I keep getting this please help

note: I put it here as I'm on arch :P

---

### Post by swerdna on 2009-10-10
You cant have three terms in the server description (//192.168.1.103/home/chris200x9) After the IP you must put the network name of the share. e.g. see here: [http://opensuse.swerdna.org/susesambacifs.html](http://opensuse.swerdna.org/susesambacifs.html)

---

### Post by swerdna on 2009-10-10
PS You might also have to change ~/LinuxBox to contain the full path.

---

### Post by Iowan on 2009-10-10
Maybe you've seen [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To for mounting CIFS shares.

---

