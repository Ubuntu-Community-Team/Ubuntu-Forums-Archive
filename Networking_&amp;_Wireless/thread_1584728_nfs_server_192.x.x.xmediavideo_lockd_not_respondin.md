---
title: "nfs server 192.x.x.x:/media/video: lockd not responding"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by jperkins008 on 2010-09-29
I have been using 10.4 as a Linux NFS server to share it's storage with a number of Mac computers we use in the office. All the Macs are configured to connect to the Linux server using the mount_nfs command in terminal.

I have been using this method to transfer files to and from the Linux server for a while. 

Today, I installed a number of standard Ubuntu updates / security patches per the standard GUI update tool. 

Now, I'm getting "nfs server 192.x.x.x:/media/video: lockd not responding" error messages. I have not seen this error before, and I haven't changed anything else about the configuration of the Linux server or the Macs with the exception of the installation of the security patches.

Any assistance would be greatly appreciated.

Thanks,

Josh




I'm using: 
Ubuntu 10.4 Lucid Lynx
Kernel info: 
Linux black 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux

---

### Post by dmizer on 2010-09-30
Here's a really good layout for troubleshooting this problem -> [http://docs.hp.com/en/B1031-90061/ch05s01.html](http://docs.hp.com/en/B1031-90061/ch05s01.html)

This is probably a server side problem.

---

