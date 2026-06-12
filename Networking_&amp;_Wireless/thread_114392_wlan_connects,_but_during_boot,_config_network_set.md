---
title: "wlan connects, but during boot, config network settings takes forever and fails"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by zahidism on 2006-01-08
ok so configuring network settings takes forever in boot, and it [COLOR="Red"]fails[/COLOR]...but when ubuntu starts wlan0 is connected and im on the network without me doing anything...how do i fix this so it configures network settings properly?  any ideas?  should i just remove ndiswrapper recompile it and then reinstall the driver? (btw how do you remove/uninstall ndiswrapper??) thanks.

-z

---

### Post by Lambert on 2006-01-08
Do you have any other interface enabled? It's possible it activates the wireless interface and then tries to activate a second one which is taking forever.

Go into system>administration>networking and highlight the other network devices. Click properties, there's a box you can check to enable a device. clear all these except your wireless device and see if it helps.

---

### Post by zahidism on 2006-01-08
it worked! thanks!!

---

