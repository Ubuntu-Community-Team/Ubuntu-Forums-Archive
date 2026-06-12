---
title: "No wireless upon returning from standby"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Muchacho_Gasolino on 2008-12-29
I posted earlier about a problem with wireless after upgrading from kubuntu 8.04 to 8.10, but I've narrowed down the problem. Apparently, it's only when returning from standby.

If I've just started up my computer, knetworkmanager will find my home network and connect fine, but if I go to standby, then come back. knetworkmanager will find the network, but will not be able to connect. It will go through most of the process but then just quit.

I had this problem with an older version of ubuntu, before 8.04. I think the upgrade to 8.04 fixed it, but now it seems to be back. Anyone seen this?

---

### Post by 67GTA on 2008-12-29
Does it use the ath_pci driver? If so, it may be related to this from the 8.10 release notes: 

```
**Wireless doesn't work after suspend with ath_pci driver**

  Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:  
 SUSPEND_MODULES=ath_pci  This will cause the module to be unloaded before suspend and reloaded on resume.  

```

---

