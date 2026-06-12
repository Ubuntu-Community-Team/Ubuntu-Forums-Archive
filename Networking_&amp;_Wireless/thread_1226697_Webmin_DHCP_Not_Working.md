---
title: "Webmin DHCP Not Working"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by DakabinSHS on 2009-07-29
Hi all, can you guys please help us with the following Webmin problem? 
 
We have installed 9.04 sever edition of ubuntu and we have installed GUI interface on it. We then downloaded webmin and set-up everything apart from NFS.
 
All things running smooth until we try to connect other ubuntu desktop edition computers through our ethernet switch using Auto Eth0, with the settings set to DHCP. At which part the machines just keep saying Wired Network- Disconnected you are now ofline. What the hell. 
 
Any and all help will be appreciated.

---

### Post by dmizer on 2009-07-29
Several issues here.

While Webmin really seems to be a sweet tool, it was dropped from the Ubuntu packaging around Breezy because it was (and still is) incompatible with how Ubuntu handles config files.

More information here: [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)
And here: [https://answers.edge.launchpad.net/ubuntu/+question/2873](https://answers.edge.launchpad.net/ubuntu/+question/2873)

Also, if you need a GUI, then you should install a full GUI version of Ubuntu rather than the server version as the server kernel is tuned for use without a GUI, and may cause problems once X is installed.

In this case, your major issue is probably related to the fact that you've tried to configure networking both via Webmin and via network-manager. I suggest uninstalling network-manager. I also suggest exploring an alternative to Webmin: [https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)

---

