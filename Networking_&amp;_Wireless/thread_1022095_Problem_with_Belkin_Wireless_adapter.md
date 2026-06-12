---
title: "Problem with Belkin Wireless adapter"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by tartagueule on 2008-12-26
Hi,
I am using a belkin wireless adapter requiring the RT73 driver.

I have tried almost everything, from the manual install, compiling the module, to the GUI instaler found on this very same forum.
The driver seems properly installed but for whatever reason, no wireless adapter is detected by the system.:confused:
Bloody annoying !!!!

Fed up, I have decided to try ndiswrapper. Again it seems to install the driver properly but it still does not work.
The interesting bit though, when I am runnig ndiswrapper -l the result is: RT73 installed but it does not tell me which USB device is using it.

That gave me the idea that there could be a prob with the USB ports. The box is pretty old (only use it at my holiday place)with USB 1 ports. Does anyone have a clue ?

Thank in advance.

---

### Post by AlexBellisBrown on 2008-12-26
With the Wifi in the USB, type lsusb in terminal. Post what it tells you here. Thanks :)

---

