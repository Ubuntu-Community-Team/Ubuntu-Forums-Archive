---
title: "VPN routing"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Darquandier on 2009-10-06
Hello,
I would like to setup a system such as only specific ports (mainly P2P) are routed through an active VPN connection (ipsec or pptp).

Is it possible ? And if yes, is there an how-to or a guide that would help me ?
No matter how I phrase my search google and forum help only point me to other type of issues ?

---

### Post by Darquandier on 2009-10-06
So far, I'm trying this :
[http://archive.cert.uni-stuttgart.de/suse-security/2005/01/msg00008.html](http://archive.cert.uni-stuttgart.de/suse-security/2005/01/msg00008.html)

Quite old, but seems right, principle in it :
* creating alternative route table
* marking packets by ports
* routing marked packets with the alternative table that goes through the right interface (ppp0).

What do you think ?

---

### Post by Darquandier on 2009-10-07
Well my trying was a failure...
Couldn't quite figure out how to discriminate the packets, and the VPN connection was all wonky with the alternative routes...

Anyways, I'm trying to run a VM that does the job with VirtualBox (since vmware-server 2.0 is all buggy)...

---

