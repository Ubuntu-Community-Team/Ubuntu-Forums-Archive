---
title: "poor performance of mounted samba share"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2010-01-05
I access this share from nautilus, (SMB://server/share) :
Speed: 50MB/s  (38sec to get a 2GB file).


then I mount it using mount -t CIFS //server/share -o ...
Speed: 22,3MB/s (1minute 25sec per 2GB)

Why is the mounted partition that extremely slow ?

(And "yes", I need it mounted, so rsync can access it.)

---

### Post by shairozan on 2010-01-05
It's purely in the protocols. SMB is historically a slower-to-react method of transmitting files due to required CPU usage and the man-in-the-middle methodology of how it delivers files. Does the device you're attempting to connect to support NFS? If so, I would try mounting the drive as an NFS share.

---

### Post by Andre-D on 2010-01-05
it cannot be just protocol.

when I use nautilus, I connect to the very same server/share, (a windows 2003 server) - and it's fast, .. when I mount the device it's suddently much slower ? - cannot blame that on protocol.

---

