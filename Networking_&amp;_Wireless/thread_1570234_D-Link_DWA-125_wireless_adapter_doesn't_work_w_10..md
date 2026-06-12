---
title: "D-Link DWA-125 wireless adapter doesn't work w 10.04"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by hodad on 2010-09-07
Have tried methods from every thread I could find for past 10 hrs.  Have tried installing rt3070sta etc.    Monitored message log; appears that the driver isn't recognized, though the USB port sees that something is plugged in (when I plug in the adapter, and unplug it).

All of the threads miss something; I can't get a wireless port listed under ifconfig no matter what I try. Seems that every method leaves out something (I guess because everyone's box is different in some way).  Network manager doesn't help much.  Downloaded Wicd, which does even less.

I guess I could try ndiswrapper, but I'm scared away by the hundreds of pages I see on going that route; I'm almost certain it wouldn't work (1000 possible points of failure). Am I wrong on this?

Does anyone have a strategy to recommend?
AM64 box, newly installed Edubuntu 10.04, ran update manager.

Thanks in advance!

---

### Post by MaindotC on 2010-09-07
I realize you have already searched for what seems like a lot of pages, there is a [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  You seem to have done a lot of troubleshooting already but always consult the guide.  There's also a list of [supported/tested wireless cards](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink).  It appears that the DWA-125 hasn't been tested or verified.

If you can't get the wireless extension to appear in ifconfig then I would guess that the proper driver is not installed, or there may not be one for that wireless adapter.  Ndiswrapper is always an option and you have nothing to fear by trying it.  It may not work flawlessly, but you have nothing to lose by trying to use the windows driver with ndiswrapper.  It will not damage your system - it will either work or not work.

---

### Post by chili555 on 2010-09-07
Please do not double-post. I am answering your issue in another thread.

---

### Post by MaindotC on 2010-09-07
> **chili555 said:**
> Please do not double-post. I am answering your issue in another thread.
[img]http://images.starcraftmazter.net/4chan/animals/busted.jpg[/img]

---

