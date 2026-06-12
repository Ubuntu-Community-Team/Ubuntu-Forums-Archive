---
title: "Transfering files from Ubuntu 11.10 to Windows 7 (Using ethernet cable)"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by Radial.Head on 2012-01-16
Hello, 

I have been trying to transfer a lot of files (100gb) from one computer to another. One has Ubuntu 11.10 and the other one has Windows 7, both of them can connect using an ethernet cable. 

I have already checked out this tutorials and followed the steps and I don't seem to make it work:

[How to Access Windows 7 Shared Folders from Ubuntu | 7 Tutorials]("http://www.7tutorials.com/how-access-windows-7-shared-folders-ubuntu")  
[How to Enable File Sharing & Change the Workgroup in Ubuntu Linux | 7 Tutorials]("http://www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows")  
[How to Change the Workgroup in Windows 7 | 7 Tutorials]("http://www.7tutorials.com/how-change-workgroup-windows-7") 

Do anyone have another method, another tutorial or another way around this? 

Thanks in advance.

---

### Post by Iowan on 2012-01-16
SSH or FTP might be an option. At work, I use PuTTY on a (Windows XP) laptop to access my 8.04 server. Samba might work, but is probably overkill for a one-time exchange.
[Here]("https://help.ubuntu.com/11.10/serverguide/C/index.html") is a link to the Server Guide.

---

### Post by jonobr on 2012-01-17
Hello


If you have openssh on the ubuntu box , you could use winscp on the windows box.

Its pretty easy to copy over.

If openssh is not installed, the 

```
sudo apt-get install openssh-server
```
once you install and run winscp on the windows side, when it starts  enter the IP address and password and it should connect and have a windows explorer style interface to copy files.

Before you transfer you could also compress the files to make it a little smaller.

Mind you,  all the above is good to do, a thumb drive may be a lot quicker........

---

