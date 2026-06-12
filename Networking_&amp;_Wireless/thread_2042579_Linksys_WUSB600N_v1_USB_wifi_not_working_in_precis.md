---
title: "Linksys WUSB600N v1 USB wifi not working in precise?"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by mj0g on 2012-08-14
Has anyone been able to get a Linksys WUSB600N v1 USB wifi dongle (USB id 1737:0071) working with 12.04 precise on amd64?

The 3.2 kernel apparently supports it via the rt2x00usb module, but when that is loaded the following is printed to dmesg:

[    2.874226] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x000c detected.
[    2.874273] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[    2.874368] usbcore: registered new interface driver rt2800usb

and no wifi network interface is registered.

Neither installing the 3.3 or 3.4 compat-wireless modules or an actual 3.4 kernel fixes the problem. Apparently people have had luck in the past with RALink's module, but that appears to be for 2.6 kernels and so I don't know if it will work with 3.2.

Any suggestions?

---

### Post by mj0g on 2012-08-21
*bump*

No one using them any more?

---

### Post by Bucky Ball on 2012-08-21
Have you plugged in an ethernet cable, with the dongle in, gotten online with the cable and gotten all updates then checked Additional Drivers? That last line does appear to load the driver though but looks like the wrong one by the errors (wrong device for the driver). Do you know what wireless chip is in the dongle? With the dongle in, what does this report:

lsusb

? If you can find out what's in there you can download from site and install. I would give the one for 2.6 a try (because it's probably 2.6 and up) but I'm not convinced it's the 2800 you're after by the looks of those errors. ;)

---

### Post by mj0g on 2012-08-21
Don't have the machine handy at the moment for an exact lsusb, but the USB ID I quote above is from lsusb. It is one of these: [http://www.wikidevi.com/wiki/Linksys_WUSB600N_v1](http://www.wikidevi.com/wiki/Linksys_WUSB600N_v1), chipset is a Ralink RT2870.

Since the original post, I've managed to get Ralink's driver compiled against 3.2 after applying a few manual source patches. After removing+blacklisting rt2x00usb and inserting the compiled rt2870sta module, I at least get a wireless network interface  appearing in if/iwconfig for it, but it's not even giving a list of AP's after a scan, let alone associating with a wifi network. From memory, dmesg shows rt2870sta complaining about a eeprom mismatch error, and I can't set the ESSID.

Apparently rt2870sta used to be included in 2.6.x kernels in staging, but was dropped around 3.x, or at least Ubuntu stopped shipping it, which explains why it used to work but now no longer does.

I guess I should look at the restricted packages (that's what Additional Drivers looks in, right? This is a server install for a Segway robot) to see if the rt2870sta module is included there, but I'm overseas at the moment. Does anyone out there know if it is?

Ta!
//Mike

---

