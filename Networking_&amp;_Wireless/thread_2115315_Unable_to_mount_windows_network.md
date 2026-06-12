---
title: "Unable to mount windows network"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by kvel23 on 2013-02-12
I have installed ubuntu linux inside Windows.

When i logged into linux os i am unable to access files of windows.When i try to open Windows network from Network list, i am getting error message as  "Unable to mount location Failed to retrieve share list from server".  

Can someone please help me how to access windows file from linux.

---

### Post by alexii on 2013-02-12
Assuming the network between the two systems is okay, try this is a terminal:

```
nautilus smb://<windows-ip-here>/<share-name-here> 
```

e.g.,

```
nautilus smb://192.168.1.100/My\ Documents
```

If it works, bookmark it.

---

### Post by magicalworld on 2013-02-16
Hi,
I was getting error "‘Failed to Retrieve Share List from Server’ while connecting to my NAS drive and windows shared drive.

I tried tweak to the smb.conf file as mentioned in below link and it worked immediately for me on Linux Mint.

[http://www.liberiangeek.net/2012/03/how-to-fix-failed-to-retrieve-share-list-from-server-in-ubuntu-12-04-11-10-when-file-sharing-with-windows/](http://www.liberiangeek.net/2012/03/how-to-fix-failed-to-retrieve-share-list-from-server-in-ubuntu-12-04-11-10-when-file-sharing-with-windows/)

Cheers!

---

