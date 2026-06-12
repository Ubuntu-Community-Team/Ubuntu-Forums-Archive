---
title: "Linksys WUSB-300N 13b1:0029 - problems"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Zalokin on 2011-02-06
Hi,

I have the wireless device Linksys WUSB-300N - 13b1:0029.

I had problems for Ubuntu 10.10 64-bit to detect this.

I installed ndiswrapper and all its compontents.

I download WUSB.taz.gz and followed instructions on [http://ubuntuforums.org/archive/index.php/t-530772.html](http://ubuntuforums.org/archive/index.php/t-530772.html)

No problems there.

Infact, when i type sudo ndiswrapper -l it states: netmw245: driver installed and device (13B1:0029) present.

However the problem is that the WIFI does not work... and more specifically, when I LEFT CLICK the small wireless symbol on the top right of the screen (with an exclamation mark) it only states "Wired Network" (Disconnected). No sign of a "Wireless" option.
Also when I RIGHT CLICK on the said wireless symbol, no sign of "Wireless" either and no option for this. However, "Enable Networking" is ticked.

Also when I enter #sudo dmesg | grep ndis - nothing comes up.

I would be very grateful if someone could inform me of a solution.

Thanks.

Zalokin

---

