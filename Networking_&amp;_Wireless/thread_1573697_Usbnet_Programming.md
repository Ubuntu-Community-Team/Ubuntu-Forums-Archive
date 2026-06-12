---
title: "Usbnet Programming"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by harsha1987 on 2010-09-13
Hi,
 
I have USB host-host cable which is used to transfer data between two PC, the usb cable got detected and I configured the IP address using ifconfig and I was able to PING to the other device.
 
Is it possible to use Usbnet thru socket programming using AF_INET for data transfer between the two PC??
 
With Best Regards,
Harsha

---

### Post by Perkins on 2012-02-13
I know this is an old post, but it deserves an answer.  If you can ping across the link, then everything is set up properly and you should be able to transfer data across it using any method supported by any Ethernet connection, including raw network sockets.

If transferring files, personally I would use SSH, or SMB, or NFS, or some other known-reliable protocol that will automatically handle any idiosyncrasies between the operating systems of the machines in question.

---

