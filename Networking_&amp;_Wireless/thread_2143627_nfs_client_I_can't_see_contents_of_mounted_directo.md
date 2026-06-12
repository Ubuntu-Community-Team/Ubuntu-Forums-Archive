---
title: "nfs client: I can't see contents of mounted directory"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by mark1977 on 2013-05-09
Hi,
I have installed nfs-client in 12.04 and it connects to my 12.04 server (which runs nfs-server).
On the client I have /etc/fstab:

```
ghost1:/mirror  /mirror  nfs  _netdev
```

The option "_netdev" doesn't seem to make a difference. My client can ssh into my server fine. My client is configured to get ip from the server via dhcp and does so fine.

However when I list the contents of /mirror on the client it is empty (it shouldn't be). I thought maybe it had not been mounted so:
```
mount ghost1:/mirror /mirror
```
just tells me
```
mount.nfs: /mirror is busy or already mounted
```

Why is my directory shown as empty?

I think the server should be okay because I CAN see the directory contents on another client (identical hardware) configured in exactly the same way...

Thanks

Mark

---

### Post by 2F4U on 2013-05-10
Is portmap properly configured? If not, UID/GID on client and server would need to share the same UID/GID:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by mark1977 on 2013-05-10
> **2F4U said:**
> Is portmap properly configured? If not, UID/GID on client and server would need to share the same UID/GID:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I can't see any important differences in my config files:

```
more /etc/idmapd.conf 
[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup


```

```
more /etc/default/nfs-kernel-server
# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS=--manage-gids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=

# Options for rpc.nfsd.
RPCNFSDOPTS=


```

Besides, my user has the same ID and GID on both the server and the client...

Are there log files I can check?

---

