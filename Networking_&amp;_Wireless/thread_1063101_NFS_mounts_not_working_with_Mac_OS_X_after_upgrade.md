---
title: "NFS mounts not working with Mac OS X after upgrade to hardy"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by gene02 on 2009-02-07
I just upgraded my system to Hardy Heron.  I have a bunch of media directories which are exported by NFS for mounting on my Mac system.  After the upgrade, the NFS mounts are very unstable.  Although I can read the files from the command line on the Mac, GUI applications which try to use those files keep timing out.  Are there any adjustments that I can make to the NFS exports to get back the stability I had under Gutsy?

I am seeing some error messages in syslog:
```

Feb  7 12:00:08 howler mountd[12144]: authenticated mount request from 192.168.0.6:1009 for /raid/music (/raid/music)
Feb  7 12:00:21 howler kernel: [10182.804839] statd: server localhost not responding, timed out
Feb  7 12:00:21 howler kernel: [10182.804870] lockd: cannot monitor lappy-2.local
Feb  7 12:00:56 howler kernel: [10217.740857] statd: server localhost not responding, timed out
Feb  7 12:00:56 howler kernel: [10217.740882] lockd: cannot monitor lappy-2.local
Feb  7 12:01:31 howler kernel: [10252.676884] statd: server localhost not responding, timed out
Feb  7 12:01:31 howler kernel: [10252.676911] lockd: cannot monitor lappy-2.local
Feb  7 12:02:06 howler kernel: [10287.612911] statd: server localhost not responding, timed out
Feb  7 12:02:06 howler kernel: [10287.612936] lockd: cannot monitor lappy-2.local

```

---

