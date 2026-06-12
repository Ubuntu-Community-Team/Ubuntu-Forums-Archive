---
title: "Ubuntu networking (vs. debian)"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by EndianX on 2009-01-08
In debian, network interfaces are detailed in /etc/network/interfaces.  This used to be the case in Ubuntu.  However, I now have three network interfaces that are not listed there.  Where are they described?  Are they just auto detected and configured at boot?

Any information on this would be greatly appreciated.

Thank you,

Dave

---

### Post by albinootje on 2009-01-08
> **EndianX said:**
> In debian, network interfaces are detailed in /etc/network/interfaces.  This used to be the case in Ubuntu.  However, I now have three network interfaces that are not listed there.  Where are they described?  Are they just auto detected and configured at boot?

Yes. 
If you're using the Ubuntu desktop now, then by default Network Manager is handling the network configuration.

---

### Post by kevdog on 2009-01-08
Interfaces not listed in the interfaces file are taken control of by network manager.  Im not sure if network manager is contained natively in the debian distribution.  The /etc/network/interfaces file is the configuration file for the ifup/ifdown commands and the interfaces are appropriately configured as such when running these commands.

---

