---
title: "File server for both Mac and Windows"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by convan23 on 2009-02-23
How would I go about setting up a fileserver that is accessible for both Mac and Windows? 

Can samba do the trick? Maybe this is a stupid question, but can I run both Samba and AFP services at the same time?

---

### Post by ddnev45 on 2009-02-23
A friend of mine does it with an ftp server.

[http://ubuntuforums.org/showthread.php?t=218630&highlight=ftp+server]("http://ubuntuforums.org/showthread.php?t=218630&highlight=ftp+server")

There are probably some more ftp HowTo's in the Tutorials and Tips forum.

---

### Post by cariboo on 2009-02-23
You can use samba  to do what you need. Have a look at this [howto]("http://ubuntuforums.org/showthread.php?t=202605").

You can run as many servers as your hardware can handle. On my personal server I run a LAMP server, ftp server, mail server and streaming audio and video server, on a AMD64 1Ghz with 512Mb ram.

Jim

---

### Post by convan23 on 2009-02-24
Okay cool. Thanks then. Yeah I manage web servers and so I know I can have many processes running at once, but not knowing anything about how a LAN fileshare system works I wanted to make sure I wouldn't run into access restrictions by having two services synomously writing to the same data at the same time.

---

### Post by dmizer on 2009-02-24
I wouldn't suggest running smb and afp on the same directory. I've had NFS and samba running on the same directory without problems, but I was the only NFS user on the system so impact was low.

Mac can handle samba. But to get true cross-platform compatibility, I also endorse the ftp howto ddnev45 mentioned.

---

