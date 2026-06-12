---
title: "Windows XP samba share - Can create &amp; delete but can't modify."
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by dariowvm on 2013-07-05
Hi, 


I have a Windows XP machine sharing the folder "share19".


It is mounted in Lubuntu 12.04 adding the next line to fstab:


//192.168.19.29/share19  /home/paul/folder cifs username=win_user,password=win_pass,iocharset=utf8,mode=0777,dir_mode=07&#8203;77 0 0


The user "paul" is a common user, not root, not sudoer, not nothing.


Loged like "paul" i can access to the share, create files and delete files but can't modify them.
I create a LibreOffice spreadsheet, but after close LibreOffice when i tried to re-open the spreadsheet, it opens in Read-Only mode. Same thing in the terminal with nano and plain-text files.


If i logon with the sudoer user and run programs with sudo, NO problem.


From machines with regular Ubuntu or Windows there's no problem neither.

---

