---
title: "sudo apt-get install --reinstall bcmwl-kernel-source"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by mbr78 on 2009-11-01
I'm trying to get my wireless adapter working on my HP Mini 110 in 9.10. Is there a way to issue this command "sudo apt-get install --reinstall bcmwl-kernel-source" while being offline? I only have internet access with a wireless connection (which is broke until I run this command) and it seems I need to be online for this command to work. I can get online in Windows to download files.

---

### Post by siglow on 2009-11-01
Im havign the same issue with netbook remix on the same model machine. i tried to download the bcmwl-kernal to a flash drive and then just install it that way (i need to install DKMS also), but im but im still having problems.

---

### Post by mbr78 on 2009-11-01
I got wireless working on HP Mini. I searched the USB stick I used to install 9.10 for "bcmwl-kernel-source". I then right clicked the package and reinstalled it. Then after a reboot my wireless worked.

---

### Post by COKEDUDE on 2010-06-26
[http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source](http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source)
It should be a debian package and all you need to do is double click it and then it will install.

---

