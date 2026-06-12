---
title: "NFS server wont connect on secondary interface"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by Solignis on 2010-06-28
I am not sure what the case is, but for some reason I can't connect to my NFS server on my secondary network interface. It works on my primary interface which is 10.1.1.4 but if I tell my ESXi server to connect on 10.0.0.1 which is the other half of my direct bonded link it says it can't connect the server. Is there something I am missing? I also have the exports configured to for the other network.

Can some possibly give me a clue?

--Update--

For some reason my bonded interface was configured correctly and was not coming up. Fixed the problem and NFS works now.

---

