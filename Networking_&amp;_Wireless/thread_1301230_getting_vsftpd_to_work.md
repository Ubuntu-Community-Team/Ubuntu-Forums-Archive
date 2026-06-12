---
title: "getting vsftpd to work"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by JVo on 2009-10-25
Hi, I'm trying to use the "put" command to upload a document to my ubuntu server. Both computers are on the same wireless network. I installed "vsftpd" on my server. 
I edited the default vsftpd.conf file to set local_enable = YES and write_enable = YES. 
I did "sudo /etc/init.d/vsftpd restart".

From my other machine, I can do "ftp [serverIP]". When I try to do "put [local file] [dest. path]", I get the error "Entering Extended Passive Mode. Error 553: Could not create file".

I'm a newbie to ubuntu and to ftp, so I apologize if I'm making any stupid errors. :o)

I searched around a bit for this error - saw something about how a firewall can cause problems - but I never installed a firewall.

---

### Post by JVo on 2009-10-26
anyone have a clue?

---

