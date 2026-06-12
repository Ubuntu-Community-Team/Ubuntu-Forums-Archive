---
title: "Problem with NFSv4 and idmapd"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Ping-wine on 2011-07-06
I have two users using NFS share. They exist on both server and client, but with different UID/GID.

client
```

$ id user1
uid=1003(user1) gid=1003(user1) groups=1003(user1)
$ id user2
uid=1004(user2) gid=1004(user2) groups=1004(user2)
```server
```
$ id user1
uid=1004(user1) gid=1004(user1) groups=1004(user1)
$ id user2
uid=1005(user2) gid=1005(user2) groups=1005(user2)
```When user1 creates a file in the shared directory, it becomes owned by id 1005.
When user2 creates a file in the shared directory, it becomes owned by id 1003.

To me these look like the client thinks it needs to convert uid for the server and sends 1004 instead of string user1, but at the same time server thinks client sent uid that is not converted and converts it again. If I disable idmapd on the client it shows everything being owned by 4294967294.

Is there something wrong with my configuration, a bug in the system or did I not understand the concept of idmapd?

Both machines are 10.04.2 server 32-bit.

Client: nfs-common 1:1.2.0-4ubuntu4.1, libnfsidmap2 0.23-2
Server: nfs-kernel-server 1.2.0-4ubuntu4.1, nfs-common 1:1.2.0-4ubuntu4.1, libnfsidmap2 0.23-2

/etc/default/nfs-kernel-server
```
RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS=--manage-gids
NEED_SVCGSSD=no
RPCSVCGSSDOPTS=
```/etc/default/nfs-common on both
```
NEED_STATD=no
STATDOPTS=
NEED_IDMAPD=yes
NEED_GSSD=no
```I changed NEED_STATD from empty to 'no' to eliminate possible autodetect failure, just in case, got the idea from this:
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people.

/etc/idmapd.conf on both
```
[General]
Pipefs-Directory = /var/lib/nfs/rpc_pipefs
Domain = dom.ain

[Mapping]
Nobody-User = nobody
Nobody-Group = nogroup
```Mount command on the client confirms type is nfs4.

Server logs:

```

Jul  5 16:13:00 server rpc.idmapd[824]: libnfsidmap: using domain: dom.ain
Jul  5 16:13:00 server rpc.idmapd[824]: libnfsidmap: loaded plugin /usr/lib/libnfsidmap/nsswitch.so for method nsswitch
Jul  5 16:13:00 server rpc.idmapd[827]: Expiration time is 600 seconds.
Jul  5 16:13:00 server rpc.idmapd[827]: Opened /proc/net/rpc/nfs4.nametoid/channel
Jul  5 16:13:00 server rpc.idmapd[827]: Opened /proc/net/rpc/nfs4.idtoname/channel
Jul  5 16:13:25 server rpc.idmapd[827]: nfsdcb: authbuf=client.dom.ain authtype=user
Jul  5 16:13:25 server rpc.idmapd[827]: nfs4_uid_to_name: calling nsswitch->uid_to_name
Jul  5 16:13:25 server rpc.idmapd[827]: nfs4_uid_to_name: nsswitch->uid_to_name returned 0
Jul  5 16:13:25 server rpc.idmapd[827]: nfs4_uid_to_name: final return value is 0
Jul  5 16:13:25 server rpc.idmapd[827]:  Server: (user) id "0" -> name "root@dom.ain"
Jul  5 16:13:25 server rpc.idmapd[827]: nfsdcb: authbuf=client.dom.ain authtype=group
Jul  5 16:13:25 server rpc.idmapd[827]: nfs4_gid_to_name: calling nsswitch->gid_to_name
Jul  5 16:13:25 server rpc.idmapd[827]: nfs4_gid_to_name: nsswitch->gid_to_name returned 0
Jul  5 16:13:25 server rpc.idmapd[827]: nfs4_gid_to_name: final return value is 0
Jul  5 16:13:25 server rpc.idmapd[827]:  Server: (group) id "0" -> name "root@dom.ain"

```after ls -lRA /srv/nfs-data/ on the client

