---
title: "Removing Default SSID, WICD, rt2870sta, Hardy"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by deech2k on 2009-02-19
Hi all,
I would like to remove the default SSID from RT2870STA.dat file.

I have compiled and installed the 2008_0925_RT2870_Linux_STA_v1.4.0.0. The installation instructions require that I configure the RT2870STA.dat file in /etc/Wireless/RT2870STA/ and give it a default SSID.

I am using WICD for managing my networks and the driver insists on trying to connect to the SSID in the dat file even if WICD has a different default SSID. As a consequence it takes at least a minute to connect to the desired network.

If I remove the dat file completely (or comment out the default SSID setting) this causes the card to try and connect to " " ( a null network).

Thanks for your help ...
Deech

---

