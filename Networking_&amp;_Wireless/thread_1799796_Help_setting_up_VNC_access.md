---
title: "Help setting up VNC access"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Rikeshar on 2011-07-08
Hello everyone. I've recently reinstalled Ubuntu and I'm having trouble remembering how I allowed VNC access before. Everything is set up properly in Remote Desktop and the route, it's the settings in the Network Connections that I can't remember. 

This is what I sort of remember doing:

I go to Network Connections, Wired tab, click Auto eth0 and edit.

From there I go to the IPv4 Settings tab, change my method to manual. In the Addresses field I put in the IP, Netmask, and Gateway found in my router. Down in DNS servers I put the DNS server found in my router.


From here I'm lost though. It's still not letting me connect through VNC or SSH (yes, I have openssh-server) and I'm not sure what I"m missing. Any ideas?

*Edit* I've also put the previous information under my wireless tab too, still with no change. It was originally under the wireless tab, since that's how I connected before I hardwired it to the network.

---

### Post by Rikeshar on 2011-07-08
Anyone?

SOLVE: I was putting the router  IP, when I should have been putting the static computer IP.

---

