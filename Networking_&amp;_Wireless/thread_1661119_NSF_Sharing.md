---
title: "NSF Sharing"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Mosabama on 2011-01-06
Hey,

I have a problem with NFS Share. I am doing all on the same computer.
Error:

```
sudo mount 192.168.1.2:/home/mosab/Desktop/mahmoud/ /home/mosab/Desktop/sambatest/
mount.nfs: access denied by server while mounting 192.168.1.2:/home/mosab/Desktop/mahmoud/

```

Export File:
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

#Added by me :

/home/mosab/mahmoud/ 192.168.1.0/24(rw,sync,no_subtree_check)



```

last couple of lines of dmesg:

```
[ 7088.375060] NFSD: starting 90-second grace period
[ 7204.628293] FS-Cache: Loaded
[ 7204.664510] FS-Cache: Netfs 'nfs' registered for caching
[ 7284.115670] nfsd: last server has exited, flushing export cache
[ 7285.183685] svc: failed to register lockdv1 RPC service (errno 97).
[ 7285.186328] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 7285.186360] NFSD: starting 90-second grace period
[ 9334.753121] nfsd: last server has exited, flushing export cache
[ 9335.811977] svc: failed to register lockdv1 RPC service (errno 97).
[ 9335.813935] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 9335.813975] NFSD: starting 90-second grace period
[ 9546.635954] nfsd: last server has exited, flushing export cache
[ 9547.704096] svc: failed to register lockdv1 RPC service (errno 97).
[ 9547.706321] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 9547.706353] NFSD: starting 90-second grace period
[ 9550.232791] nfsd: nfsv4 idmapping failing: has idmapd not been started?
[ 9565.776871] nfsd: last server has exited, flushing export cache
[ 9566.845344] svc: failed to register lockdv1 RPC service (errno 97).
[ 9566.847745] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 9566.847777] NFSD: starting 90-second grace period

```

Thanks in advance

---

### Post by gmargo on 2011-01-06
The path you exported, **/home/mosab/mahmoud/**, is not the same as the path you're trying to mount from, **/home/mosab/[COLOR=Red]Desktop[/COLOR]/mahmoud/**.  I suspect that is at least part of the problem.

---

### Post by Mosabama on 2011-01-06
Ops,, your right Iam sorry ...

it works now thanks.

any idea how to make the authentication User based not machine based ?

---

