---
title: "retry nfs mount when NAS boots after unbuntu server"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by asteinmetz on 2009-06-14
I have a NAS with an NFS share that boots more slowly than the unbuntu server that is looking for it.  If I boot the NAS first all is good but mount apparently doesn't retry if it runs before the NAS is up, like after a power outage.  I have to manually mount it.

I am pretty clueless on the dark arts of file systems so I use Webmin to administer Ubuntu.  On the "Edit Mounts" page in Webmin the defaults include "Retry Mounts in background" which is set to "Yes."

Am I missing something?  Thanks.

---

