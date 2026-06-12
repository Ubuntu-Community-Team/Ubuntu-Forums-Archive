---
title: "Connect Printer to wireless LAN without WPS"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by Feathers McGraw on 2013-08-23
Hi,

I'm having trouble connecting my HP Deskjet 3050a printer to my LAN.

The printer menu only has an option for WPS (either push button or pin), but DD-WRT doesn't support WPS.

I can print when I'm using a printer data cable, but can't find a way to change the settings on the printer so it will connect to the router via WiFi.

Any suggestions?

Feathers

---

### Post by Feathers McGraw on 2013-08-23
I figured out how to enable USB printing on a DD-WRT router, and have written it up [here]("http://www.samhobbs.co.uk/2013/08/connect-a-printer-to-dd-wrt-via-usb"), in case anyone else has the same problem.

I did try connecting to a different router (WiFi hotspot), then visiting the printer admin page in a web browser. This should have enabled me to manually add the SSID and passphrase for the actual router, but the printer wasn't having any of it. I got an error saying that MAC address filtering might be enabled and was preventing connection (it isn't).

Feathers

---

