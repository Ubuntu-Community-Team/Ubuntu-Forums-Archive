---
title: "Unbelievably slow samba"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by antieuclid on 2010-05-22
I'm trying to set up a fileserver on my 10.04 machine, and access the files from Windows 7 via wifi. I can see everything alright, but the transfer speed to Windows never gets higher than 70KBps. Both computers can access the web at 800+KBps. I've also checked with an OS X machine on the same network, which was also extremely slow, so I'm fairly sure that the problem is on the server's side.

---

### Post by shebaw on 2010-05-22
Have you tried tweaking the /etc/samba/smb.conf file? Type ```
sudo gedit /etc/samba/smb.conf
``` and then, uncomment(remove the #) from 
```
#SO_RCVBUF=8192 SO_SNDBUF=8192
#socket options = TCP_NODELAY
```
save it and close it.
And then type this on the terminal to restart samba
```
sudo service smbd restart
```

Hope this helps!

---

### Post by Nicezia on 2010-09-22
Well don't know if it worked for him, but it absolutely worked for me! Thanks!

---

