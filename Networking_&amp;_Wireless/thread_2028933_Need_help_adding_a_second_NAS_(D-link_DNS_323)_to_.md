---
title: "Need help adding a second NAS (D-link DNS 323) to a old network"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by SObailey on 2012-07-19
Hello out there. I'm trying to add a second NAS (D-Link DNS 323). I have multiple computers on a wired/wireless network. Its a hack job but it seems to work. 1st my satellite internet(192.168....) is piped in to my router ((D-Link DIR 625) IP address 179.168...) from here on out all IP addresses start with 179.168.... Now it splits off in to two directions. 1st line goes to my NAS (D-Link DNS 323) which is now full. The 2nd line runs to a hub (Netgear DS108. That hub connects multiple computers ( Ubuntu 5.04, 8.04.3, 11.04, 11.10 and Ubuntu 12.04). I started my network out with Samba and now I'm using smb4k( which I guess is still Samba) I've been to scared to upgrade the network. I figure as long as the gears are still turning why fix it. Anyway problem is when I turn on the second NAS (D-Link DNS 323) the first one freezes up and I have to do a complete shut down and start up of the hole system to recognize the first NAS again. When I shut the first NAS down and turn on the second NAS there's nothing there. Basically I need to format and assign a name and IP address to the second Nas but I don't have the software for the D-Link DNS 323 (which would most likely solve this problem) that I used the first time so thats one snag. I've been on the forums searching on how to add a second NAS I found a couple of threads but they were to vague to understand. The D-link web site no longer has the software and tech support is no longer capable of helping at all. Any help would be most welcomed. Thanks Sid

---

### Post by steeldriver on 2012-07-19
Well you've kind of made a rod for your own back by choosing a non-standard address range for your network - my guess is that the 2nd NAS is configured as a DHCP server and when you connect it you are getting competing DHCP assignments

If you haven't already done so you may want to reset the new NAS to factory settings - then you can temporarily configure your router (or go in via the hub from a single computer with a static IP) with the correct address range to access it and set it up as necessary (turn off DHCP server - turn on as client).

There seems to be quite a bit of documentation / support at the D-Link website:

[http://www.dlink.ca/products/?pid=509](http://www.dlink.ca/products/?pid=509)

[http://forums.dlink.com/](http://forums.dlink.com/)

You may be able to just point your browser at the default IP (which  appears to be 192.168.0.32) but if you need the D-Link search utility  software it does appear to be available for download - likely Windows only though

Hope this helps

---

### Post by SObailey on 2012-07-19
Thanks for the response Steeldriver, When I added the D-link router to  the network, D-link and Hughesnet were not playing nice together. Both  wanted to use the same IP address and neither one would take a second  seat to the other. D-link though would accept the none standard IP  address and so there you have it. Now there both #1. In fact when it  comes to tech support, they still don't play nice together and even more  so when running linux so the none standard IP address was a necessity  at the time. Well I had tried to reset the second NAS a few times but  with no luck at all, until I looked closer and found a blockage behind  the reset hole . I cleared it out and wala my router assigned a new IP  address. Now all I need to do is format and add a name. Then we're  cruisen down the happy trail again. Thanks again for your response.

---

### Post by steeldriver on 2012-07-19
Great - glad you got it sorted

---

### Post by SObailey on 2012-07-19
Formatted, named up and running .  Thanks Steeldriver. Say how do I change this to solved?

---

