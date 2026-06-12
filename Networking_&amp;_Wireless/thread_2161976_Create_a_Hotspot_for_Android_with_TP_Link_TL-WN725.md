---
title: "Create a Hotspot for Android with TP Link TL-WN725N"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Badhon_raj on 2013-07-12
Hello guys, I was trying to setup a HotSpot in ubuntu 13.04 using a TP Link TL-WN725N wireless adapter. (It's probably V1)
Since my android doesn't detect ad-hoc I was following [this Tutorial](http://ubuntuforums.org/showthread.php?t=2092934).
I got exactly [this](http://ubuntuforums.org/showthread.php?t=2092934&p=12698861#post12698861) error after trying [this](http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866)
Then I've installed [this](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107).

Now ubuntu won't even recognize the adapter! (i.e the blue LED on the device won't lit, Network manager or iwconfig won't show any wireless device)
It still works perfectly on windows though.
I've already removed those blacklist line from /etc/modprobe.d/blacklist.conf

So what do I do now to make everything work in ubuntu?
I'm trying to make ubuntu my primary OS instead of windows. So I need this badly.
Thanks everyone..

---

### Post by sbnwl on 2013-08-03
You made a mess up of Ubuntu, and kernel header and dkms packages are not required to reinstall for wireless hotspot creation.
After your ''[COLOR=#000000]TP Link TL-WN725N wireless adapter[/COLOR]' connects to internet on a fresh Ubuntu 13.04 installation, follow this guide
[http://ubuntuforums.org/showthread.php?t=2165035](http://ubuntuforums.org/showthread.php?t=2165035)
You should be okay.

---

