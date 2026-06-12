---
title: "help i uninstalled the network manager"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by zinelabidine on 2013-05-18
hello, i uninstalled the network-manager to handel some script shell for wifi connexion, but after when i wont to reinstall it using the code source dowloaded from network-manager web site i have the following problem.



[B]Intltool is too old need intltool 0.40.0 or later 


how can i fix this problem, or is there an other way to reinstall it ?


thanks. [/B]

---

### Post by praseodym on 2013-05-18
The packages network-manager and network-manager-gnome are on CD in the folder ~/pool/main/n

---

### Post by zinelabidine on 2013-05-21
I downloaded an image.ISO from  UBUNTU website, but I didn't find the forder .../main/n  so I can't find the backage of network manager.

Have U any idea how to install it without internet PLZ?

---

### Post by praseodym on 2013-05-21
Double-click on the ISO and open it with the respective archive manager.

---

### Post by gordintoronto on 2013-05-21
It's always helpful to say what version of Ubuntu you are using. For example, ubuntu 12.04.2 32-bit and ubuntu 13.04 32-bit do not contain a folder called pool/main/n

---

### Post by steeldriver on 2013-05-21
If you have a wired ethernet connection, you may find it easier to temporarily bring up an interface from the command line or using /etc/network/interfaces (it's possible with wireless as well - but a bit more work). Then you can reinstall network-manager from your regular repository.

---

