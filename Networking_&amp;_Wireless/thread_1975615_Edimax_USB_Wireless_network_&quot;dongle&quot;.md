---
title: "Edimax USB Wireless network &quot;dongle&quot;"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2012-05-07
I have one of the above that works well in my son's PS3 to get fast wi-fi access near the TV. However, just hard wired that connection so the "dongle" is now spare.

I have an HP Mini netbook equipped with the ubiquitous Broadcom wireless adapter which works fine BTW. However, my BT Infinity 2 connection now exceeds the max 54 MBS connection of the Broadcom. I can just plug the Edimax in and it seems to work, but I suspect the default adapter is still in the mix somehow.

So the question is, how do I disable the built in adapter, there is NOT an option in BIOS. If a CL option is available, what would the command be to reverse the disabling!

12.04 BTW

---

### Post by kurt18947 on 2012-05-07
It may depend on which Edimax adapter you have.  I have a Edimax EW7811Un.  It looks like it's working correctly but it won't connect.  Using a default 12.04 install, it would have driven me to distraction if I had let it ;).  My fix was to download the correct driver from RealTek.  You may or may not have to blacklist the default (RTL8192CU in my case I think).  One way to disable the integral adapter would be to blacklist it as well.  I'm not familiar with Broadcom but I suspect if you run "lspci" in a terminal you'll see what Broadcom module is in use.  i have a situation similar to yours and had to blacklist an Intel driver then install the correct RealTek driver.  Happily the install script included with the RealTek driver works very well so there's no manual compiling or editing required.  Post back if you need more detailed instructions.

---

### Post by AlanR8 on 2012-05-08
Thanks for the reply and here are my findings. The Edimax WiFi "dongle" is a Realtek RTL8188CUS and I downloaded the appropriate driver.

I then created a folder in my Downloads folder called Driver

Next cd Downloads/Driver

Then sudo sh install.sh

Driver was installed and all looks good!

I then deviated from your plan and went to System Settings/Additional Drivers and disabled the Broadcom driver. Rebooted and selected the Realtek driver in Settings/Additional Drivers and rebooted again.

Wireless booted fine and got DOUBLE the throughput. Result.

BUT.......

The "dongle" is very sensitive to the WiFi signal and when I moved away from the room with the router, the signal dropped.

So back to the Broadcom unless someone can make a better suggestion. 

The Edimax/Realtek is clearly a better performer but reception seems to be an issue.

---

