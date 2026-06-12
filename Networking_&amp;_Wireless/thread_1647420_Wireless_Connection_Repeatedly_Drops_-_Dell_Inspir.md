---
title: "Wireless Connection Repeatedly Drops - Dell Inspiron 500m w / 10.10"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by TheHardestWayPossible on 2010-12-17
Last night was my entree into Linux. I am a complete noob. I decided to install 10.10 desktop onto an aging Dell Inspiron 500m w/ 1.3 GHz Pentium Centrino. Router is Linksys Wireless g. 
 
10.10 runs, but I can't seem to maintain the wireless connection. I see from the other postings that this is not an uncommon problem, but I'm not sure I recognize any solutions (or any solutions that are appropriate to my situation/configuration).
 
My primary reasons for trying Linux are:
 
1. I thought learning Linux would be interesting and be a good way to get additional life out of the old laptop.
2. Turn the laptop into a fast net surfer.
3. Because I like to do everything the hard way (it would have been easier to leave windows XP running!)
 
Perhaps another distro would be more appropriate?
 
UPDATE: This is an update - I am now not convinced I ever established an internet connection via wireless (only by hard-wire ethernet). I am able to see wireless networks, and I am able to create a wireless connection to my hidden linksys router, when editing the account, I see "never" in the column indicating "Last Used". Still, it gives the impression that it is connecting, then disconnecting (red exclamation point, balloon message).
 
UPDATE: I have finally established a connection with my router and connected to the internet. I found these pages enlightening:
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/)
 
I had noticed that my config/driver was using Channel 1, though my router was on Channel 9. iwconfig would not allow me to change the driver setting ("Error for wireless request 'Set Frequency' (8B04) : SET failed on device eth1 ; Operation not supported."). So, just for grins, I decided to make my SSID visible just to see if my router showed up among the other neighborhood routers that are broadcasting their SSIDs. The router immediately connected! And, the config/driver was switched to Channel 9 to match my router. So, it seems like hiding the SSID may be contributing to the problem. 
 
I re-booted a couple times, and the connection promptly re-established. But, after disabling the broadcast of the SSID, again, and rebooting, the computer could not find the router, again, and this time, the config was set to Channel 0(?)! 
 
I don't like broadcasting my SSID - is there a fix for this glitch?

---

### Post by TheHardestWayPossible on 2010-12-21
Hi-
 
I've moved this discussion over to the "Absolute Beginners" forum since I received no input here.  And, in working through things, I've learned that I can connect with "Network Manager" when the SSID is hidden, but not secured, or when the SSID is secured and visible.   But, I still can't connect when the network is both secured and hidden.
 
I'm still exporing solutions before moving away from "Network Manager" (to wicd or another network manager).
 
Thanks!

---

