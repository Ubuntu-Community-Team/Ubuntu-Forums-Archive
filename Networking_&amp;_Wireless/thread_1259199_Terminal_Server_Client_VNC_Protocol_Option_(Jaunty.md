---
title: "Terminal Server Client VNC Protocol Option (Jaunty)"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by Max Avion on 2009-09-06
Hello,

I am running Ubuntu 9.04 and when going to the Terminal Server Client (Applications > Internet > TSC) do not see the VNC option accessible from the protocol list. The only options I have are RDP and RDPv5, VNC and a couple others are greyed out. I have been searching around assuming that a package is available but have not yet been able to find anything. Could someone please help me with this, would be very much appreciated.

Thanks in advance,
Max

---

### Post by Bartender on 2009-09-07
Go to Synaptic and search for xtightvncviewer

Install

Or try this:

```
sudo apt-get install xtightvncviewer
```

That should do the same thing.

Go back to TSC and VNC should be active.

---

