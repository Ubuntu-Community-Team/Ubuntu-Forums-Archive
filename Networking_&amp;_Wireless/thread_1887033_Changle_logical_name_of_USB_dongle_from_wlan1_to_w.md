---
title: "Changle logical name of USB dongle from wlan1 to wlan0?"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by dooper on 2011-11-26
Is this possible?

I did have an internal atheros card in my lappy which was wlan0.

I removed it as i couldnt get it working and now use a usb wireless dongle which is seen as wlan1 and works fine.

The only trouble is that on resume,the lappy still looks for wlan0 for a short time before defaulting to wlan1

I'd like it to automatically look for wlan 1 first (or only) so that it connects quicker..

Thanks

---

### Post by willemdev on 2011-11-28
You could always rename your wlan1 to wlan0..
modify the following file: 

/etc/udev/rules.d/70-persistent-net.rules
 
---------------------
# PCI device 0x8086:0x4229 (iwl4965)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:fc:ce:11:45:fe",
ATTRS{type}=="1", NAME="wlan[SIZE=4]**1**[/SIZE]"
----------------------

Change the "1" to a zero and delete the other pci device entry in that list. Hope it helps

---

### Post by Neill_R on 2011-11-28
Excellent information. I now know how to alter the assigned name for my Ethernet card. I came across the problem when on an old laptop (no CDROM) and unable to boot from a USB I was forced to extract the disk from the laptop and use a USB to IDE converter cable so as I could install UBUNTU on that disk. I of course got another eth device back in the original laptop. But now I know how to rename it back to eth0

---

### Post by dooper on 2011-12-03
The latest ubuntu downloads have now restored my internal atheros card to full working order and also fixed the incorrect battery charge problem..thanks

---

