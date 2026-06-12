---
title: "How to change FTP service &quot;name&quot;?"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by ezamorad on 2009-06-29
Hi all!!! I'm new to Linux and Ubuntu Forums... and I have not so much experience in networking =S
 
I need help for some questions... please...
 
I have just installed the vsftpd FTP server on Ubuntu 9.04 and started de service (The easy part...) , but I need the service to respond to the name [ftp.2emes.com]("ftp://ftp.2emes.com")
 
I mean the service should respond to
ftp 192.168.x.x
And also to
ftp [ftp.2emes.com]("ftp://ftp.2emes.com")
 
What I should I do to configure this feature?

---

### Post by computer13137 on 2009-06-29
That's not a feature of the FTP server.  The FTP server should respond to any DNS entry or IP address that your machine has pointed to it.

The solution is to make a DNS record (or an "A" record) for "ftp.2emes.com" and point that to your server's external IP address.

If you need help doing this, I'd be glad to assist you further, and I'm subscribing to this thread in case you reply with another question.

-Kirk

---

### Post by ezamorad on 2009-06-29
Thank you for your response!!!
 
I found some information about the hint you give me, and what I should do is to edit the /etc/resolv.conf to add the line 
 
[ftp.2emes.com]("ftp://ftp.2emes.com")            A       192.168.196.3
 
(Corrections and observations are welcome)
 
I think it should work. By the moment I can't test it but as soon as I can I will do.

---

### Post by computer13137 on 2009-06-29
Your FTP server does seem to be responding.

-Kirk

---

### Post by Iowan on 2009-06-29
[edit] bad advice...

---

### Post by Iowan on 2009-06-29
[never mind...]
I was thinking of an entry in the /etc/hosts file which would look like ```
192.168.196.3  ftp.2emes.com 
``` and would work only for the client on which it was installed.
(Sounds like you found a better answer anyway...)

---

