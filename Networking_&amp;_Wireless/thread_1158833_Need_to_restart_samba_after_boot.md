---
title: "Need to restart samba after boot"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Eraser007 on 2009-05-14
Hi,

I've recently upgraded my pc to Ubuntu 9.04 and I've a problem with accessing my shares.

When I want to access a share from a Windows machine (e.g. \\mypc\myshare) I get an error that it could not be found. 
If I try the same thing with the IP address in stead of the pc name, it works.

The pc is detected in the network because I can see it under 'My Network Places'.

When I restart the samba service and try to access the share again, everything works as it should be.
I don't think there is something wrong with my smb.conf otherwise it would never work.

Does anyone have an idea how I can solve this issue?

Thanks

---

### Post by pro003 on 2009-05-14
did you checked the name of your network i.e "WORKGROUP"?

and when you want to open a shared folder on linux from windows type in explorer/firefox 

smb://networkname/nameofcomputer/sharedfolder

---

### Post by Eraser007 on 2009-05-14
All my pc's are member of the same workgroup, that can't be the problem.

I've tried accessing the share through smb://... but Explorer throws an error that smb:// is an unknown protocol.

---

