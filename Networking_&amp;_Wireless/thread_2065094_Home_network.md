---
title: "Home network"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by GeForce 9500GT on 2012-10-01
Hi everyone,
 
I have 2 desktop systems with Lubuntu and they are connected to a router. How can i connect to them?
 
See picture for setup.
 
I only want to make PC-1 visible for PC-2 and visa versa. Is there a way on how to do it? Maken them vidible and connect to eachother?
 
The laptop is connected to the router by wifi, the other 2 systems are conneted by wire. 
Many thanks!

---

### Post by nothingspecial on 2012-10-01
Install openssh-server on both pcs, then find out the ip address of each one.
```

ssh-keygen
ssh-copy-id user@other_computers_ipaddress
```


eg ssh-copy-id bob@192.168.0.3

then open the file browser and in the address bar at the top put
```

sftp://bob@192.168.0.3
```

change the user and ip for the correct one, then do the same on the other computer. You can add a bookmark in the file browser so that next time you just have to click the bookmark.

**Edit** - You may have to install the gvfs-backends package for this to work.

---

### Post by GeForce 9500GT on 2012-10-01
Thanks for your reply!
 
After reading your explenation i get the impression this has to be done in a webbrowser? But i want to see them in a filemanager as well. Is that possible too?

---

### Post by Lars Noodén on 2012-10-01
You could put the URI into the file manager (PCManFM in Lubuntu, Nautilus in Ubuntu), that was the suggestion above.  

sftp://bob@192.168.0.3/

Obviously, fill in the right user for your own account and the right IP addresses for your own  machines.

---

### Post by nothingspecial on 2012-10-01
> **GeForce 9500GT said:**
> Thanks for your reply!
 
After reading your explenation i get the impression this has to be done in a webbrowser? But i want to see them in a filemanager as well. Is that possible too?

No you do it in the filebrowser

[ATTACH]224912[/ATTACH]

---

### Post by GeForce 9500GT on 2012-10-01
> **nothingspecial said:**
> No you do it in the filebrowser
 
Okay, I'll check it this evening!

---

### Post by GeForce 9500GT on 2012-10-07
Is it possible to make a connection to my other Lubuntu system with a FTP tool like Filezilla?

---

### Post by Lars Noodén on 2012-10-07
> **GeForce 9500GT said:**
> Is it possible to make a connection to my other Lubuntu system with a FTP tool like Filezilla?

Yes, Filezilla supports SFTP.  

One way is to use quick connect, entering port 22 for the connection.  It will then choose SFTP for you.

Another way is File->Site Manager->New Site->Protocol: SFTP

---

### Post by GeForce 9500GT on 2012-10-07
> **Lars Noodén said:**
> Yes, Filezilla supports SFTP.  

One way is to use quick connect, entering port 22 for the connection.  It will then choose SFTP for you.

Another way is File->Site Manager->New Site->Protocol: SFTP

Thanks for yopur reply. It there some sort of wiki available on how to do this?

---

### Post by Lars Noodén on 2012-10-07
> **GeForce 9500GT said:**
> Thanks for yopur reply. It there some sort of wiki available on how to do this?

You can get a more verbose description here:
[http://www.upenn.edu/computing/help/doc/ftp/filezillasftp.html](http://www.upenn.edu/computing/help/doc/ftp/filezillasftp.html)

But it is as I mentioned for FileZilla, File->Site Manager->New Site->Protocol: SFTP

To connect with Nautilus or Dolphin, just press ctrl-L

---

