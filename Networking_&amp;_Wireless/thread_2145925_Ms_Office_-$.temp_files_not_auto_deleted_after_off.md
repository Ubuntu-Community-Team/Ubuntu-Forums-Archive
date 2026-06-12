---
title: "Ms Office -$.temp files not auto deleted after office document closed"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by JunixPAman on 2013-05-16
Hello,

Just joined and my first post.

Yesterday I just finished creating a Ubuntu Server for use as a network storage.  I have an external hard drive and a second internal hard drive that I share thu SAMBA.  Everything works fine I can access, create add and delete files and folders.  However when I modify any Microsoft office document (2010 or 2007) after closing the document the -$.tmp file that Office creates when the document is being modified for recovery is not automatically deleted. 
I am connecting the Ubuntu Server to Windows 7 64 bit.  Ubuntu is running as a guest machine on Oracle Virtual box.  The drives are connected to Ubuntu via Virtual box shared folders / guest additions and mounted to the server via FSTAB.  

The SAMBA Authentication is User with Guest Account as nobody.  The drives both allow guests.  The folders in Ubuntu where the drives are mounted ownership (CHOWN) was changed to nobody.nogroup. The Ubuntu OS is the server eddition 12.04 and already ran the apt -get updates and apt- get upgrade.

Can someone assist with ensurig the microsoft office files are deleted automaticaly after the office program is closed?

Oh and yes I can delete the -$.tmp files manually.

Thank You,

---

### Post by Doug S on 2013-05-17
Hi And welcome to Ubuntu forums.

I have office 2007 and samba running on a few Ubuntu servers. I tried both excel and word, from a windows vista computer, on files on the server. The temporary files deleted fine when I closed the spreadsheet or document. Although my temporary file names didn't seem to be same as yours. I might be able to try a windows 7 computer tomorrow.

---

