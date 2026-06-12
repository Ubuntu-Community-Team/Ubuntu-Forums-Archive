---
title: "authentication error if WiFi is configured for WPA &amp; WPA2"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by graylion on 2010-06-09
Hi guys

I am using an eeePC with Xubuntu Lucid and I just configured a wireless network to run with WPA & WPA2 (wireless access point NetGear WG103). It tries to connect and then comes back with a request for reentering the passphrase. I have had this once before in a pub. The way I read this the driver is getting confused how to authenticate.

Anybody seen this before?

---

### Post by TechnikAlsace on 2010-06-09
Saw this often. 

a) Make sure that the settings for the wireless regulatory domain are the same on the router and on your netbook.

b) Make sure that you have the latest firmware installed on the netgear router (there is an auto-check-and-update option in the control interface

c) Don't select WPA and WPA2 in the router's settings, but EITHER WPA OR WPA2

Now it should work.

---

