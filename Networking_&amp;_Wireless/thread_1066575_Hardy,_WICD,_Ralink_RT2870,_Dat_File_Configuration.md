---
title: "Hardy, WICD, Ralink RT2870, Dat File Configuration"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by deech2k on 2009-02-11
Hi all,
My RT2870 USB wireless card works well, but always wants to connect to the SSID given in /etc/Wireless/RT2870TSTA/Rt2870STA.dat file first. The RT2870.dat file is used to configure the driver. One of the values that can be configured is SSID. But I don't want to set an SSID here because I would like WICD to detect and connect to a network based on location.

Even if I remove the SSID line, it tries to connect to nothing for about ten seconds before it lets WICD take over and do the right thing.

Has anyone run into this before?
-deech

---

