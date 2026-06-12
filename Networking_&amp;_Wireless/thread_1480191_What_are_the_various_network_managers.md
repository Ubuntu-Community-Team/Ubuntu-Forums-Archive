---
title: "What are the various network managers?"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by jebradley on 2010-05-11
What are the various network managers that can be present on Ubuntu? I have been having problems with network connections on my laptop, and it seems that I have more than one manager that is conflicting with the other. I can make settings for both wired and wireless connections using nm-connection-manager, yet using the applet NetworkManager to make a connection ends up with different settings. i.e. I had set a fixed IP address with nm-connection-manager, yet NetworkManager made a connection that had a different address. When I went back to NetworkManager, the settings had been changed to make an automatic connection with DHCP. I did have wicd installed at one point, but deleted it with synaptic using the "complete removal" setting.

I want to be able to go to one location to setup the connections, and have those settings remain.

Thanks.

---

### Post by 2hot6ft2 on 2010-05-11
You should only be using the Network Manager Applet. There are other tools but that's where you setup your connections.

---

### Post by jebradley on 2010-05-11
Actually, I think that the problem has been that the changes that I've made haven't been saved, so it seemed like there was more than one program controlling the settings. 

As for only running the NetworkManager applet, it calls up nm-connection-editor if you go to make any changes, so the two are linked.

---

