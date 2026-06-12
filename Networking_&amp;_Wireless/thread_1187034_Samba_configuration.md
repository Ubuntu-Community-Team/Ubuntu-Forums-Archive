---
title: "Samba configuration ?"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by VeskoJl on 2009-06-14
Hi guys,

When i share a file via Nautilus, where this share is listed?
I couldn't find it in smb.conf . Using Jaunty

---

### Post by swerdna on 2009-06-14
> **VeskoJl said:**
> Hi guys,

When i share a file via Nautilus, where this share is listed?
I couldn't find it in smb.conf . Using Jaunty

Files shared using the Nautilus sharing facility are not the classical shares you are used to seeing as stanzas in smb.conf. They are "usershares" and their config files are in directory /var/lib/samba/usershares.

To read a bit of background for usershares see this article, even thought it's written for openSUSE, it's useful background for a first encounter with usershares:
[Practical Introduction to Linux Usershares]("http://www.swerdna.net.au/linhowtousershares.html")

---

### Post by VeskoJl on 2009-06-14
Thanks a lot. I was wondering why such duplication is necessary. Probably to avoid GUI "failure" when manually edit file?
Never mind . 

Thanks again.

---

