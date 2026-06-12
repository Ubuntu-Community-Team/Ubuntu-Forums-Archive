---
title: "Personal File Sharing mystery - 10.04"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Gordonbp531 on 2010-07-22
If I do System-Preferences-Personal File Sharing it tells me that I can't
enable sharing over the network because "the required packages are not
installed on your system".
It doesn't tell me **WHAT** packages I need to install!!!!!!
Can anyone enlighten me?

---

### Post by Morbius1 on 2010-07-22
> It doesn't tell me **WHAT** packages I need to install!!!!!!
Can anyone enlighten me?     [B]apache2.2.bin
libapache2-mod-dnssd
[/B] 
Just so you know, Personal File Sharing is not Samba or NFS.

It's a minimal file server using apache and it broadcasts it's share  using avahi ( or bonjour on windows ). It will only allow you to share one folder:
/home/your_user_name/Shared

---

