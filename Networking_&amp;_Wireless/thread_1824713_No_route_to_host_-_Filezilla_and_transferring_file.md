---
title: "No route to host - Filezilla and transferring files generally"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2011-08-14
Hi all,

Desktop, laptop, both static IPs, can ping each other no issue. 10.04 LTS.

Am attempting to transfer files using Filezilla (which worked when I tried it about two years ago!) and the overall response is 'No route to host'. I have scoured the interwebs and have found no solution. Pretty sure I'm putting in the correct details.

All help appreciated as this one is an 'essential service' for me ... ;)

---

### Post by lmarmisa on 2011-08-14
Try to use Firefox as ftp client.

This is an example for a connection to a internal ftp server located at 192.168.1.100 with authentication:

[ftp://username@192.168.1.100](ftp://username@192.168.1.100)

---

### Post by lmarmisa on 2011-08-14
Other option is to use Nautilus as ftp client. Select Places -> Connect to Server -> FTP (with login) or Public FTP and so on.

Best regards,

Luis

---

### Post by Bucky Ball on 2011-08-14
> **lmarmisa said:**
> Other option is to use Nautilus as ftp client. Select Places -> Connect to Server -> FTP (with login) or Public FTP and so on.

Best regards,

Luis

Forgot to say, am using Xfce so that is not an option. Sorry. That is why I was trying with Filezilla. ;)

> **lmarmisa said:**
> Try to use Firefox as ftp client.

This is an example for a connection to a internal ftp server located at 192.168.1.100 with authentication:

[ftp://username@192.168.1.100]("ftp://username@192.168.1.100/")

That didn't work.

---

### Post by lmarmisa on 2011-08-14
What about gFTP?.

[http://gftp.org/screenshots.html](http://gftp.org/screenshots.html)

---

### Post by lmarmisa on 2011-08-14
> **Bucky Ball said:**
> 

That didn't work.

What was the exact URL you typed?. This method should work.

---

### Post by Bucky Ball on 2011-08-14
> **lmarmisa said:**
> What was the exact URL you typed?. This method should work.

I typed that adding the correct details and nothing.

---

### Post by lmarmisa on 2011-08-14
> **Bucky Ball said:**
> I typed that adding the correct details and nothing.

Hmmm. Try to access to a public ftp server, for example:

[ftp://mirror.eftel.com/ubuntu-dvd/](ftp://mirror.eftel.com/ubuntu-dvd/)

---

### Post by lmarmisa on 2011-08-14
The Xubuntu file browser Thunar seems to support ftp, at least in the 11.04 version.

Open Home and select Go -> Open location -> [ftp://yourlocation](ftp://yourlocation).

The most reliable method to test your ftp access is to use the command ftp:

```

ftp 192.168.1.100

```

In any case, if you are not able to solve your problem try to share your files using Samba.

Best regards,

Luis

---

### Post by Bucky Ball on 2011-08-14
> **lmarmisa said:**
> Hmmm. Try to access to a public ftp server, for example:

[ftp://mirror.eftel.com/ubuntu-dvd/](ftp://mirror.eftel.com/ubuntu-dvd/)

No problem accessing that incidentally ...

---

### Post by Bucky Ball on 2011-08-18
bump ...

---

