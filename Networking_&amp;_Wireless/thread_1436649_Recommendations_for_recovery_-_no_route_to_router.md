---
title: "Recommendations for recovery - no route to router"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by buchs on 2010-03-22
Now I've done it!  I messed up my Karmic install on my laptop trying to get wireless networking connection to behave better.  I'm not really sure what I did, but the problem I have is that, though it connects to my wireless network, it does not get a route to it.  Any attempt to reach the router with a ping yields a destination unreachable.  Trying to fix it in true hack fashion, I tried messing around with the static routes.  I added an explicit route for my router  (route add 192.168.0.1 wlan0) with no avail.  I ensured there was a default route to the router which is a gateway outside of my LAN (route add default wlan0 gw 192.168.0.1).  I have another route to my LAN network with a gateway of "*".  I've done all this but the results are the same.

So, I'm interested in recommendations to fix this.  Is there some networking setup/install procedure I can rerun?  Or is it best to go back and reinstall Karmic?  Are there other places that you might suggest I look to in order to fix this?

Thanks much!

---

### Post by buchs on 2010-04-16
> **buchs said:**
> Now I've done it!  I messed up my Karmic install on my laptop trying to get wireless networking connection to behave better...

My resolution to this was to stop using a static IP address.  It seems that things just will not work correctly if I specify a connection with a static IP address in Network Manager.  I cannot determine why this is the case.  I did also have my router set up to supply a static IP address.  It should have worked, but it didn't.

---

### Post by aeiah on 2010-04-16
home routers are funny things. this one here accepts a static ip for my bridge but not for any client, for instance. its best with home routers to use DHCP whenever possible, especially on wireless where you may be connecting to several access points all with different subnets

---

### Post by terazen on 2010-04-16
Try going back to dhcp using NetworkManager or whatever gui you have.  Then setup your wireless router's dhcp server so it gives the MAC address of your laptop the same ip address every time.  This way when you take your laptop somewhere else you will already have dhcp configured and won't have to change your wireless settings over and over.

---

