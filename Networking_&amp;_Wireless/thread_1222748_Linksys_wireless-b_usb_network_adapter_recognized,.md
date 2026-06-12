---
title: "Linksys wireless-b usb network adapter recognized, but can't authenticate"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by henriquemaia on 2009-07-25
I have a Linksys wireless-b usb network adapter (wusb11 v2.8) and I'm trying to connect to my wireless router without success. The device is recognized properly and nm-applet starts showing the available networks, but each time I try to connect to my router, it seems that it can't authenticate. What should I do to workaround this?

edit: the only authentication methods available to choose are wep. It doesn't make much sense.

[IMG]http://ecx.images-amazon.com/images/I/417T83WREYL.jpg[/IMG]

---

### Post by henriquemaia on 2009-07-25
The solution to the problem is quite simple: the wireless-b only supports wep encryption, and the router is configured to use wpa. I'm now using the wireless-g adapter and everything is working with no hassle. As soon as it's connected, the network manager immediately detects it and shows the available networks. Typed the password and I'm in.

Summarized solution: change the router configuration to use wep encryption or use the more recent version of the linksys usb adapter (wireless-g).

---

### Post by synapsys on 2009-07-25
I love it when people solve their own problems! You'll be much happier with wireless-g it's about 5x faster and more secure (wpa)

---

