---
title: "N00b question about filesystems and creating a file server (running Ubuntu)."
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by KillrBuckeye on 2006-06-20
I am considering building a basic file server for my home to store all of our pictures, music, and video, as it quite silly to keep duplicate copies of all of this stuff on both my computer and my wife's computer.  However, I have some very basic questions as I am new to Linux and I have never created a file server.  

1) If I install Ubuntu on this fileserver rig, can I format the data storage partitions (/home) as ext3 and have all of the contents accessible from the Windows computers?  I am trying to convince myself that I can, but I thought that Windows cannot read from Linux partitions unless a special driver is installed.  Or is this only if the Windows machine is trying to read from a local hard drive?  In other words, if the Ubuntu server is reading the information and sending it to the Windows computers, the Windows computers should have no problems reading/writing this data, correct?

2) I did some Google searching and found some guides about how to set up Ubuntu as a file server, and much of the content just flew right over my head.  I am wondering why it is necessary to go through all of these measures to set up the server.  Can't I just do a basic Ubuntu install and then set up Samba so that my Windows machines can access the shared folders?  If so, what is the purpose of going through the lengthy process that these guides describe?

---

### Post by kb3hkg on 2006-06-20
if going through samba I believe an ext3 partition should be ok

---

