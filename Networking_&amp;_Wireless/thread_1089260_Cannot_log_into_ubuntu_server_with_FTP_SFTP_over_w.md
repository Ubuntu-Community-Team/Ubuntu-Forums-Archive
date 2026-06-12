---
title: "Cannot log into ubuntu server with FTP SFTP over wireless connection"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by majickal on 2009-03-06
Hi All,

I have a bit of a strange problem. I cannot log into ubuntu (FTP or SCFTP (using winSCP)) server over a wireless connection. However, i can log in using ssh command line.

I do not have this problem when connected via Ethernet cable...strange??

BTW way this is a local development server on my home network, i do not have this problem connecting to my server on the net.

Any help would be greatly appreciated.

Regards

---

### Post by majickal on 2009-03-09
well i finally figured this out. I had to setup a ssh tunnel whilst sftp'ing. not sure why but it works.

---

