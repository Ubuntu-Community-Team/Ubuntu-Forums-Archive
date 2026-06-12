---
title: "disk sleep in Plasma due to NFS"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by ukkuku3d on 2009-04-06
Always when I unplug my laptop from network my KDE plasma process falls into "disk sleep" and is not reacting anymore. This is visible in System Monitor.
After investigating some research, it came out that NFS causes that behaviour. The following I found out meanwhile:

[LIST]
[*]The mounted NFS shares are in general unrelevant for the plasma process, except they are gone, than they create the process to hang. If I unmount the shares before unplugging, everything works fine.
[*]Even the NFS parameters "soft" combined with "timeo" or "intr" in the /etc/fstab don't help. After some seconds plasma hangs. if diconnected from the network.
Currently the parameters are the following:
"...nfs nouser,defaults,atime,auto,rw,dev,exec,suid,soft,timeo=50,intr        0       0"
[*]I'm using Intrepid Ibex with KDE 4.2 on a IBM T40 notebook, but that should not matter
[/LIST]

Is thery any bug around with plasma or NFS? Or can I improve the the NFS mounting options?

Thanks a lot
  Achim

---

### Post by ukkuku3d on 2009-04-14
bump

---

### Post by ky1e on 2009-06-18
I have exactly the same problem hindering my productivity at work, I have not yet found a solution to this. Sigh

---

### Post by ukkuku3d on 2009-06-23
SuSE 11 with KDE4 offers a solution.
Once installed on another partition of the same laptop and entered the NFS mounts by YAST, it works seamless.
When the Laptop is unpluged, it automatically unmounts all NFS connections and one can continue working with Plasma...

BTW: KDE3 did not had this problem either, I've used it on the same Laptop with the same mounts. No problems...

Achim

---

