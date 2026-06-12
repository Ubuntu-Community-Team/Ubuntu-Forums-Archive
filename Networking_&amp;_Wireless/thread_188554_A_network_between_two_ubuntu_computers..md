---
title: "A network between two ubuntu computers."
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Jay_Dogg on 2006-06-04
I need help, my computer(breezy-->dapper) and my sisters' laptop(breezy-->dapper) are connected to internet through an adsl ethernet router. I was able to share files when we had windows, but now I can't share anything. I've had this problem since September and I've tried various howtos, but nothing has worked. So, I guess it's about time to ask help. My config files are messed up, is there a way to install clean files? :-k 

I just want to have a shared folder, which can be accessed and used to share files, music, etc... via both computers. Sending email to yourself, to get a file to the other computer, is quite boring. :)

---

### Post by alexpb on 2006-06-04
One way to do it is to use NFS. 
You will need to install the nfs-common package first and set up one of the machines as a server. 

After that you can do something like this on the other machine: 

mount -v -t nfs laptop:/shared /mnt/laptop

---

### Post by Jay_Dogg on 2006-06-04
[QUOTE=alexpb]One way to do it is to use NFS. 
You will need to install the nfs-common package first and set up one of the machines as a server. 

After that you can do something like this on the other machine: 

mount -v -t nfs laptop:/shared /mnt/laptop[/QUOTE]

How do I set up a server?

---

### Post by alexpb on 2006-06-04
Here is a how-to that might help you:

[https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo](https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo)

---

### Post by Jay_Dogg on 2006-06-04
I can't get it to work, thanks anyway.

---

