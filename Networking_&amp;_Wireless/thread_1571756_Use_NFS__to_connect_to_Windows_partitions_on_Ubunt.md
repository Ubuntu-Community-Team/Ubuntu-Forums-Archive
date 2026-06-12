---
title: "Use NFS  to connect to Windows partitions on Ubuntu server from Ubuntu client?"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by dblaisde on 2010-09-10
I'm running Lucid on a laptop client and a desktop server. The server has windows partitions that I'd like to connect to from the client using nfs over a wireless link on my home network. Is this possible? (I'm currently using samba but find it slow and stalls shutdowns on the client.)

I've successfully connected to ubuntu partitions on the server via nfs, but most of the data is on the windows partitions, and must remain there.

---

### Post by dmizer on 2010-09-10
> **dblaisde said:**
> Is this possible?

No. NFS needs Linux file permissions. You will need to use either samba, or convert the drive to ext3.

---

### Post by xllxjustinxllx on 2010-09-10
Have you tried installing an FTP client on your server?

I'm not sure this would work but install ftp on your server, mount the windows drive on your server and then on the laptop click places menu, connect to server, and then depending on how you set it up click public ftp or ftp with login. It should give you a list of directories.

I am in a similar situation and i just use sftp to connect to my server and retrieve files.

---

### Post by dblaisde on 2010-09-11
thanks all. Not the news I wanted to hear, but so what. PS: I need more than FTP access but thanks for the idea.

---

### Post by dmizer on 2010-09-11
> **dblaisde said:**
> thanks all. Not the news I wanted to hear, but so what. PS: I need more than FTP access but thanks for the idea.

What do you need to do that FTP will not allow? Perhaps we can help with a suitable alternative.

---

