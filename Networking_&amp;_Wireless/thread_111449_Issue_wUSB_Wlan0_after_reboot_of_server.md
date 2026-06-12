---
title: "Issue w/USB Wlan0 after reboot of server"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by muppetmaster on 2006-01-02
I have successfully installed the libraries from here:

[http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/)

For my Zyxel USB Zyair B-220 wireless device.  I configured via the standard GUI in Breezy in Sysem -> Network -> Wireless Connection/Wlan0.  All works fine with a static IP address after configuring for WEP with the WEP key via the GUI.

But, when I reboot, while the GUI says it is active and fine but I am unable to access the network.  The only way I may do this is by doing the following command:

sudo iwconfig wlan0 enc my_wep_key

Once I do this, all is fine again.  Anyway to make this happen automagically via the GUI or elsewhere on bootup?  As of course the NTP check is failing as the network is down to begin with.

---

