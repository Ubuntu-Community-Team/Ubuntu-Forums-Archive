---
title: "Incorrect user-/group-mapping with NFS4"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by ronzo on 2011-05-17
My setup: 
1 server running Maverick (Server 64bit), 
multiple Clients (some running Maverick, some Natty)

When I am mounting NFS shares on one of my clients, NFS4 is used by default. Unfortunately, the mounts show 4294967294 as user and group. nfs-common looks like this (on server and clients):
```

NEED_STATD=no
STATDOPTS=
NEED_IDMAPD=yes
NEED_GSSD=no

```

idmapd.conf looks like this:
```

[General]
Verbosity = 0
Pipefs-Directory = /var/lib/nfs/rpc_pipefs
Domain = localdomain

[Mapping]
Nobody-User = nobody
Nobody-Group = nogroup

```

The only workaround I could find is mounting the share by using the option 'nfsvers=3' after having started rpc.statd manually (sudo rpc.statd start). (e.g. mount -tnfs -onfsvers=3 server:/home/myuser /mnt/myshares/myuser) BUT - that's only a workaround, not a real solution.

Thanks a lot in advance for your hints!

---

### Post by bwhite on 2011-05-26
On the client manually run the /etc/init.d/idmapd process.  That fixed it for me.

---

### Post by ronzo on 2011-05-27
Yesterday, I've tried it again... and everything worked as expected on one client (which had need_idmapd=yes set in /etc/default/nfs-common). So I did that on another client and everything worked too. (Strange because I could bet it did not work two weeks ago)

Another thing I do not completely understand is that the protocol used is NFS4 but the way the shares are exported on the server is NFS3-style. 

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) says:
"NFSv4 exports exist in a single pseudo filesystem, where the real directories are mounted with the --bind option"

Why does it work if I don't use NFS4-style exporting?

Thanks a lot in advance!

---

### Post by ricardo.m on 2011-06-01
I have a ubuntu 10.10 server and all client machines up to 10.10 are working fine regarding nfs mapping and ldap. 

I installed two new machines with 11.04 with basically the same packages, ldap and autofs are working fine but the uid/gid are not mapped correctly (they come up as 4294967294). The config files are all the same (e.g. NEED_STATD=no and NEED_IDMAPD=yes).

I can see that ldmaps is not running, but I am not able to start it manually, I run on the new 11.04 clients

```
sudo service idmapd start
idmapd stop/pre-start, process 2560
```

and right after 

```
sudo service idmapd status
idmapd stop/waiting
```

so, it seems that something is killing idmapd or not letting it start properly ...

One more thing, when I try to run any command with rpc_pipes I get the following (even with status or stop instead of start)

```
sudo service rpc_pipefs start
start: Unknown parameter: JOB
```

... any ideas?

---

### Post by beejee on 2011-12-09
Sorry for digging up an old thread but i can't find anything else about this on the forums.

I'm having the same thing as ricardo on 11.10, tried a clean install to test but idmapd does not start.

Does anyone have an idea?

---

### Post by jantle on 2012-05-29
I have resolved same problem.

I need to modify /etc/idmapd.conf
from:   Pipefs-Directory = /var/lib/nfs/rpc_pipefs
to:       Pipefs-Directory = /run/rpc_pipefs

---

