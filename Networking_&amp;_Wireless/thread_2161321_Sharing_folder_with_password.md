---
title: "Sharing folder with password"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by uzumakifahim on 2013-07-10
I want to share folder over a network, but I don't want that everyone can access the folder. So, I want to secure that folder with a password, so that only people who knows the passward can access the folder. Is that possible? HOW?

Thanks in advance.

---

### Post by newbie-user on 2013-07-11
So many options for this one. 

How about a password-protected web folder using apache?
[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

Or maybe a samba share?
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

What about authenticated FTP?
[https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html)

Give WebDAV a shot.
[http://ubuntuguide.org/wiki/WebDAV](http://ubuntuguide.org/wiki/WebDAV)

Basic SSH/SCP could work too.

---

### Post by uzumakifahim on 2013-07-12
Oh!!! Really thanks for this resourceful reply. This'll help me a lot.:)

---

