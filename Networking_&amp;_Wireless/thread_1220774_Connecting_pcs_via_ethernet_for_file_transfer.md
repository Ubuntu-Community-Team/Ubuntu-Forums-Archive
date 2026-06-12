---
title: "Connecting pcs via ethernet for file transfer"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by ethan EARNSHAW on 2009-07-23
I want to transfer media files between machines both running on UBUNTU 9.04. I have connected the machines with an ethernet cable and know that I have to assign one as a host but do not know how to do this. 
Please advise with simple instructions, I an new to UBUNTU.
Thanks.

---

### Post by jamest09 on 2009-07-23
Connect them via a cross-over cable, give them both an IP address on the same subnet, then use sftp or similar to transfer the files.

---

### Post by Iowan on 2009-07-24
The "host" machine will need to be set up as server - either for FTP, SSH, or NFS. [Here]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html") is a help page for setting up **vsftpd**. 
[Here]("https://help.ubuntu.com/community/SSH") is some info in SSH.

FYI, [here]("http://ubuntuforums.org/showthread.php?t=1213999") is a thread discussing various FTP servers, and mentions SSH as alternative.

---

