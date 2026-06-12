---
title: "ubuntu gnome wireless works; no luck with KDE"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by petedes5 on 2009-06-20
ubuntu works perfectly with wireless and network manager.

however, kubuntu (KDE) does not, I'm very very new with linux and have bought an amazon dummy book for it so I can learn but any help/insight/suggestions/comments/advise would be fantastic!


thanks very much

---

### Post by Ayuthia on 2009-06-20
Can you go into the Terminal and post the results of:
```
lspci -nn
lshw -C network
```It will help us identify your card.

Are you trying to scan wireless sites using the NetworkManager plasmoid/applet/widget?

For the most part, Ubuntu and Kubuntu are pretty much the same.  The NetworkManager frontend is different and sometimes can be the issue.

---

### Post by petedes5 on 2009-06-20
this is going to sound really sad but how do i get into the terminal to punch the code in/?

---

### Post by Ayuthia on 2009-06-20
It should be under Applications->System->Terminal/Konsole.  I can't remember which.

---

### Post by petedes5 on 2009-06-20
peter@peter-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
peter@peter-laptop:~$ lshw -C network

---

### Post by petedes5 on 2009-06-20
^does that look right?

---

### Post by Ayuthia on 2009-06-20
[quote]04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)[/code]That is your wireless card and in theory, is one of the cards that should work out of the box.  Can you see any wireless sites when you type:
```
sudo iwlist scan
```From the Konsole/Terminal?

Also, do you have something that looks like a plug in your system tray?  If so, that should be the NetworkManager applet.

---

### Post by petedes5 on 2009-06-20
when i do the isudo command, it asks for a password and i only have one password for ubuntu and i punch it in and it does not work.

and I do not have a plug thing in the tray to connect to theinternet

---

### Post by petedes5 on 2009-06-20
I'm pretty sure I have networkmanager installed, 

everything works fine on ubuntu but not kubuntu and I really like KDE and really want to use it : (

---

### Post by Ayuthia on 2009-06-20
Ok.  If you go to the panel and right-click it, it should bring up a list of options.  One of them should be Panel Settings.  Go to Panel Settings->Add Widgets.  That will bring up a list of items and one of them should be Network Manager.  Add that one and hopefully you will be able to then be able to connect.

Out of curiosity, what happens after you type in your password for sudo iwlist scan?  Does it produce No Scan Results?

---

### Post by petedes5 on 2009-06-20
the only thing that comes out of isudo was incorrect password and it gives me three attempts.


anyways, it **worked**!!! thank you sooooo much! you've been soo helpful

---

### Post by radixor on 2009-06-20
I too had this issue, NetworkManager manages the wirless networks which doesn't automatically start under KDE. The solution is to use a KDE/Gnome neutral wireless manager, like Wicd or to use wpa_supplicant from the command-line. 

```
 sudo apt-get install wicd 
``` 

should do the trick almost always and work for both KDE and Gnome.

---

### Post by khughitt on 2010-02-25
Same problem here. I'm running 9.10 with Gnome and KDE, attempting to connect to a WEP network using an Intel 3945ABG.

nm-applet works just fine in both Gnome and KDE. I have had no such luck with KNetworkManager however. I can see the network I want to connect to, specify that it is WEP and enter the key, but it fails to make a connection:

> 
dmesg | tail

[  125.452013] wlan0: no IPv6 routers present
[  728.632707] wlan0: disassociating by local choice (reason=3)
[  736.441276] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  736.640063] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  736.840047] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  737.040059] wlan0: authentication with AP 00:1f:90:e1:a8:67 timed out
[  743.262649] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  743.460050] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  743.661067] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  743.860053] wlan0: authentication with AP 00:1f:90:e1:a8:67 timed out
[  750.151843] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  750.348055] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  750.548050] wlan0: authenticate with AP 00:1f:90:e1:a8:67
[  750.748051] wlan0: authentication with AP 00:1f:90:e1:a8:67 timed out


Using iwconfig and dhclient from the command-line had similar results:

> 
sudo iwlist scan wlan0  // sees network...
sudo iwconfig wlan0 essid (mynetwork)
sudo iwconfig wlan0 key (10-character hex key)
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:de:11:d8:2a
Sending on   LPF/wlan0/00:18:de:11:d8:2a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Finally, I checked the status of network-manager, and it was started. Restarting it caused KNetworkManager to seg fault :\

Any suggestions? I can use nm-applet or a third party program like wicd just fine, but it's a shame that I couldn't use the tool provided by KDE.

Best,

---

