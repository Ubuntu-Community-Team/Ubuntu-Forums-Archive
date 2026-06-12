---
title: "Cant see mounted NFS volumes"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by ingeva on 2012-07-12
Network with client and server: Client sees server, server does not see client. Setup is identical in both computers.
NFS mounts on server are:

```
Plato:/My on /mnt/Plato/My type nfs4 (rw,rsize=8192,wsize=8192,intr,addr=10.10.10.2,clientaddr=0.0.0.0)
Plato:/Backup on /mnt/Plato/Backup type nfs4 (rw,rsize=8192,wsize=8192,intr,addr=10.10.10.2,clientaddr=0.0.0.0)
Plato:/Store on /mnt/Plato/Store type nfs4 (rw,rsize=8192,wsize=8192,intr,addr=10.10.10.2,clientaddr=0.0.0.0)

```I guess the problem is with clientaddr. I have tried "everything possible" to correct this, to no avail.
Problem started with 12.04 (like too many other problems! :( ).

Can anyone help?

---

### Post by ingeva on 2012-07-12
> **ingeva said:**
> 
Problem started with 12.04 (like too many other problems! :( ).

I have dropped 12.04 and have installed 10.04.
Unfortunately, it's now impossible to access 11.04 repositories. After they closed down support for it, the choice had to be 10.04 for the server, and Mint for the desktop.

If I wanted this kind of problems, I would still be using Windows.

---

### Post by Samuel Burg on 2012-08-30
Hello,

the answer is in the nfs manual :

Option for NFS version 4 : 
**clientaddr=***n.n.n.n*   Specifies a single IPv4 address (in dotted-quad form), or a  non-link-local IPv6 address, that the NFS client advertises to allow  servers to perform NFS version 4 callback requests against files on this mount point. If the  server is unable to establish callback connections to clients,  performance may degrade, or accesses to files may temporarily hang.  
If this option is not specified, the **[mount]("http://linux.die.net/man/8/mount")**(8)  command attempts to discover an appropriate callback address  automatically. [COLOR=Blue]**The automatic discovery process is not perfect**[/COLOR], however. In the presence of multiple client  network interfaces, special routing policies, or atypical network  topologies, the exact address to use for callbacks may be nontrivial to determine.


so you can :
- use static IP (or DHCP linked to your mac adress) and set the IP in the fstab
- use dynamic managment of the NFS with autofs
- use DHCP for your ethernet card, but then delay the mountall for NFS in the "init.d" scripts, so the mountall can resolv your IP adress.


best regards,

---

