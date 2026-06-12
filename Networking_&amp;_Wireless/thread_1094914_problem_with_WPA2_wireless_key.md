---
title: "problem with WPA2 wireless key"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by hot dog on 2009-03-13
I cannot for the life of me get my Ubuntu desktop computer to connect to my AT&T 2Wire gateway, using **WPA2** encryption. 

If WPA2 is set as the encryption mode on the gateway, and I use the same mode for logging on with Ubuntu, it doesn't connect.
When I set **WEP** on the gateway, and log on with Ubuntu, it works fine.

My wireless card is 802.11g, so I know IT supports WPA2.

any ideas what might be wrong??

thanks

---

### Post by komputes on 2009-03-14
Can you run this command in a terminal and upload lspci.txt and/or lsusb.txt files:

If your wireless ethernet controller is a PCI card (or integrated):
$ lspci -vvnn > lspci.txt

If your wireless "card" is a usb stick:
$ lsusb > lsusb.txt

Also, can other computers connect properly using a Live CD?

---

