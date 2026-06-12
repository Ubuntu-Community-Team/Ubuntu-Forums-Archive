---
title: "ssh/sftp/ftp access to verbatim nas mount directory"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2011-01-27
[SIZE=2]Hi!
I unfortunately bought a 1 TB NAS drive from VERBATIM believing that it would support ssh. However, even the manufacturer now tells me that it only knows FTP.

Is there a way to mount FTP (not SFTP or SSH, which can be mounted with curlftps and sshfs, respectively)? As far as I could see, the (insecure) FTP is not supported by these applications. Is there any way to do so? Has anybody managed to modify the drive's software/firmware to become more user-friendly? I'd like to use it as a normal share, in particular over the internet (btw: I have port forwarded all relevant ports to mount it as share under Windows and this does not work either - only FTP)!
Thanks, D-E[/SIZE]

---

### Post by dieter-erich on 2011-03-08
solved!  Use:

°curlftpfs uid:pw@xxx.xxx.xxx.xxx /mount-point/"
unmount with:
"fusermount -u /mount-point"

---

