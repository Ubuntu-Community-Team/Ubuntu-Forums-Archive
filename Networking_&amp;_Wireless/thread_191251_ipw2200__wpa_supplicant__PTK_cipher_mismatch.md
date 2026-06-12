---
title: "ipw2200 / wpa_supplicant / PTK cipher mismatch"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by xcyborg on 2006-06-07
I just upgraded my laptop from Ubuntu Breezy to Ubuntu Dapper and noticed that I cannot use the wireless network anymore. Before upgrading, I used wpa_supplicant to authenticate (LEAP), but now I cannot connect anymore. Of course, I tried exactly the same configuration file, but since it didn't work, I began "tuning" parameters... unfortunately without success.

Things that got upgraded are:

- the kernel - from v2.6.12 to v2.6.15
- the ipw2200 driver - from v1.1.0 (manually compiled) - to v1.1.1
- wpa_supplicant - from v0.4.5 to v0.4.8

One major thing that changed and needed adjustment in my conf file was the transition from "ipw" to "wext". After studying the debug output I see that even though the SSID matches, all access points are ignored with a message "skip WPA IE - PTK cipher mismatch".

I attached the full output 
of "wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -Dwext -t -ddd". 

What am I missing here ?

---

