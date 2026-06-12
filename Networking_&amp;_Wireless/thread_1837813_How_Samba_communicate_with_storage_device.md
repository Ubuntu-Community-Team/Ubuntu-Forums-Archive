---
title: "How Samba communicate with storage device"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by sliter on 2011-09-02
Hi, everyone.

I am now working for a project that relates to improve the performance of the Samba. And I found it is difficult to find any documents that describe the high level design of a Samba server or how the server communicate with the storage device. So does anyone has a related doc? Thanks in advance:guitar:

---

### Post by lmarmisa on 2011-09-02
> **sliter said:**
> Hi, everyone.

I am now working for a project that relates to improve the performance of the Samba. And I found it is difficult to find any documents that describe the high level design of a Samba server or how the server communicate with the storage device. So does anyone has a related doc? Thanks in advance:guitar:

[Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") is a implementation of the [SMB/CIFS networking protocol]("http://en.wikipedia.org/wiki/Server_Message_Block"). Samba allows file and print sharing among computers.

[Samba]("http://www.samba.org/") does not define the internal method used on the server for accessing to the storage devices (SATA, IDE, SCSI, RAID, etc). This is out of the scope of Samba. Anyway the server uses the operating system (normally UNIX/Linux) capabilities for accessing to the stored files. But this is not a part of the Samba protocol.

These links explain the SMB/CIFS protocol:

[http://www.samba.org/cifs/docs/what-is-smb.html](http://www.samba.org/cifs/docs/what-is-smb.html)

[http://ubiqx.org/cifs/index.html#Contents](http://ubiqx.org/cifs/index.html#Contents)

[http://www.codefx.com/CIFS_Explained.htm](http://www.codefx.com/CIFS_Explained.htm)

---

### Post by sliter on 2011-09-05
Thanks lmarmisa.
Sorry for the late reply.
I've already looked through all the links and well understood how the protocol CIFS functions. But the problem for me is that I can't find that it is in which file of the source code that samba sends a system call for writing or opening.


> **lmarmisa said:**
> [Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") is a implementation of the [SMB/CIFS networking protocol]("http://en.wikipedia.org/wiki/Server_Message_Block"). Samba allows file and print sharing among computers.

[Samba]("http://www.samba.org/") does not define the internal method used on the server for accessing to the storage devices (SATA, IDE, SCSI, RAID, etc). This is out of the scope of Samba. Anyway the server uses the operating system (normally UNIX/Linux) capabilities for accessing to the stored files. But this is not a part of the Samba protocol.

These links explain the SMB/CIFS protocol:

[http://www.samba.org/cifs/docs/what-is-smb.html](http://www.samba.org/cifs/docs/what-is-smb.html)

[http://ubiqx.org/cifs/index.html#Contents](http://ubiqx.org/cifs/index.html#Contents)

[http://www.codefx.com/CIFS_Explained.htm](http://www.codefx.com/CIFS_Explained.htm)

---

### Post by northd_tech on 2011-09-05
There are 3 "online" books included in the Samba Web Administration Tool (SWAT) "Home" page- have you looked at them yet?  The Developers' Guide is probably a good place to start.

[http://localhost:901/swat/help/using_samba/toc.html](http://localhost:901/swat/help/using_samba/toc.html)

[http://localhost:901/swat/help/Samba3-Developers-Guide/](http://localhost:901/swat/help/Samba3-Developers-Guide/)

You can find the installation instructions for SWAT linked on this thread:

[http://ubuntuforums.org/showthread.php?t=1839179](http://ubuntuforums.org/showthread.php?t=1839179)

EDIT:  Alternately, here are some resources for the Samba developer:

[http://devel.samba.org/samba/docs/](http://devel.samba.org/samba/docs/)

---

