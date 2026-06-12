---
title: "Firmware Upgrade Issue - Zoom 3G WiFi Router"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Magnificent 7 on 2011-05-16
Here's an interesting one:

Zoom 4501 3G Wifi Router with flaky performance with a new '3' UK mobile broadband dongle. With a previous Vodafone dongle, the same router had been quite stable, requiring only an occasional power cycle. With the '3' dongle, a ZTE MF112, the power cycles were more like every 2 to 3 days, so a firmware update was indicated....

The existing v1.0.6 firmware from Jan 2010 had been [updated twice]("http://www.zoomtel.com/techsupport/mobile_broadband/4501_firmware.shtml") by Zoomtel. Today I attempted to upload v1.0.11 from March 2011 via the router's web interface in Firefox (3.6.17). Each time the file transfer progress seemed to reach 100%, but the overall upgrade immediately failed with a reported "500: Internal Server Error".

Scouring the web and these forums, no-one else had reported any problems. Following a hunch, I booted back into Windoze on the same laptop and to my surprise could upgrade the firmware successfully, using the Windoze Firefox of the same version number.

The question is, why did the upgrade work in Windoze Firefox and not in Ubuntu Firefox? The 'upload' functionality must be a simple FTP-type transfer, unless there's something else going on 'under the hood' of these web-interface type upgrades that I'm missing.

---

