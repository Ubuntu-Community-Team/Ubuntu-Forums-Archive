---
title: "Sharing files and folder with windows"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by dE_logics on 2009-04-19
I've shared certain files and folders in windows having IP 192.168.1.2 and DNS server as 192.168.1.1.

The other computer [ubuntu] had IP 192.168.1.1 and DNS server 192.168.1.2.

This technique works with windows, but with ubuntu in the places>network or places>network>windows network nothing is seen.

Samba came preinstalled with ubuntu (I can see it in the package manager).

What more do I have to do?

I just need to transfer data.

---

### Post by inobe on 2009-04-19
this is how it's done, enjoy

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)


start with "Sharing folders via the Shared Folders application" in the link, steps "1 to 11".

then if you want to have secure login scroll down to "Accessing shared folders via Windows" and follow steps "1 to 6", this section requires about one minute in terminal.

---

### Post by me.translucent on 2009-04-19
it seems your ubuntu system is the client and the windows system is the server so . to acess shared files in the ubuntu u need to install smbfs.and you can use smbclient from the terminal or Places->Connect to server for a graphocal user interface .

---

### Post by dE_logics on 2009-04-19
To add more miseries I dot not have the shared folder service installed.

Yet samba is installed.

---

### Post by inobe on 2009-04-19
> **dE_logics said:**
> To add more miseries I dot not have the shared folder service installed.


```
shares-admin
```

what happens when you run that

---

### Post by Iowan on 2009-04-19
> **dE_logics said:**
> Yet samba is installed. It might be worth pointing out that the default installation installs the Samba "client" - so you *should* be able to use Ubuntu to access Windows shares on other machines.  To share FROM Ubuntu requires installing Samba-server.
Of course, all this requires a working network...

---

