---
title: "Samba working - but not secure?"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2009-01-27
I finally got Samba working on my Ubuntu 8.10 guest image (I am using VirtualBox 2.1.0 on a Windows host), it correctly appears on the network in the same workgroup as the Windows PC and even Nautilus shows other Windows PCs on the network.

The trick to getting it working was unchecking "Block broadcasts from external networks" under Firestarter advanced options.

I have been reading and re-reading this thread [Samba and Firestarter]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access") to try and make sense of it (I assume it is still valid), but it is a bit too technical for a total newbie like me and I am puzzled as to why the changes to "/etc/firestarter/inbound/setup" did not seem to work for me.

I am just worried that I have created an insecure set-up and that the Ubuntu image is now exposed to the vagaries of the internet.  I do hope to make the switch fully to Ubuntu, but only when I am sure I understand what I am doing.

Thanks for any advice.

edit: After reading again(***!***) that thread, I think I am finally beginning to get it.  I will need to check my firestarter/inbound/setup again and see if the updates are still valid.

---

