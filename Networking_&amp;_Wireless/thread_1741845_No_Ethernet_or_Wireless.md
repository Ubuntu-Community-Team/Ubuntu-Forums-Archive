---
title: "No Ethernet or Wireless"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by czerdrill on 2011-04-28
Just upgraded to 11.04, and lost my wireless and wired connections.  The network manager says "no network devices available".  Enable Networking is checked, but still no go and Ethernet is plugged in and works fine if I boot into Windows.  As does Wireless.  Any ideas?

---

### Post by dineshs on 2011-04-29
```
sudo lshw -C network
```can tell you the network hardware details,whether driver is loaded etc.Can you post the output?

---

