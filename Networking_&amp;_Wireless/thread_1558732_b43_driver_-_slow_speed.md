---
title: "b43 driver - slow speed"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by morefeo on 2010-08-22
I've got a broadcom 4312(14e4:4315) and I'm using b43 drivers (broadcom STA does not work for me) but I'm getting very low perfomance, speed never reachs 2mb and disconnects sometimes, I've tried changing the bitrate with "iwconfig wlan0 rate xM" where 'x' means 2, 5 and 11 (54 makes the interface to be unstable) but it does not make downloads/uploads faster.

Any help? maybe should I test ndiswrapper?

---

### Post by o770 on 2010-09-04
Try Broadcom's proprietary the STA that should be listed in [Hardware Drivers]("http://farm4.static.flickr.com/3495/3975889024_31a9c4b9a3.jpg") along with B43. Deactivate the B43 and reboot. Activate STA, reboot. Please post result if possible.
 
Slowness, the bitrate restricted at 1Mbps is definitely an issue in the B43 with particular kernel, chipset versions or else that WL (STA) seems always to resolve.

---

