---
title: "network manager not running"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by Demodog on 2009-06-22
I have a laptop with a usb mobile broadband connected. iCON 7.2 modem. It works good in XP.

I was happy to see that in 9.04, after upgrading it, I did not have to use a modeswitcher for my mobile broadband modem anymore.

But I have a problem with gnome network manager. After using the connection a little while it just shuts down the modem and then it says "network manager not running" when I hold the pointer above it. I cant restart, kill it or anything. I have to restart the computer. I can just surf for like 3-4 minutes.

Anyone had this issue? Don´t know if it´s related to linux, network-manager, my modem, or perhaps firefox? Any help would be great :D

---

### Post by Demodog on 2009-06-22
/var/log/messages :

Jun 22 21:08:45 ubuntu kernel: [  701.452199] usb 5-2: reset full speed USB device using uhci_hcd and address 8
Jun 22 21:08:45 ubuntu kernel: [  701.600910] hso 5-2:1.0: no reset_resume for driver hso?
Jun 22 21:08:45 ubuntu kernel: [  701.600914] hso 5-2:1.1: no reset_resume for driver hso?
Jun 22 21:08:50 ubuntu kernel: [  706.000152] net hso0: Tx timed out.
Jun 22 21:09:00 ubuntu kernel: [  716.000146] net hso0: Tx timed out.
Jun 22 21:09:10 ubuntu kernel: [  726.000158] net hso0: Tx timed out.
Jun 22 21:09:20 ubuntu kernel: [  736.000145] net hso0: Tx timed out.

---

### Post by GeorgeVita on 2009-06-22
Hi **Demodog**,
please check the output of terminal command: **lsusb**

I had the same problem with my ZTE MF636 (0x19d2 : 0x0031) and found that booting with the modem attached was more stable. Also I made a change to a HAL definition.

Regards,
George

---

### Post by Demodog on 2009-06-23
What changes did you do to HAL and how?

I have tried it connected when I startup but not much difference. Anyone knows why it resets the usb device?

---

### Post by GeorgeVita on 2009-06-23
Hi,
from 9.04 the system "attaches" a modem using udev (primary option) or HAL (as an alternative).

In my case (ZTE MF636 modem which was NOT listed into 10-modem.fdi fie):
[B]sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
[/B]found **19d2** (vendorID) and changed the productID from 0015 to 0031 (MF636). At next boot it recognizes the modem twice giving me the total of 4 same providers to dial! The explanation is that using HAL 4 ttyUSBx created and the system supposed it can use them. Only 2 of them are usable (other 2 freeze the system). In this "weird" condition I can use it.

For your case, what is the output of **lsusb** (vendorID, productID)? Does the system creates /dev/ttyUSBx?

Regards,
George

---

