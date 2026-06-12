---
title: "Trying to mount a network drive, but it wont work..."
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by robin0dev on 2009-12-13
Hello @all

I've tried to mount my network hard disk several times. But there is always an error message.

So finally I did everytihng, like on the tutorial website of ubuntu: [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=https%3A%2F%2Fwiki.ubuntu.com%2FMountWindowsSharesPermanently") (with passwort protection) 

My fstab File:
//192.168.0.4/musik /media/NetStorage cifs username=robin,password=****** 0 0

But when I want to mount my network drive, there is always the following error message:
     
```
robin@Robin-DesktopPC:~$ sudo mount -a
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
robin@Robin-DesktopPC:~$
```

  I've now red that there might be a comptability issue with my smaba Server... could thta be (check: [http://www.linuxquestions.org/questions/…s-works-456897/]("http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=http%3A%2F%2Fwww.linuxquestions.org%2Fquestions%2Flinux-networking-3%2Fcifs-mount-error-5-inputoutput-error-but-smbfs-works-456897%2F")).

cheers
robin0dev

---

