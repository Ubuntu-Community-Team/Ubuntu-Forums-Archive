---
title: "SSH or FTP"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by mikaelcrocker on 2011-11-09
g'day

So, I'm facing the conundrum of, would it be easier to use ssh than ftp if I want to access my files remotely.  It seems that I can create a simple RSA private and pub setup and transfer files using rsync; this seems like a way easier and less complicated route.

I don't know if anyone else has used this route, but any thoughts? I'm leaning toward the ssh route as it stands now.

---

### Post by jonobr on 2011-11-09
FTP is ok for quick file transfer between devices on a network where security is not an issue,

once you start to go beyond that you need to consider security.

FTP doesnt provide that.

Given what you want to do, avoid FTP and go to somthing like try Secure ftp (SFTP)or secure copy (scp) which can work with winscp on a windows box , you just need openssh on the server or come other secure method

---

### Post by matt_symes on 2011-11-09
Hi

Take a look at SFTP or SCP. They both use SSH.

FTP is insecure.

Kind regards

---

### Post by papibe on 2011-11-09
I highly recommend using sftp (included on the OpenSSH server package), instead of ftp. It works right out of the box, and it is much, much secure than ftp. Also, OpenSSH will give you both access to your file and remote login access.

In the client side you have lots of options:

Ubuntu/Linux:
[LIST]
[*]Command line tool sftp (similar to ftp).
[*]rsync over ssh (great I think).
[*]Filezilla.
[*]Nautilus itself (using the sftp:// style url).
[/LIST]
Windows:
[LIST]
[*]Filezilla.
[*]WinSCP.
[*]FireFTP addon for Firefox.
[/LIST]
I personally use rsync over ssh to access my home server, and transfers files to my brother (out of the country).

Hope that helps. Tell us if you need more help to set it up.
Regards.

---

