---
title: "Network Manager not seeing USB Wireless device (Jaunty)"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by w2vy on 2010-07-26
I have a USB device that is known to work on Lucid.

I also had to compile the driver from the manaufacturer since it is an ARM device (i.MX51)

Now...

I have the device showing up in iwconfig when I insert it
nothing shows up in ifconfig.
(unless I manually add it to /etc/network/interfaces)

If I do add it and restart networking is tries to come up
but DHCP fails, since the wireless is not configured.

How do I get Networking to take action to bring up this device?

tom
-- 
i had the wrong driver (2870 instead of 3070)

I also switched to WICD

It would be a nice sticky topic on how NM WPA_APPLICANT and Device insertion interact

---

