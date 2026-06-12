---
title: "Mounting SMB NAS drive"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Karakh on 2009-05-10
Pulling my hair out with this one. 

It used to work in Ubuntu 7.10, but after a complete format ad upgrade, it doesn't want to play.

The local ip for the share is 192.168.1.100, no username or pass needed.


I've tried:

```


sudo smbmount //192.168.1.100/main /home/kris/shared/ -o username=guest,password=

sudo mount -t cifs //192.168.1.100/main /home/kris/shared/ -o username=guest,password=

sudo mount -t smbfs //192.168.1.100 /home/kris/shared/

sudo mount.cifs //192.168.1.100/main /home/kris/shared/ -o username=guest,password=

```

And countless variations found in forums.


Almost every time I try, I'm met with the following error:

```

mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

No help found in manual :/

---

### Post by dmizer on 2009-05-11
Please see the second link in my sig :)

---

### Post by Karakh on 2009-05-11
Added nounix and it worked :)

Just out of curiosity, what does nounix do?

---

### Post by dmizer on 2009-05-11
The nounix option disables unix file extensions. This facilitates cross platform file sharing over samba.

---

