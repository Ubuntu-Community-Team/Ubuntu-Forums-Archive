---
title: "Ad-Hoc Wireless Network"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by singpolyma on 2010-08-24
I am trying to create an ad-hoc wireless network on Lucid and connect to it using my n900.  Eventually I hope to share my wired Internet connection over this network, but one thing at a time :)

I click nm-applet and then "Create new wireless network..." I enter the ssid and click create.  nm-applet begins flapping trying to connect to the network it just created and failing repeatedly.  Sometimes nm-applet crashes.  If I set it to DHCP, it stops flapping, but fails to connect (I am running dnsmasq with DHCP turned on on wlan0).  If I set it to a static IP, it says it is connected (but this is usually the case when a network is broken and you set a static IP).

Trying to connect from the N900, with the system in any of these states, it tries and eventually says it succeeded, but with a link-local IP.  It cannot ping the host system, nor can the host system ping it back.

Some forensics shows my wireless chipset is rtl8192.  If I can get ad-hoc, master, ap, or any other mode that will eventually let me share my Internet wirelessly, I will be very happy :)

---

