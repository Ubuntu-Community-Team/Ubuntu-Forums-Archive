---
title: "Intrpid Samba Shares"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by bobmendon on 2009-01-22
I have been struggling to determine why shares on my network don't work under Ubuntu 8.10 but they do work under Kubuntu 8.10. On the Ubuntu box, I can see the Microsoft computers but not the shares. I don't have a problem seeing shares on my Linux mail and web server. A closer look reveals that the Ubuntu Samba can't determine the permissions on the Microsoft shares. What I don't understand is why it works under Kubuntu and not Gnome based Ubuntu 8.10. I have had this problem with 32 bit and 64 bit Ubuntu.

Any ideas on how to fix this?

---

### Post by theozzlives on 2009-01-22
Have you set a SMB Password?
```
sudo smbpasswd -a username
```

---

### Post by Gramps on 2009-01-23
I've had that problem since 8.04 I think there has been a bug report issued, it's some kind of dns issue I think. I use the following work around...
With 8.10 still had the same problem. So I went Go/Location and in the address bar typed smb://192.168.0.x/ now I could see the directories and I just bookmarked it so I didn't have to type it each time. (replace the IP address above with the one for the machine you want to access.)

---

### Post by Iowan on 2009-01-23
As I understand it, it's a Gnome thing (gvfs?) - which is why it doesn't affect Kubuntu.

---

