---
title: "rtl8192SEvB wont run monitor mode"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by soad6 on 2011-03-08
Hi when I try to enable monitor mode thru " sudo airmon-ng wlan0" 
I get this as my output : Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
1029	avahi-daemon
1030	avahi-daemon
1179	NetworkManager
1218	wpa_supplicant
1947	dhclient
Process with PID 1947 (dhclient) is running on interface wlan0


Interface	Chipset		Driver

wlan0		Unknown 	rtl819xSE - [phy0]mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)

Then when I try to do sudo airodump-ng it doesn't work because it says no such device mon0 even though that previous command should've created the monitor mode.

---

### Post by soad6 on 2011-03-09
ok, so i got it to go into monitor mode, by doing this. Kill all process that are giving issues, dhclient, network-manager, wpa_supplicant, avahi-daemon. then sudo iwconfig wlan0 mode monitor
sudo airodump-ng wlan0
---------------------------
however after this is done it shows its in monitor mode, just it shows 0 pwr so not sure what thats about? or if I can fix this card to support injection. Any ideas would be helpful. thanx

---

