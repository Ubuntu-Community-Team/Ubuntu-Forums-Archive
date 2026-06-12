---
title: "Bluetooth keyboard fails to survive a reboot"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by mokachoka on 2011-08-18
I have successfully managed to connect a Razer Orochi bluetooth mouse with no issues. This also connects automatically when i start up the machine.

I also have a Logitech MX5000 keyboard that i can connect but it never survives the reboot. I have to manually connect it each time.

The only difference i can see between the two is the keyboard asks for a passkey whereas the mouse doesnt.

Does anyone know a fix?

Ubuntu 11.04 32bit.

---

### Post by mokachoka on 2011-08-18
Sometimes its quite difficult to actually get the keyboard to connect manually, i have to attempt the connect 2-3 times.... Anyone?

---

### Post by colorprint on 2013-03-23
try to disable SSP
add this to /etc/rc.local:

hciconfig hci0 sspmode 0

---

