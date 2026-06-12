---
title: "User folder showing on Windows."
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by jayel49 on 2012-01-18
I've installed Samba on Ubuntu 11.10 and all my shared folders show on my Windows 7 PC.  However my Ubuntu User folder is also displayed on Windows even though I've never added it to the Samba configuration or added sharing details to the folder properties.

How can I prevent my User folder being networked.  The completed contents of the folder including hidden files are shown on Windows.

---

### Post by inobe on 2012-01-18
the proper way to setup samba with security.

[http://ubuntuforums.org/showthread.php?t=1896775](http://ubuntuforums.org/showthread.php?t=1896775)

note: pay mind to what's optional!

post#4 will be a complete way, skip steps you've already completed.

---

### Post by jayel49 on 2012-01-19
Thanks for the info.  I've edited smb.conf to indicate that my User folder should not be shared and that has done the trick

---

