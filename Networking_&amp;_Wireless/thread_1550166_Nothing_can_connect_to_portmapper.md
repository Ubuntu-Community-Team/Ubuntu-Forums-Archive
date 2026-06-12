---
title: "Nothing can connect to portmapper"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by sdavids on 2010-08-10
Ubuntu Lucid freshly updated as of now I cannot get anything to connect to the portmapper after the update.

It is running as far as I can tell:

rhubarb# ps aux | grep portmap  
daemon    1004  0.0  0.0   1892   516 ?        Ss   21:52   0:00 portmap -i 192.168.1.9 -v
rhubarb# rpcinfo -p rhubarb   
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper

192.168.1.9 is the correct IP address for rhubarb

Attempt to start NIS via 
rhubarb# service nis start

I get logged:
Aug 10 22:10:32 rhubarb ypserv[3424]: unable to register (YPPROG, YPVERS, udp).
Aug 10 22:10:32 rhubarb rpc.yppasswdd[3427]: unable to register yppaswdd udp service.
Aug 10 22:10:32 rhubarb rpc.ypxfrd[3430]: unable to register (YPXFRD_FREEBSD_PROG, YPXFRD_FREEBSD_VERS, udp).
Aug 10 22:10:32 rhubarb ypbind[3438]: Unable to register (YPBINDPROG, YPBINDVERS, udp).

If I attempt to start NFS via:
rhubarb# service nfs-kernel-server start
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                                   

and it hangs with no prompt returning and the following logged:
Aug 10 22:15:56 rhubarb nfsd[3754]: nfssvc: Setting version failed: errno 16 (Device or resource busy)

Note hosts.allow has:
ALL: 192.168.1. 127.
portmap: 192.168.1. 127.
so it should be able to connect.

This used to work with lucid and it only stopped after applying the latest updates.

So, is there an obvious thing I'm missing here which has changed?  
Has anyone got any rpc services successfully running with a fully updated lucid system?

Failing any joy on that are the updates listed somewhere with the date they were
applied and I guess I try backing them out until I find what caused my problem.

Thanks for any help.

---

