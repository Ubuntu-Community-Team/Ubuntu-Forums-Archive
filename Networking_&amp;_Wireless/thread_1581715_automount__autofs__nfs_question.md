---
title: "automount / autofs / nfs question"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by ghat on 2010-09-25
hi 

this is really for a senior unix administrator... 

Here is what I want to do...

I have a network file server (doing samba, NFS and LDAP)

I have multiple linux notebooks and a desktop.... 

I want to automount my home from the NFS server, (well now thats easy isn't it... )
however I want the automount client to first check if the NFS server is accessible and mount it, but if it is not accessible I want it to mount my local filesystem... 

If we were two add to entries to the map the localhost one would almost always repond first and would be mounted before the networked fs... Is there any wat to specify a lower priority or bigger timeout for the local fs so that the nfs would have a chance to mount first....

Ghat

---

### Post by sikander3786 on 2010-09-25
> 
this is really for a senior unix administrator... 

No need to bind your thread to senior administrators. :-) Junior adminstrators as well as new users may also be well able to give you some ideas. That way it makes one to think twice before he answers and most of time he gives up.

---

