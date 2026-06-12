---
title: "Possible wireless headache remedy."
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by Scott Baker on 2011-12-07
I'm posting this in the hope that it solves as many headaches for everyone else, as it has for me. I see a HUGE number of complaints with regards to wireless issues. I've had some of these issues myself, and found a solution that's worked for me almost always. First, make sure that you have the MOST CURRENT version BIOS installed on your machine. This in itself makes a HUGE difference overall. Next, you'll need to get your hands on the following; The D-Link wireless N Pico USB adaptor ( U.S. part # DWA-121. ) I've picked up several of these for about $12.00, U.S. each. You install these like you would any other wireless card ( info can be found throughout these forums. ) Blacklist the drivers for the current card, then you can install  this device with NDIS wrapper, and ACTUAL honest to goodness UBUNTU LINUX drivers available directly through the D-Link website (support.dlink.com). I've installed these on several laptops, and the results were fantastic. Relatively fast set-up, better wireless connectivity, way better range, and lower power consumption ( as far as I can tell. ) I hope this this helps others as much as it's helped me and my clients. ( BTW, this has been tried with 10.04, 10.10, 11.04, and 11.10 )
Dr. Sheldon Cooper for U.S. president, 2012 =D>

---

### Post by skud78 on 2012-08-02
Following the above steps for my D-Link N150 DWA-121 adapter:

1.  Added to /etc/modprobe.d/blacklist 
      blacklist rtl8192cu
      blacklist rtl8192c_common

2.  Installed NDISwrapper 

3.  The ndiswrapper needs an .inf file to install a driver, as its meant to use windows drivers on the linux system.  I tried installing the linux driver file (from Dlink website) with ndiswrapper as suggested above and it gives me an error asking for a .inf file.  As a flyer tried renaming to .inf file and installing - comes up with error and lists as invalid driver.

4.  installed .inf file with NDISwrapper - (downloaded .inf from Dlink website), tried using the Win7x86, Win764, and WinXPx86 and Winx64.  

5. Win7 versions install successfully, but system doesn't pickup a wlan0 device on bootup.  WinXP versions cause major problems on the system which doesnt boot up.   

Would be extremely grateful if someone can point out my mistake or find  another solution that works

---

### Post by bakegoodz on 2012-08-03
I think that is bad advice to buy an adapter that needs NDIS wrapper or another download to make it work. NDIS wrapper is often unstable (very unstable in my experience) And with another party download you may have to redo the install for every kernel update or be without support when you upgrade to a new Ubuntu version.
 What I recommend is buying an adapter that has a chipset with good support in the generic Linux kernel. I recommend Intel Brand and Brands with Atheros chipsets. [http://www.wikidevi.com/w/index.php?title=Special:BrowseData&_cat=Wireless_adapter&Chip1_brand=Atheros&limit=500&offset=0](http://www.wikidevi.com/w/index.php?title=Special:BrowseData&_cat=Wireless_adapter&Chip1_brand=Atheros&limit=500&offset=0) (page down past the divider)
And also Ralink chipsets, but some require you to download firmware files to make it work, which is disappointing.

---

### Post by UltimateCat on 2012-08-03
Me too-
Blacklisted the rtl8169 and used the rtl8168
Used the .inf and accompanied it with NDIS Wrapper- Works great for my wusb54gc adapter:popcorn:

---

