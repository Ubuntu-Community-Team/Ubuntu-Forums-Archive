---
title: "NFS4 - UID Mapping - Permission denied"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by avajrd on 2010-10-14
I wanted to use NFS4 with id mapping.  I followed the write up at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and basically have everything working.

The problem is that I cannot write a file unless I have group write permissions.  On the server the user has uid = 1000, gid = 1000.  On the client the user has uid =1699, gid = 1000.  Both have the same user name.

On the client the directory listing properly shows the user name and the group name.  If the file on the server is 644, the client cannot write to the file.  If it is 664 on the server, then the client can write to the file.

/etc/export on server contains:
```
/export            172.24.84.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/myuser    172.24.84.0/24(rw,nohide,insecure,no_subtree_check,async)
```/etc/fstab on client contains:
```
nfsserver:/myuser /home/myuser/mntpoint    nfs4    rw,noauto,user    0    0
```Any thoughts?

---

### Post by annoyingrob on 2010-10-14
NFS doesn't look at the username at all, it only pays attention to UID and GID. The best option is to synchronize UIDs across all of your machines.

---

### Post by avajrd on 2010-10-15
> **annoyingrob said:**
> NFS doesn't look at the username at all, it only pays attention to UID and GID. The best option is to synchronize UIDs across all of your machines.

I'm aware of that for NFS up to V3.  It was my impression that with NFS4 uid and gid could be mapped with a name using idmapd.  From [https://help.ubuntu.com/community/SettingUpNFSHowTo:](https://help.ubuntu.com/community/SettingUpNFSHowTo:) 

There are three configuration files that relate to an NFSv4 server: /etc/default/nfs-kernel-server, /etc/default/nfs-common and /etc/exports. 

[LIST]
[*]Those config files in our example would look like this: In /etc/default/nfs-kernel-server we set: 
NEED_SVCGSSD=no # no is default
[*]because we are not activating NFSv4 security this time.
[*]In /etc/default/nfs-common we set: 
NEED_IDMAPD=yes NEED_GSSD=no # no is default
[*]because  we want UID/GUID to be mapped from names.
[*]This way, server and client  do not need the users to share same UID/GUID. Remember that mount/fstab  defaults to NFSv3, so "mount -t nfs4" is necessary to make this work.

 To export our directories to a local network 192.168.1.0/24 
we add the following two lines to /etc/exports 
/export       192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async) /export/users 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
[/LIST]
Maybe I'm reading that wrong, or missed a config someplace.

This is something else that supports my position:

[https://launchpad.net/ubuntu/lucid/+package/libnfsidmap2](https://launchpad.net/ubuntu/lucid/+package/libnfsidmap2)

**An nfs idmapping library**

     libnfsidmap provides functions to map between NFSv4 names (which are
 of the form user@domain) and local uid's and gid's.
         **Source package**

                 
[LIST]
[*]             ["libnfsidmap" 0.23-2 source package in The Lucid Lynx]("https://launchpad.net/ubuntu/lucid/+source/libnfsidmap/0.23-2")
[/LIST]

---

### Post by annoyingrob on 2010-10-15
Is your NFS share defaulting to v3 for some reason?

I didn't know about the UID mapping, that's really neat. You learn something new every day!

---

### Post by avajrd on 2010-10-15
I ran rpc.idmapd -fvvv on the command line on both machines.  It just may not be using nfs4 because my output looks different from some others I've seen on the forum.  I'll poke around a bit more, but I just resolved the uid and gid for the time being.  Oh well.

---

### Post by dioni21 on 2010-11-30
Hey, has anybody got a conclusion about this?

I am stuck at the same problem.

I think I got a "workaround" that may explain the bug, but is not acceptable as a solution.

If the host A mounts host B, you have this problem.  But, if at the same time, host B also mounts A, both in NFS4, it appears that the problem is magically solved.  I could not understand why, only looking into the logs, but I wonder if it could be some kinf of handshaking problem.

BTW: In my case, host A is Ubuntu Maverick (2.6.35-23-generic-pae) and host B is Fedora 13 (2.6.34.7-61.fc13).

Also, I did not try GSS authentication, yet.

---

### Post by ajoliveira on 2012-03-19
> **annoyingrob said:**
> NFS doesn't look at the username at all, it only pays attention to UID and GID. The best option is to synchronize UIDs across all of your machines.

Well, it seems that this is not quite the case...recently I upgraded a server from lucid to oneiric. What was initially thought as a simple task turned out to be somewhat complicated.
On that server I have both nfs and samba clients.
On the previous version I had the same group for all clients, and the shares worked perfectly on both nfs and smb.
I seems Oneiric nfs just pays attention to UID, if UID is different from client to server and GID is the same, nfs exports are read-only, even under 775 permissions (group write allowed).
The immediate work-around was to set up ownnership of shared dirs to UID 1000 (for nfs) and GID of the common group for samba.

# sudo chmod -R 775 <shared dir> 
# sudo chown -R  1000.GID <shared dir>

where GID is the ID of the common group.

This behavior of nfs completely ignoring GID looks like a serious NFS bug.
Beware that the validity of the wiorkaround is restricted to having the nfs user with UID=1000 on all the clients.

---

### Post by sffvba[e0rt on 2012-03-19
Old thread closed.


404

---

