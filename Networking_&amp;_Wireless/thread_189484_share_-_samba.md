---
title: "share - samba"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by hammam on 2006-06-05
Hi all,
        I want to share data between two machine the first one has opensuse linux 10.1 and the other machine has winXP, I know we use samba in this matter, but could someone tell me how to do it ?
...   thanx
Mohammed Hammam

---

### Post by tkjacobsen on 2006-06-05
i am not familiar with samba myself, but you can find information in these howtos:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba) [http://www.oreilly.com/catalog/samba2/book/toc.html](http://www.oreilly.com/catalog/samba2/book/toc.html)

---

### Post by hammam on 2006-06-07
Hi ubuntu,
               I have went through the documents you provided. So I 'll explain the problem I face 
        I have two machine the first one has linux opensuse 10.1 and the other has winxp connected both by lan. I mounted the shared files from the first machine by using samba
my computer in desktop then network folder then SMB shares then workgroup, I found my share file in read only mode, when I tried to write in it says 
'access denied to smb://pc01/shared file
Could you tells how to write on these shared files ?
...   thanx
Mohammed Hammam

---

### Post by henry95 on 2006-06-07
[http://ubuntuguide.org/wiki/Dapper#Samba_Server]("http://ubuntuguide.org/wiki/Dapper#Samba_Server")

All the information you need is there.  Pretty much just copy the config file that is posted for you and modify it a little to match what you need to do.

---

