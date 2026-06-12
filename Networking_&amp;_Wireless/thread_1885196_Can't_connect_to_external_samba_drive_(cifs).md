---
title: "Can't connect to external samba drive (cifs)"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by Faoesch on 2011-11-22
Hi everyone :D

So I'm having this problem and I couldn't find anything in the internet. What I actually want to do is mounting a windows drive from my school.

I tried this in several ways
1. Adding an entry in the /etc/fstab which looks like this:
```
/fsemu18.edu.ds.fhnw.ch/e_18_data11$ /home/fabio/Documents/School/FHNW/Active_Directory cifs$
```
When I try to mount this with ```
sudo mount -a
``` I get the error message:
```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

2. mount it directly from the terminal:
```
sudo mount -t cifs smb://fsemu.edu.ds.fhnw.ch/data11$/ ~/Documents/School/FHNW/Active_Directory/
```
When I try to execute this command I get the errormessage:
```
Mounting cifs URL not implemented yet. Attempt to mount smb://fsemu.edu.ds.fhnw.ch/data11$/
```

3. via Dolphin:
The problem there is that I don't know what it means with:
name, server and folder

4. via Nautilus:
To be honest it works there. But because I'm using KDE I hate nautilus and only use it when I really really really really have to.

Thank you in advance for reading this and trying to help me :D

---

