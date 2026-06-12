---
title: "Dell Wireless 1395 Wlan MiniCard"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by westboundroad on 2011-03-04
I have a Dell Precision M4300 with a Dell Wireless 1395 Wlan MiniCard. I have to no avail tried the procedure located at link [http://http://ubuntuforums.org/showthread.php?t=297092&highlight=Check+wireless+connection]("http://http//ubuntuforums.org/showthread.php?t=297092&highlight=Check+wireless+connection")

I am unable to get the dam thing working at all, If I do a iwlist scan it says it does not support scanning
 I installed the driver using windows wireless driver and it says no hardware present. Does anybody have any experience with this they would like to share????? Thanks

---

### Post by mikewhatever on 2011-03-04
Dell Wireless 1395 Wlan MiniCard is really Broadcom's BCM4312 802.11b/g. It has a native linux driver which works well. Remove ndiswrapper, hook up a cable, open System->Admin->Drivers and activate the STA wireless driver.
PS: The link you posted doesn't work. ;-)

---

### Post by prankstar008 on 2011-03-04
Try the official Broadcom Linux driver.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Follow the instructions in the readme (especially the part about removing existing modules)

---

### Post by westboundroad on 2011-03-04
I tried the procedure above, when I get to the step insmod wl.ko I get message no such file or directory. Also forgot to add I am a linux newb

---

