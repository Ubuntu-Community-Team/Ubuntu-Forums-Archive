---
title: "Airlink101 ANAS350 Ubuntu 9.10"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by markosjal on 2010-05-20
I have an Airlink101 ANAS350, that I have used with various versions of Linux via SMB/CIFS

I have noticed , particularly with ubuntu, that if I would mount the NAS and went back later to access a file it would often say iot was inaccessible and the folder that I tried to access would disappear. I would then refresh the folder list and the folder would be accessible. 

When I started using Mint 8 (based on ubuntu 9.10) a few weeks ago, I set up a permanent mount via

//192.168.2.253/Storage/ /media/AirNAS cifs username=guest,password= 0 0
in etc/fstab

The NAS has no password.

This seemed to resolve the issue with the folders disappearing, but then later when I created a folder from Mint via this mount , it would show up with a lock icon on it, and will not allow me to write a file to it

If I then access the drive by the network icon, windows network,  and entering SMB://IP/Path  it then monuts and  I can read AND WRITE by accessing it that way

I suspect part of what may be happening has to do with the newer CIFS vs the older SMB??

I am a little confused and need good reliable access to my NAS


Thanks in advance for any help

---

