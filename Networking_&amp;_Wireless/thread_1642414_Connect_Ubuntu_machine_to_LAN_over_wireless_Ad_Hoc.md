---
title: "Connect Ubuntu machine to LAN over wireless Ad Hoc"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by Garciat on 2010-12-10
I've googled for a possible fix for this issue that just presented to me, but couldn't find anything. I just thought I'd share my fix with the community.

Hardware: hard-wired Windows 7 machine with wireless adapter; Ubuntu 10.10 box with wireless adapter

Solution: It's quite simple, actually. Follow these steps:

[Win7] Go to Control Panel > Network and Sharing Center
[Win7] On the left sidebar, click 'Manage wireless networks' and then 'Add'
[Win7] Select 'Create an ad hoc network', type in a network name, select your favorite security type (I used WEP), click 'Save this network' (it's useful), finally click 'Next'
[Win7] Go back to Network and Sharing Center and click 'Change adapter settings', here you must select both your Wireless and Local connections (using Ctrl key and clicking both) and then right click one of them and choose 'Create network bridge'
[Ubun] Now, simply select the SSID of the network you created from the NetworkManager applet and connect to it using your security password

This fix may not be detailed enough for some people, so I encourage anyone who -did- understand it to explain it to those who didn't, as I probably won't be checking on this thread very often.

---

