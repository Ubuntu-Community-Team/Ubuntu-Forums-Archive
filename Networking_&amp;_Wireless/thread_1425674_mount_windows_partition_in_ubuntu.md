---
title: "mount windows partition in ubuntu"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by makak06 on 2010-03-09
Hey all,

Sorry for my english because i'm french

I have few questions about /etc/fstab
i would like to mount files who is in another PC so i did : (in fstab)
192.168.1.21:/mnt/md1/cedre /home/serveur/cedre nfs auto 0 0

And it's works, but when i create a folder, the permission are 755 and i wish 777 and i don't know what to do...

If i use cifs or smbfs and use umask=000 it's doesn't work...

Thanks for your help.

---

### Post by koszta on 2010-03-09
if I understand well what are you trying to do then try this
sudo chmod 777 -R FOLDER_FROM_WHICH_YOU_WANT_777_RIGHTS 

general point: you dont really use 777 much, not safe - try using 755 for the files you run and 644 for folders. 
general point2: One of the key principles of ubuntu is accessibility - so try it here :
[http://forum.ubuntu-fr.org/]("http://forum.ubuntu-fr.org/")

---

