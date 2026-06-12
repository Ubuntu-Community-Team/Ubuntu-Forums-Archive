---
title: "usb+wirelless networking....."
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by m.h.shams on 2006-02-15
dear freinds,

im new in ubuntu...

before ubuntu i had a windows xp pro. and i have a wireless network modem for connecting internt. my modem connect via usb port.

my modem application and drivers is just for windows, and i can't install it at ubuntu.

then i install a vmware on my ubuntu, and wanna install my modem on it,
but it seems at my usb port on windows don't work correct,

please help me to run usb device on vmware windos.

---

### Post by Paloseco on 2006-02-15
I never saw a wireless USB modem. Does that exist?

---

### Post by m.h.shams on 2006-02-15
[QUOTE=Paloseco]I never saw a wireless USB modem. Does that exist?[/QUOTE]

sorry about my poor english, ill try to explain better :

i have an acount for connect to a wierless network (internet)
to connect this network i most use an special external modem.
this modem connect via usb to my pc, 

i hope you got my point.
thanks again.

---

### Post by Paloseco on 2006-02-15
First of all, visit this page:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
You have to determine what kind of device is yours, brand, manufacturer, etc.
You can do "sudo tail -fv /var/log/messages" to see what is going on when you connect/disconnect usb stuff.

After you know the brand and manufacturer of the device you can browse here to see if is fully supported:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

Maybe the driver comes with ubuntu (or is in the repositories) or maybe you will have to download and compile the source code by hand, check that the module loads, etc.

After that you will have to go to "/etc/iftab" and see if the mac address of the usb device has been associated with an interface, if not you will have to do it. Having binded the interface with the real device is a generic WPA configuration.

---

