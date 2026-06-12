---
title: "jaunty+ath5k_pci+wicd=nothing?"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-05-15
this is a relatively old issue i was hoping would have more insight. in intrepid, i was able to use the native ath5k driver for the atheros chipset in my lenovo thinkpad z61e; however, the upgrade to jaunty killed that and i had to move back to the proprietary madwifi driver. even if i try to unload the ath_pci module (and all related) and load the ath5k module, i cannot view any wireless networks. all the related cli commands (ifconfig, iwconfig, etc.) give me no usable information.

any ideas of the status of this "known bug?"

---

### Post by bluestreek on 2009-05-15
Have you tried installing the jaunty backports?

---

### Post by moore.bryan on 2009-05-15
already in my sources.

---

