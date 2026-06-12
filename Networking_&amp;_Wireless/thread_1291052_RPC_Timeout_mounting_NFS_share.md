---
title: "RPC Timeout mounting NFS share"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by Illustrious on 2009-10-14
Setup: wired network with three machines. Server Crystalis is running Ubuntu 9.04 and has four NFS shares defined in /etc/exports. 

Client "Fabrosi" is a mac mini running OS X. It is able to mount the NFS shares no problem.

Client "Zeromus" is a laptop running a fresh install of Karmic, with portmapper and nfs-common installed via apt-get.

When I issue the command "mount crystalis:/media/highfive" (where highfive is one of the shares) it hangs for a bit, then returns a timeout message. Perusal of the logs shows an RPC timeout error. 

Anyone else dealt with this?

---

### Post by Illustrious on 2009-10-19
Really? Nobody's seen this? Both Ubuntu machines are nearly bone-stock! For crying out loud...

---

### Post by TyTiger on 2009-11-06
Try the IP address instead of the NetBios name or try using the netbios name including its qualified work group/domain name. It coudl just be having difficulty resolving the host name to an IP address.

---

