---
title: "Using USB Wireless Dongle with mini-pci Intel 3945 installed"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by LarryJ2 on 2009-08-02
I have a Dell Inspiron E1505 laptop with a mini-pci card containing a Intel 3945 wireless chip.  This works fine most of the time except when I want to connect to a weak RV Park access point.  Then I want to use a USB Wireless "dongle" that I can move around until the signal strength is sufficient to allow a reliable connection.   Unfortunately,  I couldn't find a way to run the Intel card and a wireless USB dongle at the same time. I ended up blacklisting the Intel 3945 card then rebooting.   If you have the same problem,  this may be helpful.

All this assumes Ubuntu 2.6.24-24-generic  Hardy 8.04 LTS with the Gnome Desktop, and that the wonderful "wicked"  Wicd Network Manager is installed. [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)  to download a .deb installable copy. (I personally highly recommend this utility and publicly thank its author.)

1. In a terminal on the command line, enter:```
sudo gedit /etc/modprobe.d/blacklist
```

2.  Add these three lines (The third line is blank)
```
# Note: comment out the following line with a # if you want the mini-pci intel 3945 wireless card to be loaded.
blacklist iwl3945


```

3. Save the file then  System -> Quit  > Restart

4. During BIOS boot,  plug in your wireless usb dongle.
(Or simply power down, plug in your dongle, and power up again)

5. Open a terminal and enter this on the command line:
```
lj@dell:~$ iwconfig
```

You should see wlan0 or wlan1 or wlan2 or similar.

6. Then open WICD network manager. (Applications->Internet->Wicd Network Manager)  In Wicd, Preferences, General Settings in the Wireless Interface
box,  enter your wireless interface you found from step 5 above (wlan0 or similar) in the box titled wireless interface.

7.  Then in the Wicd main window,  click the Refresh button.  Look for your  wireless access point.  Hopefully that will be one of the available choices so next  you can add your encryption data  and click connect.

8. To resume using the internal Intel 3945 card,  comment out the black list (Step 2 above) and reboot.  

This seems rather painful.  Maybe someone else has a better method of switching between internal Intel 3945 and external USB Wireless dongles.

I tried this technique with three USB Dongles. I'll probably end up using the SMC unit as it seemed to have the best performance.  Here's info on the three FYI.

> USB Wireless Dongle #1
SMC EZ connect g    USB Dongle
Model: SMCWUSB-G   Serial Number: T291604191
MacAddress/ HWaddr 00:22:2d:0e:46:7b
Altheros AR2524-AQ1C chip
FCC ID: RAXWN4501H
lsusb: Bus 005 Device 008: ID 083a:4505 Accton Technology Corp.
Modules zd1211rw, lbm_cw_mac80211, lbm_cw_cfg80211 
Irritations: Hard lockup when dongle is unplugged from USB port forcing power down and restart. Signal strength displayed in dBM under wicd is not correct but  Signal Quality with iwconfig seems appropriate.

USB Wireless Dongle #2
Encore Electronics  Wireless 802.11g USB Adapter
Encore  ENUWI-G2  FCC ID NOI-W420B
MacAddress /HWaddr HWaddr 00:08:54:95:2f:6a
RealTek RTL8187B chip
Serial Number 11729040724359
lsusb: Bus 005 Device 003: ID 0bda:8189 Realtek Semiconductor Corp.
Modules: r8187, ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl 
Irritations:  Senstivity, slow to connect,  LED doesn't flash on data transfer.

USB Wireless Dongle #3
D-Link DWL-G122
Model:  DWL-G122  H/W Version B1  F/w Ver 2.02
P/N BWLG122NA.B1  FCC ID:  KADWLG122B1
Serial Number  DR5Z2610111437
MacAddress /HWAddr 00:15:e9:33:95:5d 
lsusb: Bus 005 Device 005: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Modules:  rt2500usb, rt2x00lib, rt2500usb,rt2x00usb rfkill, lbm_cw_mac80211, lbm_cw_cfg80211
Irritations: Doesn't connect under WPA, No Activity LED nor Link LED,
unplugging from usb port causes hard lockup forcing power down restart.

---

### Post by LarryJ2 on 2009-08-03
When attempting to align your USB Wireless dongle for maximum signal strength,  give   "wavemon" a try.  It's a "curses/text" based utility that continuously reports signal strength, link quality, and signal to noise ratio for the access point you are connected to.
```
sudo apt-get install wavemon
```

---

