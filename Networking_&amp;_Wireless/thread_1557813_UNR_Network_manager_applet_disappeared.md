---
title: "UNR Network manager applet disappeared"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by SVWander on 2010-08-21
Yesterday while trying (unsuccessfully) to get a new Bluetooth dongle set up I lost the network manager applet. When I rebooted, after giving up on Bluetooth in Ubuntu, I had no way of connecting to my wireless network. In command line (iwconfig & iwlist scan) I was able to see the wireless router. So the wireless card is working correctly. How do I reinstall the network manager applet? Oh even when use a wired connection to the router there is no connection.

---

### Post by dineshs on 2010-08-21
Right click on the top panel-click add to panel-select notification area -click add

---

### Post by SVWander on 2010-08-21
> **dineshs said:**
> Right click on the top panel-click add to panel-select notification area -click add

Well I booted back into Ubuntu and tried your suggestion. However in UNR right clicking on the panel doesn't give you the Add option.
I looked in Synatic and found that the network manager applet is not installed. Perhaps in trying to get the Bluetooth working it got uninstalled. Without the ability of going online I am not sure how to install it.
I checked in terminal and found that the network is disabled. I attached a screenshot.

---

### Post by SVWander on 2010-08-21
> **SVWander said:**
> Well I booted back into Ubuntu and tried your suggestion. However in UNR right clicking on the panel doesn't give you the Add option.
I looked in Synatic and found that the network manager applet is not installed. Perhaps in trying to get the Bluetooth working it got uninstalled. Without the ability of going online I am not sure how to install it.
I checked in terminal and found that the network is disabled. I attached a screenshot.

I was able to solve the problem of the missing network manager applet by using instructions: 
How To: Manual Network Configuration without the need for Network Manager
This is a post on this site by kevdog. 
Then once connected I was able to download the network manager applet and all is right with the world . . . at least my world. Thanks for the help.

---

