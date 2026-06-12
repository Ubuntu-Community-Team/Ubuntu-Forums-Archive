---
title: "Alcatel one touch x220s modem on ubuntu 11.10 linux"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by Sam Musasizi on 2012-03-12
1. After plugging in your usb modem, In terminal enter the command below as one string:


sudo usb_modeswitch -v 0x1bbb -p 0xf052 -P 0x0052 -s 10 -M 55534243123456788000000080000606f50402527000000000000000000000; sudo modprobe usbserial vendor=0x1bbb product=0x0052

I have to enter the above command each time you plug in the modem.

Alternatively;
2. Create a udev rule.
Save the following in a file for example called “10-alcatel.rules” in  “etc/udev/rules.d”


# Alcatel X220S Alcatel HSPA Data Card
ATTRS{idProduct}=="f052", ATTRS{idVendor}=="1bbb", RUN+="/usr/sbin/usb_modeswitch -v 0x1bbb -p 0xf052 -P 0x0052 -M 55534243123456788000000080000606f50402527000000000000000000000", RUN+="/sbin/modprobe usbserial vendor=0x1bbb product=0x0052"
The above instructions will work if your alcatel modem has vendor number "1bbb" and product id "f052" (in terminal check with either "lsusb" or "usb-devices")

After creating the udev rule if I start the computer with the modem plugged in. the driver is not attached right away. I have to plug it out then in for it to work. Any help on getting it to work if I start the computer with the modem plugged in?

---

