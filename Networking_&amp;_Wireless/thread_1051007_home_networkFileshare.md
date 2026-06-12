---
title: "home network/Fileshare"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Bigneil on 2009-01-26
i have 2 laptops and a desktop pc. all are successfully connected to a wireless modem router.   

How would i go about sharing files between the 3 computers?

---

### Post by Bigneil on 2009-01-26
OH!  two are running Hardy and one has kubuntu 8.10.

---

### Post by BrandonBan6 on 2009-01-26
I like to use Samba. There are a ton of user docs around the web for configuation of it.

---

### Post by Bigneil on 2009-01-26
Ah! i did see a program called samba on the kubuntu.  do i need samba on all the computers?

---

### Post by BrandonBan6 on 2009-01-26
It needs to be installed on Linux computers, I think it is even included automatically with some distros. Anywho, yes, if it is installed you can right click a file and select sharing options. Or you can add an entry to the smb.conf file under the "Share Definations" section. (the smb.conf file is located in /etc/samba/ dir). Once you've established the share you should be able to browse to with any file browser using smb://[workstation/server name]/[share name]

---

### Post by Bigneil on 2009-01-26
Thankyou, i will have a noodle about and see how i get on. :)

---

### Post by BrandonBan6 on 2009-01-26
That's the best way to learn!!! :) ...........Let me know if you get snagged somewhere, I realize my instructions above were brief. There are a lot of great tutorials out there too.

---

### Post by Iowan on 2009-01-26
The native "sharing" file system for Unix (and Linux) is NFS.  Another option is SSHFS.  Hop over to [https://help.ubuntu.com]("https://help.ubuntu.com/") - search for Samba, NFS, and/or SSHFS to learn more.

---

