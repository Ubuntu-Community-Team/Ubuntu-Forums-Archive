---
title: "Dell TrueMobile 1400 WLAN issues"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by sam_19113 on 2009-10-07
I recently converted my DELL Inspiron 8600 from Windows (XP) to Ubuntu (jaunty jackalope). Installation was straight forward and ubuntu found drivers for the wired ethernet just fine. The Dell TrueMobile 1400 WLAN card, however, required some additional downloads and hardware activation. The "Hardware Drivers" utility listed "Broadcom B43 Legacy" as the device. The wireless connects just fine but web page loads sometimes freeze, browsing seems very slow and port access does not seem to work for bittorrent. 

Has anyone experienced anything similar? Does anyone know what might be the cause or how to isolate/fix it?

---

### Post by opt1k on 2009-11-25
The broadcom drivers for linux have really "SUCKED" for a long time.

You should install ndiswrapper and use the windows drivers. You will get better range and stability.

sudo apt-get install ndisgtk


and read [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

