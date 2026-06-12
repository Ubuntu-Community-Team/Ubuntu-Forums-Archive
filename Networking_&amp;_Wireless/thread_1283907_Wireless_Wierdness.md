---
title: "Wireless Wierdness"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by xandr55 on 2009-10-06
Hello All, 
So my computer has been acting strangely lately in regards to wireless. 

This is my set-up if you need more information let me know.
I am running current Jaunty on a Toshiba Satellite M50. 
My wireless card is: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) (from lspci)
I use wicd and the madwifi driver. 

Here is a synopsis of the behaviours and what seems to fix them. 

When I change places, and try to connect to a different wireless network, it seems to kind of kill the driver, because although initially it will show me what networks are available or even say that I am connected, it won't be connected and after an attempt and a couple of refreshes of which networks are available the whole thing stops and it says no networks available. 

If I go to System -> Administration -> Hardware Drivers and deactivate the madwifi driver, then restart the system, then reactivate the driver and restart again, the problem seems to be fixed. However sometimes it takes about 5 reboots to get it to work. 

If anyone has any idea what is causing this please let me know as it is very frustrating. Even just a way to deactivate the madwifi driver and reactivate it without rebooting would cause a significant improvement in productivity for me. 
Thank you for your time,
Xander

---

### Post by kreggz on 2009-10-06
I would say as an alternative you could use the NDISWRAPPER. This sounds the same as my media centre PC which has a netgear card atheros based. Activating the NDISWRAPPER fixed the problem and boosted the signal.

---

### Post by drpjkurian on 2009-11-01
> **xandr55 said:**
> Hello All, 
So my computer has been acting strangely lately in regards to wireless. 

This is my set-up if you need more information let me know.
I am running current Jaunty on a Toshiba Satellite M50. 
My wireless card is: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) (from lspci)
I use wicd and the madwifi driver. 

Here is a synopsis of the behaviours and what seems to fix them. 

When I change places, and try to connect to a different wireless network, it seems to kind of kill the driver, because although initially it will show me what networks are available or even say that I am connected, it won't be connected and after an attempt and a couple of refreshes of which networks are available the whole thing stops and it says no networks available. 

If I go to System -> Administration -> Hardware Drivers and deactivate the madwifi driver, then restart the system, then reactivate the driver and restart again, the problem seems to be fixed. However sometimes it takes about 5 reboots to get it to work. 

If anyone has any idea what is causing this please let me know as it is very frustrating. Even just a way to deactivate the madwifi driver and reactivate it without rebooting would cause a significant improvement in productivity for me. 
Thank you for your time,
Xander

Hi

Please visit my thread 
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)
It might help you.

Best of luck
Dr kurian

---

