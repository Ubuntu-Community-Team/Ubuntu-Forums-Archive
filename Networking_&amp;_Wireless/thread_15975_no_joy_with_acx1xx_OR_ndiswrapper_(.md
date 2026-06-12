---
title: "no joy with acx1xx OR ndiswrapper :("
date: 2005-02-18
forum: Networking &amp; Wireless
---

### Post by brainstuff on 2005-02-18
Hi

Hope someone can help!

I got halfway through this excellent guide on installling the Linux acx100 driver for my D-Link G650+ (texas instruments) chipset (the one ending :9066):
[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

..until the instructions about Kernel sources / compiling stopped making sense in relation to the Ubuntu structure - none of the files were where they should be, I couldn't even find a .config file - so I made one from the config-2.6.8-1-3-386 file and left it in a variety of different places hoping that would help!...I got a little further but the driver compile failed horribly. Major sticking point and I couldn't get any further, cos frankly I'm lost!

So, I moved on to ndiswrapper - installed it through Synaptic, no probs. Installed the driver as per instructions, no probs. Modprobe is meant to light up the link LED but it didn't...When I typed ndiswrapper -l it told me "gplus        hardware present". 

My device manager can see the card and identifies it as ACX 111...

Help me Ubu Wan, you're my only hope!


By the way, this card works fine on the Win2K partition.  

there's more...this time using the Deb install method..

$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

 ](*,)

---

### Post by brainstuff on 2005-02-18
woohoo! this post is brought to you by the power of Wi and Fi!

unfortunately I can't be entirely sure, but I would put decent money on the steps followed here:
[http://stef.tvk.rwth-aachen.de/~nazgul/debian/DWL-650+_Howto.html](http://stef.tvk.rwth-aachen.de/~nazgul/debian/DWL-650+_Howto.html)

followed by a restart is what fixed it for me.

Woohoo!


Now to buy a new battery for this old heap of junk, so I can get more than 5 minutes wirelessly online  :-P

---

