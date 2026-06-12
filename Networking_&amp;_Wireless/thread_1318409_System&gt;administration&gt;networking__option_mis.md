---
title: "System&gt;administration&gt;networking  option missing"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by AceRB on 2009-11-07
**System>administration>networking [B]option missing**[/B] 			
 			 			 		   		 		 		I just did a fresh install of 9.10 and am trying to start network manager. The option isn't listed under administration although everything tells me it is currently installed.

 I am trying to start the utility to set up my wireless, got the driver installed and I am following step 1 from this guide:[https://help.ubuntu.com/community/Wi...eShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), and the option is just not there.

> Open *System > Preferences > Network Configuration* - on Ubuntu 8.04 and later this should be *System > Administration > Network*. 			 		

What am I doing wrong? How do I start it?
 
Anyone have any ideas?

thanks!

also see:

[http://ubuntuforums.org/showthread.php?t=1318341](http://ubuntuforums.org/showthread.php?t=1318341)

---

### Post by AceRB on 2009-11-07
wrong thread

---

### Post by t0mppa on 2009-11-07
Yes, network connections is the one for setting up connections for Network Manager. At least on my system, I have BSSID and MAC address lines empty and simply a SSID is there to mark the network, so you might as well try that first, since it's the simplest solution.

If you do need the info, you can grab the MAC address of your wireless card by running **ifconfig** and the BSSID on Infrastructure - i.e., the default case, where you have APs and stations, contrary to say Ad-hoc or Independent - networks is the MAC address of the AP, i.e., wireless card of your router, which you can find for instance from doing a network scan like **sudo iwlist scanning** or the connection details of any computer connected wirelessly to your router. Also a bunch of routers have their MAC address written on a label at the bottom of the device.

---

