---
title: "Wireless problem in Karmic - ASUS p5q3 Deluxe Wifi@n"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by berman56 on 2009-10-31
Wireless works in 9.04.  Following upgrade to Karmic, network manager sees the router but won't connect.  The wheel spins and eventually times out.  Any thoughts on the first/next step in troubleshooting?  

Help greatly appreciated!!!

---

### Post by berman56 on 2009-11-02
I managed to find a solution in this thread:

[http://ubuntuforums.org/showthread.php?t=916845](http://ubuntuforums.org/showthread.php?t=916845)

In particular, I followed the instructions from glittalogik in the following way:

1. Download the RT2870USB(RT2870/RT2770) wireless driver from the ralinktech website.  The link in the previous post doesn't work anymore.  You can find the driver in the support section:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

2. tar xjf 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2

3. cd to the directory 2009_0820_RT2870_Linux_STA_V2.2.0.0

3. gedit /os/linux/config.mk and set both HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to y.

4. make

5. cp os/linux/rt2870sta.ko to /lib/modules/currentlinuxkernelversion/kernel/net/wireless .

6. gedit /etc/modules and add a line rt2870sta

7. depmod

8. Restart

That did it for me.  Interestingly, before I tried the above, I installed WICD.  I had the same exact problem in WICD as with network manager.  Again, 9.04 ran fine without any alterations.  Hopefully, a future update will take care of this issue with the p5q3 deluxe wifi@n motherboards.  Cheers.

---

### Post by Azzir on 2010-08-30
Just in case anyone like myself tried this and it failed to work, after following these steps I re-installed the WPA Supplicant from the Synaptic Package Manager, followed by a reboot...

...and now I'm typing to you from my 10.04 Ubuntu install hooked up wirelessly to my WPA access point :-)

---

### Post by PSBTornado on 2011-03-07
I'm going to be putting Maverick on my PC later in the week. Has this issue been addressed for an easier fix or will I also be following the above steps?

---

