---
title: "Can see wireless networks on my Dell laptop but can't connect"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by epsom6 on 2009-11-12
I know there are lots of posts around wireless but this seems to be a slightly different issue so please bear with me.

I've never been able to get the wireless on my Dell D400 with a Broadcom Corporation BCM4309 802.11a/b/g (rev 02) work with older versions of Ubuntu. I installed 9.10 and enabled the B43legacy driver under "Hardware Drivers". 

I am able to view all the available wireless networks if I click on the network icon. 

HOWEVER - I am unable to actually connect to any of them. If I try to enter in the wireless password (WPA/WPA2) when it asks, the icon just spins and ultimately doesn't connect. I've tried this with both secure and unsecured networks and it won't connect.

I've checked a log and the below is what I'm seeing - in my uneducated view it's having trouble authenticating (yes, the password is correct - I've got another IBM laptop running 9.10 working without any problems).

Any help would be MUCH appreciated - I have never been able to get wireless working on this Dell laptop and I really don't want to go back to MS.


ct 30 08:50:24 dell-d400 wpa_supplicant[932]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 30 08:50:24 dell-d400 kernel: [  323.824040] wlan0: direct probe to AP 00:22:3f:43:cc:b0 timed out
Oct 30 08:50:29 dell-d400 wpa_supplicant[932]: Authentication with 00:00:00:00:00:00 timed out.
Oct 30 08:50:30 dell-d400 wpa_supplicant[932]: CTRL-EVENT-SCAN-RESULTS 
Oct 30 08:50:30 dell-d400 wpa_supplicant[932]: WPS-AP-AVAILABLE 
Oct 30 08:50:30 dell-d400 wpa_supplicant[932]: Trying to associate with 00:22:3f:43:cc:b0 (SSID='SKY25405' freq=2412 MHz)
Oct 30 08:50:30 dell-d400 wpa_supplicant[932]: Association request to the driver failed
Oct 30 08:50:30 dell-d400 kernel: [  329.644691] wlan0: direct probe to AP 00:22:3f:43:cc:b0 try 1
Oct 30 08:50:30 dell-d400 kernel: [  329.844109] wlan0: direct probe to AP 00:22:3f:43:cc:b0 try 2
Oct 30 08:50:31 dell-d400 kernel: [  330.044082] wlan0: direct probe to AP 00:22:3f:43:cc:b0 try 3
Oct 30 08:50:31 dell-d400 wpa_supplicant[932]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 30 08:50:31 dell-d400 kernel: [  330.245310] wlan0: direct probe to AP 00:22:3f:43:cc:b0 timed out
Oct 30 08:50:35 dell-d400 wpa_supplicant[932]: Authentication with 00:00:00:00:00:00 timed out.
Oct 30 08:50:37 dell-d400 wpa_supplicant[932]: CTRL-EVENT-SCAN-RESULTS 
Oct 30 08:50:37 dell-d400 wpa_supplicant[932]: WPS-AP-AVAILABLE 
Oct 30 08:50:37 dell-d400 wpa_supplicant[932]: Trying to associate with 00:22:3f:43:cc:b0 (SSID='SKY25405' freq=2412 MHz)
Oct 30 08:50:37 dell-d400 wpa_supplicant[932]: Association request to the driver failed
Oct 30 08:50:37 dell-d400 kernel: [  336.048098] wlan0: direct probe to AP 00:22:3f:43:cc:b0 try 1
Oct 30 08:50:37 dell-d400 kernel: [  336.248069] wlan0: direct probe to AP 00:22:3f:43:cc:b0 try 2
Oct 30 08:50:37 dell-d400 kernel: [  336.448075] wlan0: direct probe to AP 00:22:3f:43:cc:b0 try 3
Oct 30 08:50:37 dell-d400 wpa_supplicant[932]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

---

### Post by ratbone on 2009-11-17
I'm no guru, but this thread looks similar.
[http://ubuntuforums.org/showthread.php?p=8332889#post8332889](http://ubuntuforums.org/showthread.php?p=8332889#post8332889)

I found wicd to fix my issues.

---

### Post by epsom6 on 2009-11-17
thanks...unfortunately wicd didn't help - but I've switched to that thread now. Cheers

---

