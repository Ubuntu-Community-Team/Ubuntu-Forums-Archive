---
title: "FTP server - vsftpd"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by Zenze on 2009-06-29
So I just set up a FTP server with vsftpd and for the most part everything is working ok. I forwarded the port on my router so it is accessible from the net, I disabled anonymous, and I set local_enable=YES so you have to have an account to access it. However, I still have a few concerns.

1: Is there a better way to access my files from anywhere on the net, such as apache, a vpn, or something else?
2: Is there a way to allow a user who logs in to only have access to their home directory as well as a separate ftp directory?
3: Is it secure? I read ftp sends the username+password in plain text so is there anything I should do to ensure security?

I read through the vsftpd.conf file and read a bunch of guides online but couldn't find much about this.

Thanks for the help.

---

### Post by Zenze on 2009-06-29
Actually, I guess the only thing that I am really worried about is the security aspect of it. I just don't want anyone to be able to do anything malicious to it. That goes for people who I give access to it and anyone out there who discovers it.

But maybe thats just me being paranoid, is this something I should even bother worrying about?

---

### Post by puppywhacker on 2009-06-29
SFTP is your friend (or SCP) it is based on SSH so it's on an encrypted link, it doesn't have the active/passive problems and it only uses one port.

go SSH :)

---

### Post by Zenze on 2009-06-29
> **puppywhacker said:**
> SFTP is your friend (or SCP) it is based on SSH so it's on an encrypted link, it doesn't have the active/passive problems and it only uses one port.

go SSH :)

Awesome! I'll go check that out right now. :)

---

### Post by Zenze on 2009-07-01
So I decided to use vsftpd and enable ssl encryption. However, when I enable the ssl I can't seem to connect to it :confused:.

I installed ftp-ssl and when I run:
```
ftp-ssl 127.0.0.1
```
I can login and everything works fine.

However, when I try it from another computer(outside of the lan) I can't connect to it. Because it worked fine locally it makes me think that it could be a port forwarding problem? Is is using a different port now that I have encryption?

---

### Post by puppywhacker on 2009-07-01
according to FTPS wikipedia you want to forward 990 for control and 989 for data.

I (and the rest of the world) still stick to the SFTP (over SSH) above the FTPS (over SSL) ... happy smiles anyway =)

---

