---
title: "ubuntu8.0.4can not recognize my &quot;Dell wireless 1395 WLan Mini-Card&quot;,"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by jokerqiang on 2009-10-15
it's even not listed in "Hardware Drivers"

what should I do, Please help:confused:

---

### Post by Metaljaz on 2009-10-16
Run this command from the terminal window:
lspci
then look for the line that resembles this:
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

If the results state that you have the broadcom chipset follow the below steps. If it states something different please post the results of the network controller information.

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. (this will extract the broadcom 43xx firmware) Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

