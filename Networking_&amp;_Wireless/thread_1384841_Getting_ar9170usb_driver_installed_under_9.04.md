---
title: "Getting ar9170usb driver installed under 9.04"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by Billsey on 2010-01-18
I have a Netgear WNA-1000 that I can't get recognized on any of my Ubuntu boxes (8.10, 9.04, 9.10). [This page]("http://linux-wless.passys.nl/query_part.php?brandname=Netgear") says that it should work with the ar9170usb driver, and that this driver is already part of the mainline Linux kernel as of 2.6.30. It also noted that ar9170usb does not claim this device's USB-ID at this time.

Now then,

How do I
(a) get this driver to recognize and work with my WNA-1000 under 9.10?

and/or

(b) get this driver installed and working under the older versions of Ubuntu that I also have?



Thank you for your time and help.

---

### Post by RSLU on 2010-01-20
I had the same problem with mine. I just installed ndiswrapper and used the driver for Win XP. See if it will work for you >.<

---

### Post by Billsey on 2010-01-22
It doesn't.

It recognizes the hardware is there, but when I go to "Configure Network" it just claims that it cannot find a network configuration tool. :(

So, I'm stuck, unless someone can tell me how do proceed from there without the help of "Windows Wireless Drivers" (in the System/Administration Menu once you install ndisgtk).

---

### Post by FixIt PeteC on 2010-02-15
Here's the fix that worked for me! 1. Download and install compat-wireless-2010-02-01, 2. go to the compat-wireless-2010-02-01/drivers/net/wireless/ath/ar9170 folder, 3. open the file "usb.c" at line 62 there will be a list of devices with their device IDs, 4.  Edit one of the existing devices to "Netgear WNA1000" and device ID "0x0846,  0x9040" you have to edit one of the existing devices since a usb driver can only control 18 devices, which are already listed.  

The ar9170usb driver is the closest match for the WNA1000, but it must recognize your device ID.  If for some reason your WNA1000 device ID is different, use you IDs.  I had to plug mine into a windows pc and look at its properties first.

Mine looks like: 

static struct usb_device_id ar9170_usb_ids[] = {
	/* Atheros 9170 */
	{ USB_DEVICE(0x0cf3, 0x9170) },
	/* [COLOR="blue"]Netgear WNA1000 */[/COLOR]
	{ USB_DEVICE([COLOR="Magenta"]0x0846, 0x9040[/COLOR]) },
	/* TP-Link TL-WN821N v2 */
	{ USB_DEVICE(0x0cf3, 0x1002) },

If everything else in the system is correct, just reboot and there it is!

Good luck!

---

