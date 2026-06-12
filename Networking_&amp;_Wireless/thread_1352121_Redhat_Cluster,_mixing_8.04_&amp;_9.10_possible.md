---
title: "Redhat Cluster, mixing 8.04 &amp; 9.10 possible"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Laenny on 2009-12-11
Hi,

I am currently trying to add a 9.10-Node to an existing cluster of nodes. Up to now, I am NOT successful, however.
I see that 8.04 is using cman 2.20080227-0ubuntu1.1, whereas 9.10 is using cman 3.0.2-2ubuntu1.
So far, I have not been able to figure out, if this combination should work. Sure, openais has been renamed to corosync, but corosync is running in whitetank mode, according to syslog:

```
Dec 11 14:51:35 v-server30 corosync[7016]:   [MAIN  ] Compatibility mode set to whitetank.  Using V1 and V2 of the synchronization engine.
```

This should enable communication between the nodes, shouldn't it?

Anyone who had success running such a combination? Anyone, who can verify that it will never work?

Up to now, I fail to understand the tcpdumps made, I am not quite sure where else I could look right now.

Thanks in advance,
and best regards,
Carsten

---

