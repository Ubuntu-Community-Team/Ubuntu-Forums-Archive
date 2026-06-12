---
title: "Auto conect to ftp site (Web Hosting) on boot up"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by Mobidoy on 2010-10-02
I am working on a website and instead of uploading/downloading my page every time I need to change something, I would like to auto connect to it and have it has a Folder in Places under Server.

If I open a file on the server thru Bluefish (ex: [ftp://elmarquis@74.121.222.56/index.php](ftp://elmarquis@74.121.222.56/index.php)) it will map the server in Places automaticaly but, when I reboot, it is gone so, If I only want to add images or documents in the folder of the site, I need to start Filezilla instead of simply drag&drop.

Thanx for any help :)

---

### Post by Mobidoy on 2010-10-05
Anybody can help me with this ?

---

### Post by joberly on 2010-10-05
Seems as though this will suit your needs. [http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)

Pretty easy syntax as shown on the webpage. You can make a script that runs your specific host and mount point run on startup.

---

### Post by Mobidoy on 2010-10-08
> **joberly said:**
> Seems as though this will suit your needs. [http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)

Pretty easy syntax as shown on the webpage. You can make a script that runs your specific host and mount point run on startup.

Thanx for the suggestion, it was working but could not make it work in fstab but, I have found out that when you try to add it in the Places menu, from the option at the bottom, you should not put [ftp://ftp.blabla.com](ftp://ftp.blabla.com) but only ftp.blabla.com on the server line :)

---

