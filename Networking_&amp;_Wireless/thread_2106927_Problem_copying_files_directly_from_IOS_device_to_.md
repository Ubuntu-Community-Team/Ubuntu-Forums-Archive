---
title: "Problem copying files directly from IOS device to Samba share"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by Hawkway on 2013-01-20
This is my first home server and I'm relatively new to Linux and Ubuntu. I ran across a strange problem when trying to copy files direclty from an iPhone connected to my Windows 7 PC to a Samba share on my Ubuntu server. It hangs somewhere during the copy process and just stops there. I have to cancel the copy and then copy the files to a temporary location on my PC before recopying them to the Samba share.
 
I've copied hundreds if not thousands of files from my PC and other USB drives to the Samba share with no problem but the problem arises when I try to access the iPhone internal storage through Windows Explorer and copy to the Samba share.
 
Has anyone else seen this problem and is there a work around?  I'm not sure how to start troubleshooting the problem.

---

### Post by tgalati4 on 2013-01-20
Log into the Ubuntu machine open a terminal and look at the SAMBA log files.  Post anything that may be helpful:

```
cd /var/log/samba
ls -la
cat log.nmbd

```

Go through each of the files.  This will only troubleshoot the Linux side of things.  If the problem is within Windows7, then I have no clue how to troubleshoot it.

It might be a permissions problem.  You don't own the files on the iPhone until they are copied to a temporary directory in Win7.  Then you "own" them and are allowed to paste them into the Ubuntu/SAMBA shared directory.  Check the permissions of the files on the iPhone, then on the Windows temporary directory.  Then check the permissions of the Shared SAMBA directory.

---

