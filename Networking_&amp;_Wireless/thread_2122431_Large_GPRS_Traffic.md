---
title: "Large GPRS Traffic"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by konalexiou on 2013-03-05
Hello all,
I have a server that is located in CityA and I am located in CityB. This server ServerA is running ubuntu 12.04 LTS and I have a usb mobile broadband modem to connect to the internet.
In order to remotely connect to this server I also have an OpenVPN server installed at CityB and ServerA connects to the VPN server. 
I have a scheduled task running at every on ServerA at every minute in order to send the vpn ip and also know that it is alive and another scheduled task to try reconnect to vpn server if no vpn ip is available.
I have ServerA running 24/7 and normally everything is ok data traffic wise and less than 10MB/day. 
Last saturday ServerA had a traffic of 3,3GB from which Rx: 1,5GB  and Tx: 1,5GB. I monitor traffic with vnstat.

Does anybody have any idea what this traffic is and how i can get information about it?


Thank you in advance

---

### Post by konalexiou on 2013-03-05
I forgot to mention that I have disabled the automatic updates from ServerA and moreover If the traffic was an update I would expect something like Rx: 3,3 Gb Tx: 0 from the total of 3,3 GB traffic

---

