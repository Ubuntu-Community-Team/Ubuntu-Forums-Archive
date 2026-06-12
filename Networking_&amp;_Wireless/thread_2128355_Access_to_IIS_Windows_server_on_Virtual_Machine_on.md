---
title: "Access to IIS Windows server on Virtual Machine on my Ubuntu Server"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-03-22
Hello fine people!  I have a problem.  I need to access a file with ajax, that is on my server....but within a windows IIS server on a VM  on my Ubuntu server if that makes any sense.  

I can easily use ajax, jquery or php to access any file on my ubuntu server.  But when I reference the virt server....it gives me "404's" that the page is not there or I don't have access to it.  Is it possible to actually do this?  The structure of my system is:

```
myUbuntuServer.com -> myUbuntuServer.com/ajax_info_I_can_access.txt 

myUbuntuServer.com -> myUbuntuServer-virtMachine1->myUbuntuServer-virtMachine1/ajax_info_I_really_need_bad.txt
```

I can show you code if you'd like but it's simple ajax calls that I've tested and they work.  So it's an issue with network setup.  Thanks a lot for all the help.):P

---

