---
title: "Different connectivity under different Kernels"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by tezer on 2010-04-19
Hi

I use a laptop with a built-in WiFi card (Intel PRO/Wireless 3945ABG [Golan] using iwl3945 module). It's OK but sometimes is not very stable, occasionaly it simply dies and I have to reboot. It was even worse but I improved it by applying a new driver.
I also have a very nice USB WiFi card (D-Link System DWA-140 802.11n Adapter [ralink rt2870]). It's much better and faster.

So the problem is that in Ubuntu 9.10 (2.6.31) I can use only the built-in one. The other one (D-Link) also works but I can't make it connect to my router. The built-in card connects to it but the D-Link even does not list it among possible connections (but it lists other possible connections which I do not want to use).
The funny bit is that this problem disappears when I use an old Kernel (2.6.28-18 ) : both cards work fine and can connect to the router at the same time (obtaining different ip's). I then disable the built-in one and happily use the external card.

Unfortunately the old Kernel has issues with sound and video, so I would like to use the latest Kernel with the external card. I tried WICD but it didn't change anything.
I can add that under the old Kernel the USB card is used as a ra0 device while the new Kernel lists it as wlan1.

Any ideas why it happens and how I can enable my external card to connect to my router?

---

### Post by tezer on 2010-04-19
I found the solution:
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9143407&postcount=2]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9143407&postcount=2")
Thanks to shahan for posting it.

---

