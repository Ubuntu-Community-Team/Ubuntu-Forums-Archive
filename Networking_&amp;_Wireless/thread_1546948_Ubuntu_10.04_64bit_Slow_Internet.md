---
title: "Ubuntu 10.04 64bit Slow Internet"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by zumadale on 2010-08-06
The MTU settings should match across your network.  The default MTU of Ubuntu is 1500 ... your router or wireless router should also be set to 1500.  I have heard that 1492 MTU is optimal but 1500 works for me.

I wanted to share this ... my Internet connection slowed WAY down after first installing the 64bit version (not sure if 32bit is the same?).

I tried ALL the suggestions to disable IPV6 etc etc etc... they only worked temporarily then the Internet got slow again!

I decided to look at my router settings ... the MTU was set at 1400 ....  I decided to set it at 1500, which is the default MTU of Ubuntu.

My fast Internet is back... hopefully to stay this time!

---

### Post by zumadale on 2010-08-09
Ok... MTU settings didn't help ... but after about 24hrs troubleshooting this issue ... it was UBUNTU ONE cloud storage that was slowing the Internet down!!

What a pain finding this issue.  Once I killed Ubuntu One processes from running my Internet came right back to normal.  This was also causing lag (ping latency) on all the computers on the LAN.

Had nothing to do with IPV6 on the system, or MTU settings.  It was UBUNTU ONE uploading in the background.

Who needs 2 GIGS cloud storage anyway?  Especially at the cost of major bandwidth.  Thumb drives are a better way to go IMO.

Dale

---

