---
title: "Slow wireless transfers on Ipad - Samba config?"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by chadwell on 2012-11-02
Folks,


I have an laptop running 12.04 Ubuntu, which is acting as a dedicated NAS.  I store all my photo and videos on it etc

I use Samba and smb.conf to share to other devices.  I can access it and transfer photos etc from my phone and a windows 7 netbook.  I get wireless transfer speeds of 2MB/sec on these devices.

I bought a new iPad and installed the paid app filebrowser - so I could access the NAS over wireless and copy files or view photos etc.  But the transfer speeds are 100KB/sec.

No matter what file I transfer I get really slow speeds.  I contacted the makers of file browser and they said it may be due to the packet size and there may be a way to change the packet size in the smb.conf.

I have searched and have not found anything.  I read about the socket options somewhere, and I uncommented out the line and changed to the following:

socket options=TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 

but this is in the MISC section of my SMB.conf - does it nee to be in global or does it not matter.

Any help appreciated

---

### Post by chadwell on 2012-11-05
Any ideas?

Really confused as to why the speeds would be ok when copying a file using a netbook, and using an Android phone - but not using an iPad.

Is it the app - 'FileBrowser' or is it something in the Samba settings?

---

### Post by chadwell on 2012-11-06
Just tried writing about 100 images (over 300MB worth) to the NAS drive from the iPad using filebrowser.

It took about 3 mins which is great and seems about right.  So the problem seems to be **reading** from the NAS?  Does this narrow the problem down any??

---

