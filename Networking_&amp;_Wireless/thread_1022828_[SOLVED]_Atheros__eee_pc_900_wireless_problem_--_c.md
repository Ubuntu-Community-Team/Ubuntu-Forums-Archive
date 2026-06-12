---
title: "[SOLVED] Atheros / eee pc 900 wireless problem -- can only see some wireless networks"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by johan77swe on 2008-12-27
Hello all,

I have a problem which I haven't been able to solve despite some serious googling and experimenting:

My eee pc 900 with an Atheros wireless NIC works nicely using the stock Xandros Linux -- it finds my wireless network (WPA protected) as well as a number of neighbour networks, and I can connect to it. So the hardware part seems to work nicely. 

However, after installing Ubuntu 8.10 and messing a bit with MadWifi / installing the array.org eee pc kernel I can view available wireless networks, but I **cannot find my own wireless network in the list of available networks**, and I cannot connect to it either. 

I'm thinking this may be a driver issue, possibly related to my wireless router using WPA. But shouldn't my network be visible anyway since it's broadcasting its SSID, even when using WPA? 

I'd be happy to post more info if needed. 

Help appreciated!

// Johan

---

### Post by johan77swe on 2008-12-27
I've made some progress: by using ndiswrapper as instructed here: [http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html) , my wireless network now shows up in the list. But I cannot connect to it -- likely a WPA issue. 
It's strange that I see all neighbour networks and not my own when using madwifi or the ubuntu-supplied drivers (installed with the backend package).

---

### Post by johan77swe on 2008-12-28
I finally solved this and now have working wireless connectivity. The steps were, on a high level:

1) Install the array.org eee pc kernel. At this point, I could see several wireless networks, but not my own.

2) Configured ndiswrapper with an Atheros windows xp driver as instructed under the link above. This allowed me to see my network.

3) Installed the wicd connection manager. This connection manager sets up wpa support in a nice way, which allowed me to connect easily to my wireless wpa net.

---

