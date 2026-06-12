---
title: "Ubuntu --&gt; ncpmount --&gt; OpenOffice"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by lambugari on 2011-03-07
I have a Novell volume mounted successfully on Ubuntu. I am able to create and modify files with no problem except when using OpenOffice.

When I access a file with OpenOffice and try to save it, I get the following error:
Error saving the document [file]:
General input/output error while accessing:
/home/[U_usr]/[mount_dir]/[folders]/[file]

The syntax I am using to mount the volume is:
ncpmount -S [server_ip] -A [server_ip] -U [N_user.N_context] -V [volume] -u [U_usr] -g [U_grp] -f 777 -d 777 /home/[U_usr]/[mount_dir]

Cheers!

---

