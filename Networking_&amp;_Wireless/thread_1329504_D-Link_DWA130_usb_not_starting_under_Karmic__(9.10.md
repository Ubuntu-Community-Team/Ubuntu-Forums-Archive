---
title: "D-Link DWA130 usb not starting under Karmic  (9.10)"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by dunkelgrun on 2009-11-17
We had the DWA-130 usb network connector working under Jaunty (9.04), but when we upgraded to Karmic (9.10 - with Network Manager), the connection was broken.              (uname -mr:  2.6.31-14-generic i686)
 
I added Ndiswrapper to the startup programs so the drivers are there.  However, it appears that the system does not automatically start the driver on a cold reboot.   'lshw' indicates the wlan1 interface is 'disabled'.  

If I open the wireless connection under Network Manager and edit/save the data (but without making a real change), when I shutdown and then start again, the drivers are loaded and activated and the system connects to the router.  

I have not tried directing Ndiswrapper to the port in the startup because the help includes a warning.

---

### Post by bkratz on 2009-11-17
> **dunkelgrun said:**
> We had the DWA-130 usb network connector working under Jaunty (9.04), but when we upgraded to Karmic (9.10 - with Network Manager), the connection was broken.              (uname -mr:  2.6.31-14-generic i686)
 
I added Ndiswrapper to the startup programs so the drivers are there.  However, it appears that the system does not automatically start the driver on a cold reboot.   'lshw' indicates the wlan1 interface is 'disabled'.  

If I open the wireless connection under Network Manager and edit/save the data (but without making a real change), when I shutdown and then start again, the drivers are loaded and activated and the system connects to the router.  

I have not tried directing Ndiswrapper to the port in the startup because the help includes a warning.



Please see my discussions above in the "stickies".  So you actually got it to connect at some point? Were you using any encryption on the router?  As you can see I haven't had much luck at all.   What warning are you referring too?

---

### Post by dunkelgrun on 2009-11-17
Yes, it does connect, but only after the twiddling.  It also does not update the 'last connected' note in the connection data window.   Yes, there is encryption on the router, but the problem is that the system does not activate the send/receive unit (There is no light showing on the unit).  

When I did "ndiswrapper -h", the output indicated that there was an option to specify a port which concluded with a comment '(dangerous)'.  That's the warning.

---

