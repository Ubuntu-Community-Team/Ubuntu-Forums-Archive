---
title: "Wifi drops randomly"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by bendeguz on 2010-11-24
My Wifi connection drops randonly on Ubuntu 10.10. I uninstalled Network Manager and use wicd with wpa_supplicant. The hardware is an IBM Thinkpad T60p laptop with an Intel 3945 wireless adapter. The wireless works flawlessly on Windows on the same laptop, both at work and at home but it's absolute crap on Linux. I can leave the laptop running XP over night on wireless and I can be 100% sure that it's still connected in the morning (my VPN to work stays connected). On Linux I can't be sure my wireless will be on in 5 minutes.

When my wireless on Ubuntu drops it cannot be restarted, I have to reboot the box.

Wpa_supplicant.log about the crash:
------------------------------------------------------
CTRL-EVENT-TERMINATING - signal 2 received
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Wicd.log about the crash:
--------------------------------------
2010/11/24 19:16:06 :: Autoconnecting...
2010/11/24 19:16:06 :: No wired connection present, attempting to autoconnect to wireless network
2010/11/24 19:16:08 :: Unable to autoconnect, you'll have to manually connect
2010/11/24 19:16:09 :: Autoconnecting...
2010/11/24 19:16:09 :: No wired connection present, attempting to autoconnect to wireless network

So on....

After rebooting it works again.

My home wireless uses wpa2 with AES encryption.

Thanks.

---

