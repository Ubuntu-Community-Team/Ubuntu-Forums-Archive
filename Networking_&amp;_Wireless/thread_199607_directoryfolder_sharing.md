---
title: "directory/folder sharing"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by kinalas on 2006-06-19
1. how can i share a directory/folder on my pc
2. how can my ubuntu/kubuntu log-on to my windows 2003 domain

---

### Post by munckfish on 2006-06-19
Hi

Have a look at the Ubuntu server help docs here:

  [http://help.ubuntu.com/ubuntu/serverguide/C/index.html](http://help.ubuntu.com/ubuntu/serverguide/C/index.html)

For generic file sharing services check out the sections on FTP, NFS, and the HTTPD Apache Web Server under chapter 4. I would also recommend familiarizing yourself with Firewall setup which can also be found in the same section.

For integration with Windows and usage of Windows file shares check out chapter 5 which is all about a technology called Samba. Samba will let you connect to and setup Windows shares from Linux/Unix. The info in this chapter should get you setup for common usage scenarios. However, if you need a much more complex setup I recommend the very comprehensive 'By Example' guide on the Samba website: [http://us5.samba.org/samba/](http://us5.samba.org/samba/).

Best of luck. :)

---

