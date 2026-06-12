---
title: "KNetworkManager in Kubuntu 10.04 keeps asking for WPA key on Eee PC 901."
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by jackyboy633 on 2010-05-17
I have a problem with my Eee PC 901 with Kubuntu 10.04. I have recompiled the RT2860STA module with support for WPA. However, my Eee PC connects to my wireless network for a few moments, then keeps dropping its connection. I enter the WPA key in the secrets window, but it does not accept it. It worked fine in Ubuntu, so why is it not working in Kubuntu? Any help would be appreciated. Jackyboy633.

---

### Post by Zorael on 2010-05-17
I've noticed that it sometimes interprets a failed connection attempt as a failed authentication, regardless of cause.

If you're using KNetworkManager, you could try the new network management plasmoid and see if you have better luck with that. Its package name is **plasma-widget-networkmanagement**. It should be the default in lucid, but if you upgraded you could still be using the older knetworkmanager, I guess.

Another solution (perhaps more surefire) is to use **wicd** instead.

---

### Post by jackyboy633 on 2010-05-22
It has nothing to do with the network manager. There are actually 2 kernels in Kubuntu, and it boots to the older kernel, but the driver compiles to the new kernel. I've switched to Linux Mint for the time being.

jackyboy633

---

