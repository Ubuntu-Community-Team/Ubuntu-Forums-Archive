---
title: "Cloned MAC address only way to get internet access. Why?"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by Rubadubdub on 2011-04-07
I have a strange problem. I have to clone my MAC address (and specify a different MAC address) to get internet. Without the new MAC address I get an IP address but no internet. :confused:

This happened with my old (updated from 7.04 -> 10.10) OS installation and with a new, clean install of 11.04.

So I have a workaround. But I don't know what the problem is.

Ps. I recently switch modem and router. And I had the problem with old and new modem/router combinations.

---

### Post by Rubadubdub on 2011-04-08
Bump.

Anybody? Anyone know why or has had similar problems?

---

### Post by dandnsmith on 2011-04-08
Could you say a bit more about what is connected to what and how?

I don't understand the need to clone a MAC - does your internet suppler have some sort of bar on your real one?

---

### Post by oldfred on 2011-04-08
Before I had a router, Comcast would see the MAC change when I switched computers and not work, I thought. Then one time I left it and after twenty minutes it did work. But I found cloning MAC it worked immediately. (My router is still seen as that old computers MAC.)

---

### Post by AlphaLexman on 2011-04-08
Your router may have MAC filters enabled, if so, you will need to log into the router via a web browser, with the proper password, and either turn MAC filtering off, or add your current MAC address.

---

### Post by Rubadubdub on 2011-04-09
This problem happened with my old router and modem and with my new router and modem. And only with my desktop computer. My laptop, also running Ubuntu there is no problem.

The situation:
When I connect my desktop computer (old and new installation & live CD) to my network I get an IP address assigned by the DHCP server of my network. But my desktop computer is not able to connect to  not have Internet. Network connection becomes very slow when searching for network shares, it fails ultimately. When I edit the LAN network connection eth1, and fill in the "cloned MAC-address" field (I hope I translated correctly from dutch). And I "off-set" the mac address by 1 (from XX:XX:XX:XX:XX:93 to XX:XX:XX:XX:XX:94) then all is well.

??? :confused: ???

thanks for the replies so far. As I said, the work-around works but I still like to find out what the problem is. Especially since this problem exists when booting from a live CD.

If you need more info, please let me know.

Robert  :)

PS. MAC filtering is NOT enabled in the router.

---

### Post by AlphaLexman on 2011-04-09
Does,
```
ifconfig | grep HWaddr
```
MAC value match the xx:93 or the xx:94 ??

EDIT: Also, what make and model is your router?

---

### Post by Rubadubdub on 2011-04-11
> **AlphaLexman said:**
> Does,
```
ifconfig | grep HWaddr
```
MAC value match the xx:93 or the xx:94 ??

EDIT: Also, what make and model is your router?

MAC address matches xx:93 (when I don't specify the cloned address xx:94)

Make Model router:
Current: D-Link DIR-652
Old: Linksys WRT54G (Tomato Firmware v1.27.1798)

---

