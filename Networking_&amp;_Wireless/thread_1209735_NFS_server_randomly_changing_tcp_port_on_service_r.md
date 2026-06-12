---
title: "NFS server randomly changing tcp port on service restart"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by npinto on 2009-07-10
Dear all,

For some reason, my nfs server is using a port different from 2049 when I restart its services.

For example, if I run "touch /nfs/foo" on the client side, and then run:

```

sudo /etc/init.d/nfs-common restart && sudo /etc/init.d/nfs-user-server restart && sudo /etc/init.d/portmap restart && sudo rpcinfo -p

```I get:

```

 * Stopping NFS common utilities                                         [ OK ] 
 * Starting NFS common utilities                                         [ OK ] 
Stopping NFS servers: mountd nfsd.
Starting NFS servers: nfsd mountd.
 * Stopping portmap daemon...                                            [ OK ] 
 * Starting portmap daemon...                                            [ OK ] 
   program vers proto   port
    100000    2   tcp    111  portmapper
    100024    1   udp   4000  status
    100024    1   tcp   4000  status
    100003    2   udp   2049  nfs
    100003    2   tcp    934  nfs
    100005    1   udp   4002  mountd
    100005    2   udp   4002  mountd
    100005    1   tcp   4002  mountd
    100005    2   tcp   4002  mountd
    100000    2   udp    111  portmapper

```or

```

 * Stopping NFS common utilities                                         [ OK ] 
 * Starting NFS common utilities                                         [ OK ] 
Stopping NFS servers: mountd nfsd.
Starting NFS servers: nfsd mountd.
 * Stopping portmap daemon...                                            [ OK ] 
 * Starting portmap daemon...                                            [ OK ] 
   program vers proto   port
    100000    2   tcp    111  portmapper
    100024    1   udp   4000  status
    100024    1   tcp   4000  status
    100003    2   udp   2049  nfs
    100003    2   tcp    943  nfs
    100005    1   udp   4002  mountd
    100005    2   udp   4002  mountd
    100005    1   tcp   4002  mountd
    100005    2   tcp   4002  mountd
    100000    2   udp    111  portmapper

```etc.

but if I wait for a few minutes, I can get the 2049 port back:

```

 * Stopping NFS common utilities                                         [ OK ] 
 * Starting NFS common utilities                                         [ OK ] 
Stopping NFS servers: mountd nfsd.
Starting NFS servers: nfsd mountd.
 * Stopping portmap daemon...                                            [ OK ] 
 * Starting portmap daemon...                                            [ OK ] 
   program vers proto   port
    100000    2   tcp    111  portmapper
    100024    1   udp   4000  status
    100024    1   tcp   4000  status
    100003    2   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100005    1   udp   4002  mountd
    100005    2   udp   4002  mountd
    100005    1   tcp   4002  mountd
    100005    2   tcp   4002  mountd
    100000    2   udp    111  portmapper

```Is there any way to correct that problem?

Thanks in advance.

Regards,

Nicolas

---

