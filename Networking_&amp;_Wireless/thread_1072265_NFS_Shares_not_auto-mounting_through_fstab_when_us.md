---
title: "NFS Shares not auto-mounting through fstab when using wicd"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by wjp.reg on 2009-02-17
While many of you love to hate network-manager, and recommend wicd in it's place, I have discovered a problem with wicd and auto-mounting nfs files from my fstab.

This is not the case when using network-manager.

This occurred after swapping out network-manager with wicd (latest versions).  After a while I decided to restore network-manager and remove wicd to see if that would make a difference, and to my surprise, it did!  Using network-manager (again), my nfs mounts reappeared automatically after booting.

I would prefer to use wicd on my laptop for roaming purposes, and while it is a minor nuisance to ```
sudo mount -a
``` after connecting to my home network, I would prefer the nfs mounts to come up automatically as they do in network-manager.

Any ideas as to why this happens?

here are my fstab/nfs entries:

```
192.168.0.199:/home/wolf/downloads /home/wolf/downloads nfs rsize=8192,wsize=8192,timeo=14,intr,bg 0 0
192.168.0.199:/media/Elements/Music /home/wolf/Music nfs rsize=8192,wsize=8192,timeo=14,intr,bg  0 0
192.168.0.199:/media/Elements/Pictures /home/wolf/Pictures nfs rsize=8192,wsize=8192,timeo=14,intr,bg 0 0
```

I have seen other reports of this (and smb shares defined in fstab), but no adequate explanations/fixes as far as wicd is concerned.

Thanks,

Wolf

---

### Post by regala on 2009-02-17
> **wjp.reg said:**
> 

(snip)

Thanks,

Wolf

guess that it's simply because networkmanager uses its Dispatcher to run "mount -a" after any "connection succeeded" event, and wicd doesn't have this kind of feature. Oh yes it does. You can specify a script to be run in each wicd connection section. Just write a simple wrapper
```

#! /bin/sh

mount -a

```
and set wicd to run it with your preferred connection. do not forget to make the script executable.

br, mathieu

---

### Post by wjp.reg on 2009-02-17
Thanks Regala, I'll give it a go..

Cheers

---

