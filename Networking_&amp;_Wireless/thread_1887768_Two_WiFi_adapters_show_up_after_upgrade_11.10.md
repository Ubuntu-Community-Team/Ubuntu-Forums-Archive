---
title: "Two WiFi adapters show up after upgrade 11.10"
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by derekcentrico on 2011-11-27
Recently, I upgraded my desktop to Ubuntu 11.10 from 11.04.  I have a US Robotics WiFi-G router which has a broadcom chipset.  This has required me to do some extra steps to get the Windows driver loaded into Linux.  Further, I have a cheap USB WiFi N adapter that has no Linux support.

Anyway, now I magically two different WiFi cards showing up.  The cheap USB one is not listed, though.  What's more, the one "non-existent
 one will show as CONNECTED when the real one is.  But, I have to "disconnect" from it before my WiFi will work.

The real one is labeled "Broadcom BCM4318 [AirForce One 54G]".  The non-existent one is labeled "Realtek 802.11n WLAN Adapter."

I removed both WiFi adapters to test if either would work.  The USB one did not work and no adapter showed up when it was alone.  The Broadcom adapter showed up with the Wifi-N adapter still listed when it was in the PC alone.  

This leads me to believe the USB one is definitely not seen by Linux, and that the Broadcom is being seen as two devices without the ability to properly operate out-of-the-gate.

Any help would be appreciated on how to get rid of this dual adapter listing so that I don't have to go through this disconnect from the non-existent driver before my network connection will work.

Thanks.

---

