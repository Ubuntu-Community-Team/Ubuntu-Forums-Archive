---
title: "Occasional FTP Server Setup"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by szim90 on 2009-11-29
Hello,

I occasionally need to move files around on my network. Since the system that runs Ubuntu is both connected to the home network via wireless, and directly connected to the internet via a broadband router, for security reasons I prefer to set up the receiving computer on the home network (usually my mac), as an ftp server, and simply connect from Ubuntu and transfer files over ftp (it's trivial to turn on and off the mac's built in ftp server, so I turn it on for the transfer, then stop it).

However, this can be problematic when I need to move files from Ubuntu to other systems that don't have built in ftp servers. I wanted to ask, is there an easy way to configure an ftp server in Ubuntu, such that it does not start on boot and can easily be turned on an off, so as not to cause a security risk (ideally with the same ease of controlling the mac's ftp server)?

I understand I could just install vsftpd and open and close the firewall on ports 20-21 as necessary, but I wanted to see if there was a more elegant solution.

Thanks for any help in this matter.

Regards,
szim90

---

### Post by Iowan on 2009-11-29
I could point you to a couple of FTP (or SSH) How-To's, but setting them up is not what you're after. Depending on your version, You'd probably want to disable a program startup in an RCx.d directory or disable a service (I haven't used Karmic, so dunno how this is done). Then, you could manually start/stop it via */etc/init.d* or via a **service** call.

---

### Post by szim90 on 2010-05-23
Thanks Iowan, this was what I was looking for.
Marking as solved.

---

