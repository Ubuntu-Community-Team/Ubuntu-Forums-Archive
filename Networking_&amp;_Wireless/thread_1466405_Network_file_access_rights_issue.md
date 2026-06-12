---
title: "Network file access rights issue"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Stonerz on 2010-04-30
I have recently setup my work computer on Ubuntu 10.04. I have installed Samba and smbfs and setup the shares to my networks drive in fstab. I used the same method I used to setup my netbook which is on Jaunty. 

My network on jaunty runs fine and I am able to open and save files and folders on the network drives through terminal and GUI route. If i type ls -l into the terminal the access for the files is -rwxrwSrwx for folders -drwxrwxrwx.

On the 10.04 machine, i can read and write files through GUI but through terminal it comes up with permission denied even if I try as root. When I do a ls -l on this machine, the access is different for files it is -rwxr-xr-x and folders drwxrwxr-x.

I cannot understand how this can be because i have setup the systems exactly the same. Any suggestions please. :)

---

