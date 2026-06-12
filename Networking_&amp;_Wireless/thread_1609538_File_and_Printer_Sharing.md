---
title: "File and Printer Sharing"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by JoshDN on 2010-10-30
Hi All,

Does anyone know where to find good documentation on setting up file a printer sharing on Ubuntu 10.04. I'm using the desktop version, not server. I'm new to networking so something that covers all the basics would be great.

Thanks everyone!

---

### Post by SteveDee on 2010-10-30
> **JoshDN said:**
> Hi All,

Does anyone know where to find good documentation on setting up file a printer sharing on Ubuntu 10.04. I'm using the desktop version, not server. I'm new to networking so something that covers all the basics would be great.

Thanks everyone!

[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by JoshDN on 2010-10-30
Just started reading the info here. This is excellent information!

Thanks for the help! I'll report the results.

---

### Post by JoshDN on 2010-10-31
Well, the documentation above didn't quite work. I'm not sure if it was my operator error or the info is outdated. I was able to get everything working using the Samba Server Configuration Tool. It was in the Ubuntu software center and made things real simple. So right now I can share files and printers on all the computers on the network.

I am having trouble with permission settings for my windows 7 computers. I used the following command in a terminal to set the permissions for the shared directory.
```
chmod 777 /shared directory
```After this the windows computers have read/write permissions for this directory only. If i create another directory inside this shared directory i also need to set the permissions for this folder as well. Is there a way to set permissions for the shared directory and all subdirectories with one command?

---

### Post by SteveDee on 2010-10-31
I thought this was controlled by the #===Share Definitions=== section in /etc/samba/smb.conf {but I have not tried this}

Also checkout the samba conf manual, from a terminal:-
```

man smb.conf

```


Edit: I had another look at this: [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)

.... and I think you may need to set:-
```

# Directory creation mask ...
directory mask = 0777

```

---

### Post by luvshines on 2010-10-31
> **JoshDN said:**
> 
I am having trouble with permission settings for my windows 7 computers. I used the following command in a terminal to set the permissions for the shared directory.
```
chmod 777 /shared directory
```After this the windows computers have read/write permissions for this directory only. If i create another directory inside this shared directory i also need to set the permissions for this folder as well. Is there a way to set permissions for the shared directory and all subdirectories with one command?

Are you trying to modify permissions for shares that exist on Windows 7 and are being accessed from Ubuntu machine ?

---

