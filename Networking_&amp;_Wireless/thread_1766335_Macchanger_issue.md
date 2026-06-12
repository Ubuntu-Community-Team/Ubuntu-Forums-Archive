---
title: "Macchanger issue"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by tygsxr on 2011-05-24
Hi, my problem is i have a Dlink Dwa-645 (AR-5416 chipset) pcmcia card in laptop when i try to spoof mac address with Macchanger it changes the mac address in the terminal but when i re- enable network manager to connect to network it automatically changes back to my default mac address. I have also tried editing the interfaces file aswell but same thing.. Any suggestions would be great cheers..

**Solved**

---

### Post by Jean-Sebastien Gosselin on 2011-06-04
Hi tygsxr,

I have the same issue but do not have the skills to find a solution by myself.

Could you explain me how you solved this please?

Thanks a lot.

JS

---

### Post by tygsxr on 2011-06-09
Hey [Jean-Sebastien]("http://ubuntuforums.org/member.php?u=1313233")
The issue is still not totally solved, i have been disabling network manager-wireless option, then i am going to terminal and entering sudo ifconfig wlan0 down, sudo macchanger --mac=01:23:45:67:89:AB wlan0(copy new mac address), then ifconfig wlan0 up. Then i have been going to edit connections in network manager picking you connection and under wireless tab i am putting in your new address in the cloned address option. Then enable network wireless option.. It has been holding the address for a short amount of time but not as long as i like. I am using a DWA-645(Atheros AR5008 chipset). What is the card you are using..If you have found a better solution i would be interested to know. Cheers

---

### Post by jsgosselin on 2011-06-14
Hello tygsxr (this is my old account I managed to retrieved back),

There is currently a bug in the wpa_suplicant client that prevent MAC cloning with NetworkManager. Maybe you can try the workaround proposed by Mathieu Trudel-Lapierre in [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/787192](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/787192).

For me it has not worked. I suspect I have another issue on top of the wpa_supplicant one that is related to the proprietary driver I use for my *Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller* in a *Dell Inspiron* Laptop.

Hope it works for you. Bye

---

