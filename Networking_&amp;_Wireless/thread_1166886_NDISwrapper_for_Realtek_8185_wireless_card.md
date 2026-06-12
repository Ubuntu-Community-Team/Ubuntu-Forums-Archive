---
title: "NDISwrapper for Realtek 8185 wireless card"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by cyclone5uk on 2009-05-22
I have a Realtek 8185 PCI wireless card. Under Intrepid this wasn’t natively recognised. There is a Linux driver on Realteks website, but forum users advised me to use NDISwrapper with the Windows 32 driver. 

This worked fine under Intrepid, but after upgrading to Jaunty it now takes a very long time to connect to the internet. Once I’m connected, it stays on and doesn’t drop out. However, sometimes I have to input my wireless password several times before it finally connects, and even then it takes a long time to connect.

Id like to know if the Realtek 8185 is natively supported under Jaunty and how I can remove the NDISwrapper and use the Linux driver instead.

---

### Post by cyclone5uk on 2009-05-26
Sorry, but this problem's really bugging me now - anyone got any advice?

---

### Post by t0mppa on 2009-05-26
If NDISWrapper isn't working, I suppose the native drivers are worth a try. Can't see any mentions saying it wouldn't work on Jaunty. Looks like you get a binary source, so you'll have to compile it manually and there's probably pretty good instructions in a readme or install file.

To remove NDISWrapper:[LIST=1]
[*]Run **ndiswrapper -l** on a terminal and see what driver it is using.
[*]Run **ndiswrapper -r <driver_name>** to remove the driver.
[*]Run **sudo modprobe -r ndiswrapper** to unload the module.
[*]Uninstall ndiswrapper with either apt-get or Synaptic.
[*]Clean up any blacklistings you made when installing ndiswrapper and remove **/etc/modprobe.d/ndiswrapper**.
[/LIST]

---

