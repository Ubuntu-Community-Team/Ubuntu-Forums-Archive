---
title: "Linux to Linux, like Windows Homegroup?"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by dbaybay on 2010-08-03
I am new to linux and these forums and have a few questions.

I installed Ubuntu on both my desktop and laptop and have them dual booted with Windows 7 Professional on each. I'm having a very hard time figuring out how to store all my files locally and share linux to linux kinda like Windows homegroup?

I wish there was a way to get everything accessible on each computer. Can anyone help?

---

### Post by v1ad on 2010-08-03
through console

lookup ssh, scp, rsync, sshfs.

scp file_directory username@ip_address:./location

if u want graphical copy paste use sshfs

make a directory

mkdir 1

---

### Post by Dr_Willis on 2010-08-03
linux to linux - has lots of options.

For casual usage, the file manager has the 'places --> connect to server' tool where you can use ssh/sftp to access the remote box.

For a more 'permanent' way that works with all apps transparently sshfs is very very handy.

For an actual server setup to share stuff to a whole network. 'nfs' is  the service to look into.

---

### Post by drdos2006 on 2010-08-03
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

regards

---

### Post by dbaybay on 2010-08-03
> **drdos2006 said:**
> [http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

regards

Thanks for replying guys.. Reai new to Linux/Ubuntu - so I'll some research!

---

