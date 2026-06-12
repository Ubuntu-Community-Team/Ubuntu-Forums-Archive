---
title: "Cannot start NFS - Karmic"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by uonedang on 2009-12-14
Hi all,
 
I tried to start the nfs server .. by running /etc/rc2.d/S20nfs-kernel-server ... and I got the followings:
 
* Exporting directories for NFS kernel daemon ... **[OK]**
* Starting NFS kernel daemon 
 
and it hangs ... .. and I got these entries in the syslog:
 
nfsd [2138] nfssvc: Setting version failed: erron 16 (Device or resource busy)
kernel: [] rpcbind: server localhost not responding , timeout
kernel: [] rpcbind: server localhost not responding , timeout
 
And after killing the S20nfs-kernel-server .. I got this entry:
 
kernel: [] svc: failed to register lockdvl RPC service (errno 512)
...
 
I have the following packages installed (for nfs)
 
nfs-common
nfs-kernel-server
libnfsidmap2
portmap
 
 
I am not sure what I have missed .. configuration or missing packages ? 
 
Thanks,
 
Dang

---

### Post by njparton on 2010-01-13
Did you ever resolve this?  I'm getting RPC errors when trying to mount nfs shares.

---

### Post by johnson.d on 2010-01-13
The entries in the syslog file say that the RPCBIND is not working.

That can be corrected by the following steps:

1) In Ubuntu 9.10, we can check whether the rpcbind service is running or not, by using the command /etc/init.d/portmap status.
2) If it is not found running, use the command /etc/init.d/portmap start.
3) After the portmap service gets started, start the nfs server.

---

### Post by uonedang on 2010-01-19
thanks ... 

I will try that 

Dang
> **johnson.d said:**
> The entries in the syslog file say that the RPCBIND is not working.

That can be corrected by the following steps:

1) In Ubuntu 9.10, we can check whether the rpcbind service is running or not, by using the command /etc/init.d/portmap status.
2) If it is not found running, use the command /etc/init.d/portmap start.
3) After the portmap service gets started, start the nfs server.

---

### Post by uonedang on 2010-01-19
Hi 

I have not resolved this problem ... and I will try as suggested by johnson.d.

Thanks

Dang
> **njparton said:**
> Did you ever resolve this?  I'm getting RPC errors when trying to mount nfs shares.

---

