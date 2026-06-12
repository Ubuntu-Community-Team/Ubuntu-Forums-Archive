---
title: "wlan0 interface missing after suspend- how to rescan USB port"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by northhillca on 2009-06-11
I am using Realtek RTL 8192u based USB adapter with NDISWrapper and XP drivers on Jaunty-9.04. No native drivers yet. The adapter works like a charm except after resume from suspend, wlan0 interface is not available/ is missing from iwconfig/ifconfig and hence no wireless connectivity. lsusb does shows the adapter.

Is there a way to re-scan the usb port on resume similar to enable/disable usb device under device manager in windows. since removing and re-inserting the adapter fixes the problem. Ubuntu is my primary desktop at home for everyday use, I would like to find the solution to this. Thanks.

---

### Post by jstrawther on 2009-07-10
Same problem here.  I'm on 9.04 with all latest updates, with a Belkin F5D7050 usb wireless interface.  Works like a charm until suspend/resume. Then the only I've been able to get it to work again is to unplug/replug it.  Would love it if there were a way to probe usb devices or some such.

---

### Post by kerry_s on 2009-07-10
you got to suspend the drivers for the card.
what drivers are you using?

**gksudo gedit /etc/pm/config.d/config**

put:

**SUSPEND_MODULES="your-drivers"**

---

### Post by jstrawther on 2009-07-10
Eureka! 

For me, SUSPEND_MODULES="rt73usb" did the trick.  Thanks friend.

---