```

Jul  5 16:17:28 server rpc.idmapd[827]: nfsdcb: authbuf=client.dom.ain authtype=user
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_uid_to_name: calling nsswitch->uid_to_name
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_uid_to_name: nsswitch->uid_to_name returned 0
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_uid_to_name: final return value is 0
Jul  5 16:17:28 server rpc.idmapd[827]:  Server: (user) id "1004" -> name "user1@dom.ain"
Jul  5 16:17:28 server rpc.idmapd[827]: nfsdcb: authbuf=client.dom.ain authtype=group
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_gid_to_name: calling nsswitch->gid_to_name
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_gid_to_name: nsswitch->gid_to_name returned 0
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_gid_to_name: final return value is 0
Jul  5 16:17:28 server rpc.idmapd[827]:  Server: (group) id "1004" -> name "user1@dom.ain"
Jul  5 16:17:28 server rpc.idmapd[827]: nfsdcb: authbuf=client.dom.ain authtype=user
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_uid_to_name: calling nsswitch->uid_to_name
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_uid_to_name: nsswitch->uid_to_name returned 0
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_uid_to_name: final return value is 0
Jul  5 16:17:28 server rpc.idmapd[827]:  Server: (user) id "1005" -> name "user2@dom.ain"
Jul  5 16:17:28 server rpc.idmapd[827]: nfsdcb: authbuf=client.dom.ain authtype=group
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_gid_to_name: calling nsswitch->gid_to_name
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_gid_to_name: nsswitch->gid_to_name returned 0
Jul  5 16:17:28 server rpc.idmapd[827]: nfs4_gid_to_name: final return value is 0
Jul  5 16:17:28 server rpc.idmapd[827]:  Server: (group) id "1005" -> name "user2@dom.ain"

```Client log:

```

Jul  5 16:13:24 client rpc.idmapd[768]: libnfsidmap: using domain: dom.ain
Jul  5 16:13:24 client rpc.idmapd[768]: libnfsidmap: loaded plugin /usr/lib/libnfsidmap/nsswitch.so for method nsswitch
Jul  5 16:13:24 client rpc.idmapd[770]: Expiration time is 600 seconds.
Jul  5 16:13:24 client rpc.idmapd[770]: Opened /proc/net/rpc/nfs4.nametoid/channel
Jul  5 16:13:24 client rpc.idmapd[770]: Opened /proc/net/rpc/nfs4.idtoname/channel
Jul  5 16:13:30 client rpc.idmapd[770]: New client: 0
Jul  5 16:13:30 client rpc.idmapd[770]: Opened /var/lib/nfs/rpc_pipefs/nfs/clnt0/idmap
Jul  5 16:13:30 client rpc.idmapd[770]: New client: 1
Jul  5 16:13:30 client rpc.idmapd[770]: nfs4_name_to_uid: calling nsswitch->name_to_uid
Jul  5 16:13:30 client rpc.idmapd[770]: nss_getpwnam: name 'root@dom.ain' domain 'dom.ain': resulting localname 'root'
Jul  5 16:13:30 client rpc.idmapd[770]: nfs4_name_to_uid: nsswitch->name_to_uid returned 0
Jul  5 16:13:30 client rpc.idmapd[770]: nfs4_name_to_uid: final return value is 0
Jul  5 16:13:30 client rpc.idmapd[770]: Client 0: (user) name "root@dom.ain" -> id "0"
Jul  5 16:13:30 client rpc.idmapd[770]: nfs4_name_to_gid: calling nsswitch->name_to_gid
Jul  5 16:13:30 client rpc.idmapd[770]: nfs4_name_to_gid: nsswitch->name_to_gid returned 0
Jul  5 16:13:30 client rpc.idmapd[770]: nfs4_name_to_gid: final return value is 0
Jul  5 16:13:30 client rpc.idmapd[770]: Client 0: (group) name "root@dom.ain" -> id "0"
Jul  5 16:13:30 client rpc.idmapd[770]: New client: 2
Jul  5 16:13:30 client rpc.idmapd[770]: Stale client: 1
Jul  5 16:13:30 client rpc.idmapd[770]: #011-> closed /var/lib/nfs/rpc_pipefs/nfs/clnt1/idmap

```after ls -lRA /srv/nfs-data/ on the client

