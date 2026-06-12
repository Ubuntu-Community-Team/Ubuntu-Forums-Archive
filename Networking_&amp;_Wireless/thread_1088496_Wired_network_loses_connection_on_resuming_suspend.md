---
title: "Wired network loses connection on resuming suspended session"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by BuggyBY on 2009-03-06
Hello,
I recently (finally) successfully installed Intrepid on my computer after buying a whole new hard drive for it and disconnecting all others. (Some of you may remember [my last attempt]("http://ubuntuforums.org/showthread.php?t=1006466") - in the end, after running what seemed to be one too many diagnostics on the hard drive in question, the partition table disappeared) Everything went smoothly this time, and all my hardware and software seems to be working as it should. Just the "suspend session" feature is giving me some trouble.

Every time I resume a previously suspended session, the wired network connection does not reconnect. (A note on hardware: I'm using the on-board Ethernet (eth0 - there's also eth1, but it's unused) on my Asus A8#N32-SLI Deluxe mainboard, connected via a 25m cat5 cable to a Pluscom BR7-WP3221 router, which in turn connects to my student accommodation's mysterious cable-based ISP via a socket in the wall.)

Though comparatively dirt cheap, the router does not appear to be the one at fault. There's (obviously, but still I checked) no change in the physical connection, and even disconnecting, waiting and reconnecting the LAN cable at the router seems to have no effect. The only way I found to restore the connection (admittedly I have not tried a lot of others) is to reboot the computer. As an aside, I can perform the session suspending and resuming trick on the MS Windows 7 beta currently dual-booting with Ubuntu on this system without any connection loss.

Since I primarily use Ubuntu for my online activities, and the PC with its rather noisy fans is just a few metres away from my bed, being unable to suspend the session without such consequences while I sleep is quite a problem. (And no, I don't think I'll be switching to water-cooling any time soon.)

My searches turned up nothing, but is this a known issue for anyone else? Besides not using the "suspend session" feature, how should I solve or work around this problem?

---

### Post by BuggyBY on 2009-03-07
Further searches seem to indicate a connection to [Bug 288281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281). Being a noob in the ways of Linux, how do I install the fix linked from that page?

---

