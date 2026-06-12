---
title: "Cannot mount Windows network shares"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by temporos on 2010-02-13
I am trying to share files on my Windows XP Home machine over my P2P network to my Ubuntu netbook.  The folder I wish to share is configured in Windows with public permissions.

I go to the Files & Folders > Documents and then I click on Network in the Places tab.  A Windows Network icon appears, but when I double click it I receive the error message, "Unable to mount location.  Failed to retrieve share list from server."  What am I doing wrong?

---

### Post by Iowan on 2010-02-13
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To for Windows browsing problems. Have you tried the connection via Places>Connect to Server?

---

### Post by temporos on 2010-02-18
Thanks.  I switched my workgroup on my Windows machine to "WORKGROUP", and now it works.  The connection fails frequently, though.  I think that's a Windows issue...  Windows doesn't like to play nice with other OS'.

---

