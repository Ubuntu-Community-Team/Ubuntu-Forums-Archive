---
title: "Connect Ubuntu 11.10 via USB alcatel X220S modem"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by u2japman on 2011-12-13
Hi.
I downloaded WUBI ,saved it on a flash disk and installed it off-line on a laptop running windows 7, a week ago- DUAL Boot.
I did NOT have an internet connection for the laptop. 
I bought a modem alcatel X220S.but i can NOT have it connecting, it however works well on windows.I got some post telling me to open SYSTEM/ADMIN/NETWORK and configure the modem,but i can not trace it on Ubuntu 11.10.I desperately need the ubuntu running.
Note: I do not have any other internet connection,I only hope to have the modem working,
BERNARD.

---

### Post by Sam Musasizi on 2012-03-14
1. After plugging in your usb modem, In terminal enter the command below as one string:


sudo usb_modeswitch -v 0x1bbb -p 0xf052 -P 0x0052 -s 10 -M 55534243123456788000000080000606f50402527000000000000000000000; sudo modprobe usbserial vendor=0x1bbb product=0x0052

You will have to enter the above command each time you plug in the modem.

Alternatively;
2. Create a udev rule.
Save the following in a file for example called “10-alcatel.rules” in  “etc/udev/rules.d”


# Alcatel X220S Alcatel HSPA Data Card
ATTRS{idProduct}=="f052", ATTRS{idVendor}=="1bbb", RUN+="/usr/sbin/usb_modeswitch -v 0x1bbb -p 0xf052 -P 0x0052 -M 55534243123456788000000080000606f50402527000000000000000000000", RUN+="/sbin/modprobe usbserial vendor=0x1bbb product=0x0052"

The above instructions will work if your alcatel modem has vendor number "1bbb" and product id "f052" (in terminal check with either "lsusb" or "usb-devices"

---

