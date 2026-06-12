---
title: "Nt_status_logon_failure"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by audireddy on 2011-05-25
Dear all
I configured samba in ubunt 10.10 after that i configured backuppc 
after that i got this problem 
but all xp client systems are mounted my ubuntu system  
how to solve this problem

Contents of file /var/lib/backuppc/pc/pacews032/XferLOG.bad.z, modified 2011-05-25 13:17:31 (Extracting only Errors) Running: /usr/bin/smbclient \\\\pacews032\\pacews032 -I 192.168.1.248 -U backup -E -d 1 -c tarmode\ full -Tc -
full backup started for share pacews032
Xfer PIDs are now 2066,2065
session setup failed: NT_STATUS_LOGON_FAILURE
session setup failed: NT_STATUS_LOGON_FAILURE
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (No files dumped for share pacews032)
Backup aborted (No files dumped for share pacews032)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)



Thanks

Audi

---

