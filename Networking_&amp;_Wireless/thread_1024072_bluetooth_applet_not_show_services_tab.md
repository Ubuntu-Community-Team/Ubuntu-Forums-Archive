---
title: "bluetooth applet not show services tab"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by shtripok on 2008-12-28
I read page about bluez setup ([https://wiki.ubuntu.com/BluezGnome](https://wiki.ubuntu.com/BluezGnome)), and see there "click "Preferences", than click the tab "Services", Find the service you want (such as "Input Service" for a mouse), click on it and click "Add""

As you can see on screenshot ([http://imagebin.ca/view/IBeNR6e8.html](http://imagebin.ca/view/IBeNR6e8.html)), no "services" tabs here.

I can only pair devices, all other I have to do with command line and configs, like there ([https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)).

How can I obtain GUI for bluetooth modem and gprs connection configuration?

Interpid 8.10, eeePC 901

---

### Post by michelefrost on 2009-01-27
Same here with Intrepid + eee-modified kernel on my eee-pc 4g.
Possibily something missing - let me check and if I solve I will let u know.

---

### Post by michelefrost on 2009-01-27
Seems like it's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/258738](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/258738)

a fix should be in the upgrades. Let's try ;)

---

### Post by shtripok on 2009-01-27
The last note in that bug is 2008-10-08, and there sayed "This should be resolved in the BlueZ Gnome 1.8 package that entered intrepid yesterday." - long time ago.

And first screenshot in this bug missed another tab.
So, I think I have another bug.

---

