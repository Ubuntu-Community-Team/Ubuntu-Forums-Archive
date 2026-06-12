---
title: "pass custom options to network-manager-pptp"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by vangop on 2010-07-27
Hi!
I have ~20 log entries/second in syslog 
```
nm-pptp-service-1078 log[decaps_gre:pptp_gre.c:414]: buffering packet 57467 (expecting 57429, lost or reordered)
```
after opening a vpn via network manager. I had this from CLI as well, but fixed it by adding --nobuffer option.
Can't find a way to add this option to network manager, not in the GUI, not in the configs.. Is it possible?
Thanks.

---

### Post by vangop on 2010-12-12
new release of MN has improved this, on 10.10 v0.8.1 doesn't have this problem anymore.
But still you can't pass any custom option into.

---

