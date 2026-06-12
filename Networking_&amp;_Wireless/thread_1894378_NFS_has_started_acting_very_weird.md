---
title: "NFS has started acting very weird"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by sreilly on 2011-12-12
I have a file server running Ubuntu 10.04 LTS and a number of CentOS 5 workstations whose /home is NFS'd from the server.
Up until Dec 2 (and for at least a year before) NFS had been working normally.
Then I started to see lockd errors in the log files;
statd: server rpc.statd not responding, timed out
lockd: cannot monitor <machine-name>

Not having changed any of the NFS setting on the server or clients I still do not know why this started to happen.

After a couple of days pulling my hair out as the users got more and more irate about not being able to log in to their KDE desktop (but GNOME worked), reinstalling the nfs packages, rebooting the server and all of the clients (a number of times), I decided to try mounting the clients as NFSv4 from the server (the server has always exported NFSv3 and NFSv4)
This worked!
But now I find that the server fails to mount (automount or nfs) exported dirs from other machines.
I have other Ubuntu 10.04 servers at the same site and they have no problems using nfs3 or automount.

The only changes to the default setting are
/etc/default/nfs-common has;
NEED_STATD=yes
NEED_IDMAPD=yes

/etc/default/nfs-kernel-server has;
RPCNFSDCOUNT=16

In desperation. What have I missed?

TIA,
Steve

---

