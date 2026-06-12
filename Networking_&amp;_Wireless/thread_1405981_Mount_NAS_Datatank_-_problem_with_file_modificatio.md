---
title: "Mount NAS Datatank - problem with file modification dates"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by hmf1 on 2010-02-13
I installed a Freecom NAS Datatank on my network and automatically mounts the command in / etc / fstab 

/ / 192.168.2.105/datatank / media / DataTank cifs defaults, credentials = / root / .smbcredentials, umask = 0 0 0 

The disk mounts properly, however, I encounter a problem during synchronization, since the dates of the files are not stored ... 

By testing a copy of the file without mounting DataTank, but live on the network, I have no problem, the file dates remain unchanged. 

The problem seems related to the choice of editing, but I can not find the solution. 

The DataTank is formatted ext3 ... would the solution be there? 

thank you[IMG]http://www.google.fr/images/cleardot.gif[/IMG]

---

