---
title: "Is there any other file that stores the network configuration content besides the int"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by photonxp on 2010-10-01
For Ubuntu 10.04, I can configure the network by "Network Connections". This configuration is done by doing the following operation sequences(System->Preferences->Network Connections->wired->auto eth0). Then I can connet to and browse the internet. If I type the command "ifconfig", I can see the ip I configured for eth0. Part of the content is as blow:
> **ifconfig**
eth0
inet addr:192.168.28.31 Bcast:192.168.28.255 Mask:255.255.255.0But in the "interfaces" file, there is no eth0 content. The whole content is simply as below:
> **cat /etc/network/interfaces **
auto lo
iface lo inet loopbackI think there should be other files that keep the eth0 configuration content. What are they?

---

### Post by CedricMC on 2010-12-07
Per user conf:
~/.gconf/system/networking/connections
Per system conf:
/etc/NetworkManager/system-connections

Ref. to [this thread]("http://ubuntuforums.org/showthread.php?t=1111099").

PS: I also got crazy because of this. Not even mentioned [here]("http://live.gnome.org/NetworkManager"). Goog job Gnome!

---

