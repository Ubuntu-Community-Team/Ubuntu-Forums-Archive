---
title: "Using WICD on PS3"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by cdschuett on 2009-11-20
I just set up Ubuntu 9.04 on a PS3.  The install went fine, but I am trying to connect wirelessly to my home router using WPA-PSK.  The default installation put configuration settings in the /etc/network/interfaces file using auto wlan0.  This apparently caused the OS to completely bypass network manager because I could not change any settings using nm.  This connection worked fine when I switched my router to broadcast unsecured.
When I removed the auto configuration settings from the interfaces file and rebooted, network manager did not work at all whether the connection was unsecured or not.

I tried replacing nm with wicd.  When unsecured, wicd just kept recycling the interface.  When I tried switching to WPA, WICD was never able to connect.  The status message on the bottom of the console said it was trying to establish an IP address, so I think it was able to authenticate, but it never actually connected.

I am no expert with Linux, especially when it comes to network settings so I don't know where to look for clues, and most posts I have seen don't seem to match my problem so I am not too sure how to proceed.  Any help would be appreciated.

---

