---
title: "D-Link connection problem"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by Seascribe on 2010-06-14
Nube here, looking for help connecting Ubuntu 9.10 desktop to my wireless system via D-Link DWA-125.

Have enabled networking and wireless and have indication via connection icon that wireless connection is made, but the icon is grayed out, and I cannot get firefox to connect. Seems its probably something simple, but it's quite beyond me. 

Any suggestions would be greatly appreciated.

Thanks,
Seascribe

---

### Post by grahammechanical on 2010-06-14
I am new to all this myself. So I may not be much help, but did you set the correct password? It is not the log-in password of your computer. It is the WPA-PSK password. also called WIRELESS KEY. I got confused with ll of this myself. Unbuntu is slow to reject a wrong password. It does not tell you the password is incorrect. It just asks for the password again.

Regards

---

### Post by Seascribe on 2010-06-14
Yes, thanks, I've entered the key/password ...ie the wireless password. So strange that the D-Link and wireless router seem to be talking to each other, but I can't get firefox up.

---

### Post by Iowan on 2010-06-14
Does **ifconfig -a** show an IP address for the wireless adapter? If so, see if **route -n** shows the router as a gateway. Help with terminal commands available on request. :)

---

### Post by Seascribe on 2010-06-14
> **Iowan said:**
> Does **ifconfig -a** show an IP address for the wireless adapter? If so, see if **route -n** shows the router as a gateway. Help with terminal commands available on request. :)

Yes, **ifconfig** shows an IP address. and **route -n** gives:
Destination - 10.43.43.0 and 169.254.0.0
Gateway - 0.0.0.0 and 0.0.0.0
Genmask - 255.255.255.0 and 255.255.0.0

I have no idea what any of this means:confused:
Active Network Connections
Interface 802.11 WiFi (wlan3)
Hardware Address 00:26:5A:72:A0:BC
Driver rt2800usb
Speed Unknown
Security WEP

IP Adress 10.42.43.1
Broadcast Address 10.42.43.255
Subnet Mask 255.255.255.0

Oh! and for about four seconds the grayed out connection icon turned full black, then back to gray.

---

### Post by Seascribe on 2010-06-15
This morning I discovered that D-Link has been try ing to connect my desktop computer to my neighbor's WiFi system, not mine (found out when II shut down my wireless system and the grayed out connection icon remained on my desktop).

So the problem now is D-Link is not recognizing my WiFi - an Apple system that works very well with my Acer One running Linux.

Any suggestions for connecting my D-Linked desktop to my WiFi will be greatly appreciated.

---

