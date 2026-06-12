---
title: "Perplexed Linksys WPC54G"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by camogreen on 2011-05-20
In the past I've installed 9.10 using a hardwired network port for the web with the above card in the machine. After the install I got a notification of an update which downloaded the appropriate software for the above wireless card. Worked like a charm. Today I installed 11.04 and zilch. No wireless. Supposedly the firmware is missing. I guess my question is why is something that worked well in the past now missing?

Mike

---

### Post by chili555 on 2011-05-21
I don't think anyone knows why. I guess the reason is that computers do not work 100% perfectly 100% of the time, as much as we might wish it were so. I think your real question is what to do now. If you are running the slick but evolving Unity desktop, go to Applications and search for addition. Additional Drivers will be the only choice. Hook up that ethernet cable temporarily and get the firmware.

Using classic Ubuntu, look in System > Administration > Additional Drivers.

---

### Post by camogreen on 2011-05-21
My install defaulted to Gnome because the laptop is a bit older and seems to not have the proper video hardware for Unity. 

Thanks for the reply I'll give it a go.

---

### Post by camogreen on 2011-05-23
Found no drivers listed in "Additional Drivers". Perhaps if I had remembered the driver was "Broadcom B43legacy wireless driver" it might have helped. What I did was boot to XP, delete the Linux partition, then boot XP CD and ran fixmbr. Burned a new CD of 10.4.2. After the install "Hardware Drivers" listed the above for the wireless card. Activated, configured for WPA and all is working. It's up and running so I consider this partially solved although not perfect.

---

