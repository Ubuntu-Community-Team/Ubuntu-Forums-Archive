---
title: "linksys wireless pcmcia wpc card recognition"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Got a question on 2009-05-10
Hi

Does anyone know why ubuntu 8 doesn't recognise my linksys wireless pcmcia wpc card?
Ubuntu 7 did recognise it but froze when the WEP key was typed in (did work with unsecured wifi) After updating to 8 the wifi option is shown disabled. LAN works. Wifi works under windows.

Absolute beginner - Any help welcome.

Thanks

---

### Post by Triptol on 2009-05-10
To start, we need to know what card it is (name and number). Then some output created by dmesg would be helpful.

Mabe the following will produce something:
```
dmesg | grep wlan
```
If so, post it here.

---

### Post by Got a question on 2009-05-10
Hi

Done that.
This is what it comes up with:
 dmesg | grep wlan
[   43.208601] wlan0: ethernet device 00:0c:41:bf:16:df using NDIS driver: lsrtnds, version: 0x100, NDIS version: 0x500, vendor: 'Realtek RTL8180 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8180.5.conf
[   43.208661] wlan0: encryption modes supported: WEP
[  255.457547] ADDRCONF(NETDEV_UP): wlan0: link is not ready

It's a wpc11 802.11B pcmcia card.
Realtek network card seems to be recognised correctly. .

I remember that the 8.10 update struggled with the recognition at some stage but then continued.


???

Cheers

---

### Post by Triptol on 2009-05-11
I have found this thread ([http://ubuntuforums.org/showthread.php?p=7138562](http://ubuntuforums.org/showthread.php?p=7138562)) with someone with a similar problem. Seems that the RTL8180 is not the most stable driver in this Ubuntu release.

Trick could be to blacklist the RTL8180 driver and the correctly install the Ndiswrapper driver for it. Since you are already using ndiswrapper (according to your output) you probably first need to deinstall the current one and do a reinstall of the driver.

Here is an Ndiswrapper manual (rtl8180 ndiswrapper). The manual starts with building its own ndiswrapper from cvs. You can skip that part and continue from where it says: 
```
ndiswrapper -i NET8180.INF
```

---

