---
title: "mount.nfs4: access denied by server"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by jcobban on 2011-08-03
I followed all of the advice in the NFS installation guide, but I end up with:

$ sudo apt-get install nfs-common
$ sudo gedit /etc/default/nfs-common

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
$ sudo modprobe nfs
$ sudo mount -t nfs4 -o proto=tcp,port=2049 linux-server:/ /mnt
mount.nfs4: access denied by server while mounting linux-server:/

I see reports of this issue in various forums, but I cannot see any resolution.

I am running the server "linux-server" on 11.4 and the client on 10.4.

All I want to do is be able to mount the user folder on the server on the client.  This seems an excessively complicated and error prone procedure for such a straightforward task.

---

### Post by monkeyMonk on 2011-08-30
Hi,
  I'm not sure if this can help you.  I had seen the same problem when I'm tuning the NFS4 server initial script. So when I back off the changes, the problem gone away.
  Here is my story.
  By reading many documents from the Internet, I find out the NFS server start/stop script on Ubuntu provides NFS server on version 2,3,4 simultaneously, which increases security risk and wastes memories. So I decide to trim off NFS version 2 and 3, leave version 4 only. I had this done successfully. After then, by run command  rpcinfo -p , I can see that the nfs server accepts NFS version 4 only.  Then I try to trim down further to those so-called side protocols such as portmap mountd etc.  It is OK when I shutdown portmapper, however, I had problem when I remove mountd, or so-called rpc.mountd,  I get the error on the client side when I try to mount NFS4 server's exported, the error is exactly same as yours, "mount.nfs4: access denied by server while mounting linux-server:/".  This really confused me. Some documents tell me that rpc.mountd only used for NFS version 3 and before, the mount protocol has been included into NFS main protocol in version 4.  By check the man rpc.mound, it also says so. On ubuntu, the NFS server start/stop script runs mountd to support version 1 to version 3. I tried to disabled other version on rpc.mountd and leave only one version, then I find no matter which version of mountd I left it on, as long as rpc.mountd is running, the NFS4 client will go through the nfs4 mount.

I'm not sure if this can help you. My suggestion is run rpcinfo to check the configuration on server and client. 

From client, run "rpcinfo -p" check local config.  
             run "rpcinfo -p  server_ip_addr" to check server's config.

Here is my server's rpcinfo, (I already had some things trimmed off, but works)

    program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  37348  status
    100024    1   tcp  34469  status
    100021    1   udp  37025  nlockmgr
    100021    3   udp  37025  nlockmgr
    100021    4   udp  37025  nlockmgr
    100021    1   tcp  45900  nlockmgr
    100021    3   tcp  45900  nlockmgr
    100021    4   tcp  45900  nlockmgr
    100003    4   udp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  46644  mountd
    100005    1   tcp  37350  mountd


Good luck.

---

### Post by jcobban on 2011-09-15
I am not a LINUX guru.  All I want to do is mount a folder on my server so it is accessable to my laptop.  Why is that so made so difficult?

```
$ sudo rpcinfo -p linux-server
[sudo] password for jcobban: 
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  54033  status
    100024    1   tcp  49996  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100021    1   udp  54388  nlockmgr
    100021    3   udp  54388  nlockmgr
    100021    4   udp  54388  nlockmgr
    100021    1   tcp  46714  nlockmgr
    100021    3   tcp  46714  nlockmgr
    100021    4   tcp  46714  nlockmgr
    100005    1   udp  60880  mountd
    100005    1   tcp  44700  mountd
    100005    2   udp  60880  mountd
    100005    2   tcp  44700  mountd
    100005    3   udp  60880  mountd
    100005    3   tcp  44700  mountd
jcobban@jcobban-laptop:~$ sudo mount -t nfs4 -o proto=tcp,port=2049 linux-server:/ /mnt
mount.nfs4: access denied by server while mounting linux-server:/
jcobban@jcobban-laptop:~$ 

```

---

