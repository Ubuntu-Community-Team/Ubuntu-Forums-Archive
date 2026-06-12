---
title: "Using UUID in Samba?"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by smcrossman on 2011-06-18
I'm still trying to figure out Samba & home networking my 3 machines.  I took a break to trouble shoot wireless connections (since tha is also the base of my home network), file management and external storage.

Now I think what I need to do is use UUID to identify my "server shares" (which will reside on an external HD) so if I need to move the HD to another machine or when I can finally attach it to a router/gateway I don't have to totally re-work the system.  My understanding is that labels/names change based on what the external storage is connected to but the UUID does not.

So how do I use UUID instead of names in setting up the shares?  
Right now I can (from the non-server machine) access the shared network  drive, but cannot access any others. (Makes sense...that share is  totally open).  On the remote drive I have samba installed but no samba  directory and it hasn't been configured (obviously).

On the standalone (where the HD is attached) I can access any of them by  mounting them where they are listed under Places, but through the  network menu I can access the shared drive, and the personal drive with  just one password entry (my login or sudo password).   The others  whenever I enter my login/sudo password I  get an unable to mount  error.  

My understanding is with the 2 passwords the first one should be my  login/sudo password and the second is my samba password.  I actually  think my current set up would be working if not for mounting issues so  now I just want to figure out how to switch over to using UUID instead  of label/name identifiers if I can.

---

