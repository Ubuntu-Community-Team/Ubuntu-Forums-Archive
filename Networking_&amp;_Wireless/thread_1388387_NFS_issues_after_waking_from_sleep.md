---
title: "NFS issues after waking from sleep"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by draculr on 2010-01-23
I seem to have a VERY annoying issue relating to NFS mounts from my QNAP NAS in ubuntu 9.10 x64.

Whenever I wake from sleep, I need to wait ~10 minutes to access my NFS mount again. The NAS is never shut down and this happens whether I allow the NAS drives to spin down or not (not that it would take 10 minutes for them to spin back up).

Anything accessing the NFS mount is frozen (fair enough, that is a known NFS 'feature') but I don't understand why the NFS mount is just dead? Is something not properly being reinitialised after waking from sleep? If I reboot immediately the mounts are fine, it only occurs when waking up and it is EXTREMELY annoying.

Any ideas on why this is happening?

---

