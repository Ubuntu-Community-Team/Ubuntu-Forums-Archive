---
title: "Connect automatically to hidden network"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by bill_p on 2009-12-17
On Koala with a RealTek 8192, I'm trying to connect automatically to my WPA wireless network without broadcasting the SSID. I went down the Gnome NM road and could get a connection manually with many steps to make it work, most of the time. 

With wicd I can always connect by letting it scan, fail to connect (or cancel), then when it shows all the available networks, I see my hidden network, put in my SSID  (Network > Find a hidden network), press connect and life is good. But when I reboot it tries to connect to "none" and does not remember the SSID I previously put in.  I added the SSID to the /etc/wicd/wireless-settings.conf to no avail.

Is there a way to get wicd to remember the SSID? Or is there a better way to get an automatic connection?

---

### Post by bill_p on 2009-12-24
Okay, it looks like I fixed this by using [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

I am set up with hidden SSID and WPA1, using wpa_supplicant and editing /etc/network/interface. 

One other issue that came up in the meantime was trouble reconnecting after sleep/hibernate.  I can now reconnect reliably by either restarting networking from a terminal or bounce the interface with ifup/ifdown.

I highly recommend the post I linked to, just took me a while to find it.

---

