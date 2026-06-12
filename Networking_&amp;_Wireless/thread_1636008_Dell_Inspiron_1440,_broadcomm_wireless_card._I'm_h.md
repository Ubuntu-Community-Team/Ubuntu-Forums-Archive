---
title: "Dell Inspiron 1440, broadcomm wireless card. I'm having issues."
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by LunaCollins on 2010-12-02
I installed Ubuntu 10.10 onto my Inspiron 1440 about two weeks ago. I couldn't get on the internet then unless it was a wired connection. That isn't a preferable method for me, since my router is physically high up and I'm quite short for my age. But, when I would go under "Additional Drivers," it said the wireless driver was activated but not in use. Also, it wouldn't come up with any wireless networks.

So, yesterday, after installing Ubuntu 10.10 to my boyfriend's HP laptop, I established a wired connection between the two computers because I was curious. (He had internet access, mind you.) And the moment I plugged in the cable, the internet on mine started to work. I unplug the cable, and the wireless seems to work as intended. About a half hour later, I restarted to finish updating. And the internet was back to what it was like two weeks ago. I also had this problem with Mint 9, but never with Ubuntu 10.04.

Is this a problem with Dell or Broadcomm? Many thanks!

---

### Post by uncaspi on 2010-12-02
Broadcom came out in Oct with a new driver you should try. Goto to the Broadcom home page and download 

hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

unpack it and follow the instructions in the README.txt file. After make install type sudo depmod -a and then sudo modprobe wl

---

### Post by LunaCollins on 2010-12-02
...Oh. Apparently it's not a Broadcom. It says "Dell Wireless 1395 WLAN Mini-Card" in the Device Manager in Windows. Well, that would explain why the broadcom drivers may not be working right.

---

### Post by uncaspi on 2010-12-02
You can find out the driver to use by sudo lspci -nn
and look at the digits in [x.x.x.x:x.x.x.x] i.e. [14e4:4357] where the first 4 are the Vendor code, here Broadcom and the last 4 the product code.
Then to see the drivers from Broadcom supported by the kernel open a terminal and type:

grep 14e4 /lib/modules/$(uname -r)/modules.pcimap

---

