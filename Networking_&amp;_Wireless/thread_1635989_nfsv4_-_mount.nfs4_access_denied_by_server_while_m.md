---
title: "nfsv4 - mount.nfs4: access denied by server while mounting"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by edwin11 on 2010-12-02
Hi all,

i'm trying to setup a nfs4 server and client.

i followed the instructions in
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) (nfsv4 quick start section) and
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

The SERVER is on 192.168.89.1 running Xubuntu 10.04,
and the CLIENT is on 192.168.89.128 running Ubuntu 10.10.

Firewall is disabled on both the server and the client for testing purposes.

/etc/default/nfs-kernel-server on the SERVER:
```
# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information, 
# see rpc.mountd(8) or http://wiki.debian.org/?SecuringNFS
RPCMOUNTDOPTS=--manage-gids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=no

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=
```

/etc/default/nfs-common on the SERVER:
```
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/?SecuringNFS
STATDOPTS=

# Do you want to start the idmapd daemon? It is only needed for NFSv4.
NEED_IDMAPD=yes

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=no
```

/etc/exports on the SERVER:
```
/home/myself/shared_folders					192.168.89.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/home/myself/shared_folders/common_shared			192.168.89.0/24(rw,nohide,insecure,no_subtree_check,async)
/home/myself/shared_folders/linux				192.168.89.0/24(rw,nohide,insecure,no_subtree_check,async)
/home/myself/shared_folders/linux/common_linux			192.168.89.0/24(rw,nohide,insecure,no_subtree_check,async)
```

/etc/default/nfs-common on the CLIENT:
```
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/?SecuringNFS
STATDOPTS=

# Do you want to start the idmapd daemon? It is only needed for NFSv4.
NEED_IDMAPD=yes

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=no
```

i then did
```
/etc/init.d/nfs-kernel-server restart
```
on the SERVER to ensure that the nfs server is started, and got the output on /var/log/syslog:
```
Dec  3 03:42:25 mydesktop kernel: [  137.690268] nfsd: last server has exited, flushing export cache
Dec  3 03:42:26 mydesktop kernel: [  138.756274] svc: failed to register lockdv1 RPC service (errno 97).
Dec  3 03:42:26 mydesktop kernel: [  138.757320] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec  3 03:42:26 mydesktop kernel: [  138.757337] NFSD: starting 90-second grace period
```

Then i did on the CLIENT:
```
sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.89.1:/common_shared common_shared
```
and got the output:
```
mount.nfs4: access denied by server while mounting 192.168.89.1:/common_shared
```

There's no message on both the server and the client's /var/log/syslog.

Some additional information:
My SERVER is actually a VMWare HOST, and my CLIENT is a VMWare GUEST on the server, but i doubt it should matter.

What have i done incorrectly?

On the [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo), i see some steps related to portmap on the "NFS Server" and "NFS Client" sections. Would i need those steps as well?

There's also a list of steps on [http://www.citi.umich.edu/projects/nfsv4/linux/using-nfsv4.html](http://www.citi.umich.edu/projects/nfsv4/linux/using-nfsv4.html) (linked from [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)). Are those necessary?



Thanks,
Edwin

EDIT:
Running showmount on the client seemed to show that NOTHING is shared on the server:
```
$ showmount -a 192.168.89.1
All mount points on 192.168.89.1:
```

---

### Post by edwin11 on 2010-12-03
TO ADD:

Confirm that the CLIENT does try to reach the SERVER. i tested again, forgetting to turn off firewall on the SERVER, and can see a rejected connection from the CLIENT to port 2049.

---

### Post by edwin11 on 2010-12-04
UPDATE:

i found that the problem is due to

1. The folder that i was trying to access on the SERVER has got permission 700.

2. It doesn't match the uid on the SERVER with the uid on the CLIENT.

The folders i was trying to access on the SERVER are all owned by uid 1000, with permission 700.

But, after setting the permission to 777, and doing a successful mount, the mounted folder is owned by nobody:nogroup.

Is it because of these 2 lines in /etc/default/nfs-common:
```
NEED_IDMAPD=yes
NEED_GSSD=no
```
?

The HowTo says:
> because we want UID/GUID to be mapped from names. This way, server and client do not need the users to share same UID/GUID.

In that case,

1. Should i set those 2 fields to "no" and "yes" respectively instead?

2. Or else, how do i make sure that the uid on the server is mapped to something useful on the client instead of nobody and nogroup?



Thanks,
Edwin

---

### Post by edwin11 on 2010-12-07
UPDATE:

The problem is that rpc.idmapd wasn't started.

By doing

```
sudo rpc.idmapd
```

on both the SERVER and the CLIENT, i can mount NFS share with correct gid/uid.

But, how can i get rpc.idmapd to be started on boot up, before processing of fstab? i would like to put the mounting of the NFS volumes in fstab.



Thanks,
Edwin

---

