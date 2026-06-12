---
title: "Cannot mount NAS since upgrade to 9.10 (mount error (11))"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by cptvitamin on 2010-01-01
I had four computers running 9.04 successfully mounting a Buffalo TeraServer NAS with the following fstab entry:

//192.168.1.2/share	/home/user/net-public	cifs	credentials=/home/user/.smbcred,noperm,nocase,user,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

I have upgraded two of them to 9.10 and neither can mount the NAS anymore. Anyone have any ideas?

When I try to mount the shares from the command line I get:

mount error(11): Resource temporarily unavailable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

