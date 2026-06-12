---
title: "Change default network connection?"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by zia.newversion on 2012-03-05
Hi there...

I have two internet connections. One is a mobile broadband (EVDO/CDMA) connection using a USB-dongle modem. The other one is a public WiFi.

The problem is, the mobile broadband, although higher bandwidth, is unreliable. There are problems with the hardware (modem) issued by provider. The connection often disconnects. I need a consistently continuous connectivity for some reason and while I'm trying to find a solution for this problem, I'm making use of the WiFi which is reliable as it usually doesn't disconnect from the ISP. However, the bandwidth of the WiFi router is quite low.

The network manager in Ubuntu has automatically chosen the WiFi to be its default connection and although both connections are active, the applications use WiFi connection when it's available (which is always, unless I intentionally disconnect). 

I would like to choose the mobile broadband (ppp0) to be my default connection so that the applications use mobile broadband whenever it is available and use the WiFi only when mobile broadband connection is not available.

However, after a lot of internet search, I am still unable to find a way to manually select the default connection as ppp0 instead of wlan0. Could someone help me out please?

---

### Post by abdulcanbaz on 2012-03-07
I'm quite a novice on Linux but I had the same problem. I have my printer connected to my wireless router but it's got no internet, you alike I was using mobile phone to connect internet. Anyway when I connect wireless I couldn't browse internet. I use Ubuntu 11.10. Here's how it resolved:

Go to network manager(network connections, at the end of connections list on the task bar). Select wireless tab, select the network and click edit on IPv4 tab, you'll see routes below. Click on it and you'll see the option "use this connection only for resourses on its network" check it and click OK and save. Now both my printer and mobile connection works fine.

---