```

Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_uid: calling nsswitch->name_to_uid
Jul  5 16:17:34 client rpc.idmapd[770]: nss_getpwnam: name 'user1@dom.ain' domain 'dom.ain': resulting localname 'user1'
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_uid: nsswitch->name_to_uid returned 0
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_uid: final return value is 0
Jul  5 16:17:34 client rpc.idmapd[770]: Client 0: (user) name "user1@dom.ain" -> id "1003"
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_gid: calling nsswitch->name_to_gid
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_gid: nsswitch->name_to_gid returned 0
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_gid: final return value is 0
Jul  5 16:17:34 client rpc.idmapd[770]: Client 0: (group) name "user1@dom.ain" -> id "1003"
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_uid: calling nsswitch->name_to_uid
Jul  5 16:17:34 client rpc.idmapd[770]: nss_getpwnam: name 'user2@dom.ain' domain 'dom.ain': resulting localname 'user2'
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_uid: nsswitch->name_to_uid returned 0
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_uid: final return value is 0
Jul  5 16:17:34 client rpc.idmapd[770]: Client 0: (user) name "user2@dom.ain" -> id "1004"
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_gid: calling nsswitch->name_to_gid
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_gid: nsswitch->name_to_gid returned 0
Jul  5 16:17:34 client rpc.idmapd[770]: nfs4_name_to_gid: final return value is 0
Jul  5 16:17:34 client rpc.idmapd[770]: Client 0: (group) name "user2@dom.ain" -> id "1004"

```

---

### Post by Ping-wine on 2011-07-11
I had to edit UID/GID to be same on both machines. It works but it's not optimal solution.

However, it would be great if someone could confirm similar system as described above works or doesn't work. When I have more time I could try to track down the problem or if there's more of us a bug report should be filed, I think.

---

### Post by biocyberman on 2011-11-21
Hi, 
I am having similar problem. And worse, even if I changed gid and uid to be the same on both servers, it does not work. My uid and gid on nfs client machines got changed to 65534, which is nobody, nogroup. They were working before I install LDAP authentication. So I think it has something to do with LDAP. However I checked ldap and nsswitch.conf, everything is fine. So this gave me no clue now. :(

---

### Post by lisanels47 on 2012-03-26
I've got ldap/autofs working now.  All Ubuntu 11.10 systems, both clients and servers.  I'm using NFS3, not 4.

From any client, when you log on, you get your home directory mounted from the server, and everything works very well.

When a client creates a file/directory, it is owned/grouped by them on the server.  Permissions work fine for the user/groups also.

But, on the client side, if you do a ls -l, the permissions and ownership of files reflects some huge number.  

Inside the GUI, if you right-click on a file and set permissions, it shows the file owner is -2, and the group as -2.  It also says you don't own the file.  So changing them won't work.

Don't know if this will help you out or not....

---

### Post by wintrmute on 2012-03-27
NFS V4 performs ID mapping, NFS V3 didn't, so the previous comment isn't terribly relevant to this discussion. (Although it is helpful, in pointing out that if you downgrade to V3 and ensure all your UIDs and GIDs are identical across all your servers, then things will work..)

Has anyone managed to solve the NFS V4 problem?
I've been hitting the same issue and not been able to resolve it - and it's still present in the Precise betas :(

---

### Post by wintrmute on 2012-03-27
Since this looks pretty similar to my issues, I thought I'd mention for future readers that I've created this bug to track the issue:
[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/966734](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/966734)

---

