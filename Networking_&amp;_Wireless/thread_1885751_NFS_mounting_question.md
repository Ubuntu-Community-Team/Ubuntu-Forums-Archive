---
title: "NFS mounting question"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by phil_elvey on 2011-11-23
Hi Everyone,

Have a query about mounting NFS shares.  I an Ubuntu 11.04 box and Mythbuntu 11.04 box.  

On the Ubuntu box I export my home directory to the whole local subnet (192.168.6.0/24)

On the Mythbuntu box I mount the directory using /etc/fstab to a sub-folder of my Mythbuntu home directory.

This works great, except that if my Ubuntu machine is turned off, and I go to open Nautilus (or whatever the file explorer is) in Mythbuntu, I can't access my home folder and it just hangs, presumably because it can't access my mounted folder anymore.

How can I get it to mount so that if my Ubuntu machine is turned off, it will ignore the fact it can't access the mounted folder and still allow me to browse my home folder?

I have searched already and tried a few different options but to no avail.  The current mount command in fstab is:

```
192.168.x.x/home/phil /home/phil/mount-folder nfs ro,soft,timeo=4,retry=1,intr 0 0
```

If anyone can help with this I would be very thankful

Cheers
Phil

---

