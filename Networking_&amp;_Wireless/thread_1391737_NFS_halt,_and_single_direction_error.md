---
title: "NFS halt, and single direction error"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by chrysler on 2010-01-27
There's a problem even if I checked google and some books, i.e.  [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")
So I post this question here.

The NFS environment can be created in my computers, however, there is a strange problem. I tried many times and change many parameters, but the problem still cannot be solved.

The details are described as follows:

There are two computer, says PC and notebook, which are installed ubuntu 9.10.

PC has /dataPC
notebook has /dataNB
Both of previous directories have many files and at least 200MB available space.

Now, I input following two commands in PC:
$ sudo mkdir /nb-nfs
$ sudo mount -t nfs (notebook&#30340;IP):/dataNB  /nb-nfs

Then, the notebook's  /dataNB  directory will be mounted as PC's  /nb-nfs successfully.

To copy files from PC to /nb-files is all right.  For example: $ cp  /media/usbdisk/*  /nb-nfs/

However, to copy files from /nb-files brings some problems.  For example: $ cp  /nb-nfs/*  /media/usbdisk/
The problems include:
1. The cp process halt, the copying action is stop.
2. The notebook's network connection is disconnect.  Firefox in the notebook can not browse web pages except reboot.
3. System monitor (ex. atop) indicates the data flows of network and disk are stop.

This problem occurs in sshfs, GlusterFS, NFSv3, NFSv4 etc..  I called this problem as single direction error.  I notice that the problem occurs when "mount" remote directories.
The other softwares, such as ftp, do not have this problem. The ftp softwares can upload and download files normally.  The problem still occurs if I keep iptables as default.

Please help me to solve this problem. Thank you so much.

---

