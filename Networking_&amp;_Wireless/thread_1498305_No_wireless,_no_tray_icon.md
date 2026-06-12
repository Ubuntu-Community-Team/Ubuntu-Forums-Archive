---
title: "No wireless, no tray icon"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by cliffordis on 2010-05-31
Yesterday, I noticed the tray icon for network-manager disappeared, and when I booted this morning I couldn't connect to any wireless network.  I'm pretty sure I haven't made any changes that should affect this.  Previously, all hardware, drivers and connections were fine.

Ideas?

---

### Post by Jeroensum on 2010-06-01
1.) Did you get an update?
2.) Is network manager running at all?
3.) Is the hardware being detected?

1.) You should know ;-)
2.) Fire up a terminal and run: ps uax | grep -i networkmanager
    Next, run: ps uax | grep -i nm-applet
3.) In the terminal run:  ifconfig -a and/or iwconfig for cable and/or wifi and check if you see adapters like  eth0, eth1 , wlan0 ath0 , etc.  lo doesn't really count in this case as it's the local loopback adapter.


@2, if you see results for NetworkManager but not for nm-applet then NetWork manager is running but the applet has died or has not been started, try to start it with: nm-applet & from a terminal.

---

### Post by xaegis on 2010-06-01
This happened to me as well. My notification area was still there but there was no visible nm-applet, I checked and it was still running as a service just not showing up.  It seems that I had too many items booting into the notification area and it didn't resize, so the nm-applet got pushed out of the visible area/or didn't render properly. I just right clicked > Add to panel > Notification Area  (added a new notification area). and then deleted the old one and rebooted. Everything worked like a charm. or you can just resize it and reboot after you give yourself a little extra space in the notification area. Hope this helps.

:)

---

