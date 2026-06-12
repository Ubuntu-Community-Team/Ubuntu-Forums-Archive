---
title: "After upgrade to 10 from 9.x Wireless fails"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by ESimard on 2010-11-22
Hi, I upgraded from 9.x to 10.10. Under 9.x my wireless usb dongle worked correctly. After upgrade it does not. I checked the dongle on another machine and it works correctly. I inserted a usb memory stick and the system found it as a drive correctly. I assume from this that both the dongle and usb port are ok. The wireless device is a D-Link G122 A2 which is on the supported list (it ran out of the box on 9.x). The link light did not even come on.  So I installed ndiswrapper and the windows D-Link driver (note that this was not needed in 9.x).  Now the link light comes on and the wireless router is found but the unit will still not connect.  The log file entries on dongle insertion are as follows:

 ernie-desktop kernel: [ 1368.838094] usb 1-2: USB disconnect, address 5
Nov 22 19:46:42 ernie-desktop kernel: [ 1369.268122] ndiswrapper: device wlan0 removed
Nov 22 19:46:47 ernie-desktop kernel: [ 1374.828027] usb 1-2: new high speed USB device using ehci_hcd and address 6
Nov 22 19:46:47 ernie-desktop kernel: [ 1375.084031] usb 1-2: reset high speed USB device using ehci_hcd and address 6
Nov 22 19:46:48 ernie-desktop kernel: [ 1375.220685] ndiswrapper: driver prisma02 (D-Link,08/05/2004, 3.00.22.0) loaded
Nov 22 19:46:49 ernie-desktop kernel: [ 1376.221374] wlan0: ethernet device 00:11:95:db:ed:3a using NDIS driver: prisma02, version: 0x30016, NDIS version: 0x500, vendor: 'D-Link AirPlus G DWL-G122 Wireless USB Adapter(rev.A2)', 2001:3704.F.conf
Nov 22 19:46:49 ernie-desktop kernel: [ 1376.221448] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Nov 22 19:46:49 ernie-desktop kernel: [ 1376.235329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 22 19:47:12 ernie-desktop kernel: [ 1399.714624] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
Nov 22 19:47:13 ernie-desktop kernel: [ 1401.040934] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 22 19:47:23 ernie-desktop kernel: [ 1411.042646] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)


It appears that the problem is with wlan0 not being ready.  If this is the case how do I make it ready?

Thanks inadvance
_Ernie

---

### Post by uncaspi on 2010-11-22
There are many things you could try. Many have problems with 10.10 and wireless. Your driver is loaded,, but did you blacklist the native driver preventing it from being loaded too?

Do you see any networks with this command?

sudo iwlist scan

---

### Post by rkham11 on 2010-11-22
I've had very similar problems before.

Sometimes after an upgrade, I have to hardwire my internet connection and update my hardware drivers so that my wireless driver is updated

---

### Post by ESimard on 2010-11-23
Yes the scan shows the wireless router that I'm trying to connect to.

What is blacklisting I can try that.

_Ernie

---

