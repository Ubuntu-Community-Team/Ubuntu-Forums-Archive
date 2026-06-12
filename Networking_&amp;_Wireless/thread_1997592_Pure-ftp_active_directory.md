---
title: "Pure-ftp active directory"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by araujovirtual on 2012-06-05
Hello all

i have instaled pure-ftpd with autenticated in active diretory (windows) work well horever..


I have a problem!!!

When a connect for ssh using a normal user ex:    User@mydomain 
i create normal folders files .. Del forlder.. Ren folder normal. And in local share as folder apperas when create e disapears when delete..

But when a connect via ftp.. I conect normal.. Put piles ..delete files.. Move files.. But not the same files appears in folder….
Only conect via ssh ou sftp work well.. But ftp i don’t work… work half terms….

Ex:

Connect via putty or other programs via ssh

$user = mkdir –p test  (create normal works)     in share folder windows (appears test)
$user = rm test (delete normal ) in share folder windows (dissapears test, works well normal works)


connect via ftp

ftp: Create a dir test (create normal) in /home/user/test apperas but in share folder windows (not show) diferent)

please help

sorry for my english

---

