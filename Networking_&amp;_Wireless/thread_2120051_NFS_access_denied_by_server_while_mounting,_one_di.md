---
title: "NFS: access denied by server while mounting, one direction only"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by Razmear on 2013-02-25
Hi,
I'm kind of a noob when it comes to setting up NFS and linux networking, but I finally found a good How To Guide ( [http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/) ) and managed to get PC 2 to connect to PC 1 with full access, but when PC 1 tries to connect to PC 2 I get these errors: 

sudo mount /home/eb/NetShares
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
mount.nfs: an incorrect mount option was specified

sudo mount /home/eb/NetShares -o nolock
mount.nfs: access denied by server while mounting 192.168.1.104:/home/kelley/Videos

Both machines are Kubuntu 12.4 and the networking was setup identically between the two machines following the guide linked above. Been searching on this one for a while and not having much luck. If anyone can point me in the right direction I'd appreciate it. 
Samba has been uninstalled on both PCs and Firewalls are off.

---

### Post by Razmear on 2013-02-25
OK, I redid the steps on PC 2 and found the error in the exports file, fixed it and all is good.

---

